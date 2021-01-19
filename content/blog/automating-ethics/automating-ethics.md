---
title: "Automating Ethics"
date: 2021-01-18T09:48:10Z
categories: [Automating Ethics]
tags: [MLOps, data science]
DisableComments: true
---
***This is the first post in a series on the topic of automating ethical deliberation in data science and AI.***

The philosophy and ethics of technology has a long tradition. In tracing this history, we could go all the way back to the Ancient Greek philosophers and the concept *technê*. Alternatively, we could explore Martin Heidegger's account of the relationship between technology and human existence (Dasein) as a starting point for modern phenomenological approaches to information and communication technologies. Or, we could begin with contemporary discussions and debates in science and technology studies that bridge the gap between philosophy, ethics, politics, law, sociology, and of course science.[^sep]

[^sep]: If you're unsure about where to start, the Stanford Encyclopedia has many fantastic summaries [[1](https://plato.stanford.edu/entries/ethics-it-phenomenology/), [2](https://plato.stanford.edu/entries/ethics-it-phenomenology/)], and the PhilPapers archive also has collections on both [Philosophy of Computing and Information](https://philpapers.org/browse/philosophy-of-computing-and-information/) and [Technology Ethics](https://philpapers.org/browse/technology-ethics).

Regardless of our starting point, having some knowledge of this rich multi-disciplinary history is useful for identifying where current debates in the ethics of technology echo (or "rhyme"[^history] with) previous debates. For instance, current research into FairML is grappling with and drawing upon longstanding debates in political philosophy[^binns], and Zuboff's idea of *surveillance capitalism*[^zuboff] while novel in its elucidation and critique of contemporary business practices, nevertheless echoes well-trodden discussions about the normative significance of concepts such as privacy and autonomy. In spite of these similarities, however, the development of novel data-driven technologies, such as ML or AI, invariably create novel ethical challenges or dilemmas.

[^history]: This is in reference to the phrase, ["History may not repeat itself. But it rhymes."](https://blogs.lse.ac.uk/internationaldevelopment/2020/04/16/history-may-not-repeat-itself-but-it-rhymes/)

[^binns]: Binns, R. (2018). What Can Political Philosophy Teach Us about Algorithmic Fairness? IEEE Security & Privacy, 16(3), 73–80. https://doi.org/10.1109/MSP.2018.2701147
[^zuboff]: Zuboff, S. (2019). The age of surveillance capitalism: The fight for the future at the new frontier of power. Profile Books.

This series will explore one such ethical challenge, which is the result of an emerging trend towards the *automation of governance processes* in data science and AI research and development. To be clear, technological automation itself is not new. There have been growing concerns about technological automation for centuries, including its impact on labour markets, environmental sustainability, or even the human condition itself. This kind of automation is not the focus of these posts. Instead, these posts will discuss a trend towards the automation of ethical decision-making that arises during a data science or AI project's workflow, and how this trend threatens to distance practitioners from challenging but vital forms of ethical reflection and deliberation.

There are myriad drivers of this trend towards **automating ethics**. However, an obvious and significant driver is economic incentives. Unsurprisingly, an organisation (whether in the public or private sector) is motivated by economic goals, such as increased profits through scalability, being first to market, reduced overhead costs, and so on. If an organisation relies upon a ML model for business intelligence, customer analytics, or as a key component in a product (e.g., an automated decision-making system), then they are likely to want to get this model into production as efficiently as possible. To address this need, the last couple of years have seen a growing interest in the area of **MLOps**.

MLOps stands for 'ML operations'. It is defined as,

> "the process of operationalizing data science by getting ML models into production—being able to monitor their performance and ensure they are fair and in compliance with applicable regulations." [^sweenor]

[^sweenor]: Sweenor, D., Hillion, S., Rope, D., Kannabiran, D., Hill, T., O’Connell, M., & Safari,  an O. M. C. (2020). ML Ops: Operationalizing Data Science. https://go.oreilly.com/queensland-university-of-technology/library/view/-/9781492074663/?ar

As a practice, it derives from the application of DevOps practices to data science and ML workflows (i.e., combining the development (Dev) of ML systems with their operation (Ops)). This, in itself, may not be that interesting a change from an ethical perspective. However, consider the following quotation from one of [Google's](https://cloud.google.com/solutions/machine-learning/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) articles on MLOps :

> "Practicing MLOps means that you **advocate for automation and monitoring at all steps of ML system construction**, including integration, testing, releasing, deployment and infrastructure management." (emphasis added)

Here, we are able to drill in on a possible source of concern. While the automation of "all steps" in the ML workflow may bring with it many benefits (primarily economic and operational) it also creates a variety of ethical challenges. First, there is the possibility of a loss of oversight at critical junctures that demand reflective dialogue and human judgement, potentially leading to unintended harms being missed or moral deskilling emerging in teams, especially when the monitoring is itself also automated. Second, to automate monitoring there needs to be a prior decision about which metrics need to be monitored. This invariably creates a situation where properties of a system that are resistant to simple quantification are passed over in favour of simpler metrics (e.g. KPIs). Third, there is a problem that if an ML model is affected by missing data bias because of structural barriers for inclusion that disproportionately impact certain sub-groups, then the above concern about automation is moot due to the upstream issue. Finally, there is the problem of deciding which metrics are suitable as goals to be optimised, encapsulated in [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law):

> "When a measure becomes a target, it ceases to be a good measure."

These challenges are just a selection, and also require further elaboration. The purpose of this series of blog posts will be to critically engage with them. However, identifying and evaluating these challenges first requires a way of mapping and delineating the key stages associated with the ML workflow. There are a variety of perspectives that we could take here. For example, the MLOps perspective adopted by Sweenor et al. (2020) gives rise to the following four steps, which they refer to as the Build, Manage, Deploy and Integrate, and Monitor process.[^sweenor]  

{{< figure src="/images/ml-ops.png" alt="Steps in the process of operationalising data science. Reprinted from (Sweenor et al. 2020)." caption="Figure 1. Steps in the process of operationalising data science. Reprinted from (Sweenor et al. 2020)." width="100%">}}

This schema serves a number of purposes, but it is not ideal for identifying and evaluating the ethical challenges that this series is interested in exploring. Instead, we will be building on a different framework, which breaks the ML workflow into a circular (and iterative) process of design, development, and deployment, with various sub-stages contained within this over-arching perspective:

{{< figure src="/images/ml-workflow.png" alt="A schematic of the ML workflow as a process of design, development, and deployment." caption="Figure 2. The ML workflow as a process of design, development, and deployment." width="100%" >}}

As this series continues we will say a lot more about how this perspective helps to identify significant ethical issues in the design, development, and deployment of ML, as well as how it can help us to design better tools for the governance of data science and AI more generally. In doing so we will also uncover a variety of concerns about the automating of ethical deliberation, as well as the following topics and questions:

- What is the proper function of ethical principles? How do we operationalise them in the context of data science and AI?
- When, if at all, is it permissible to use computational systems to automate key stages of ethical decision-making?
- What is MLOps, and how is it reshaping research and development practices?
- How can we design governance processes that provide sufficient support for ethical deliberation, while maintaining an appropriate pace of innovation?
- Who are the main actors that are responsible for the increased automation of ethical deliberation in data science and AI?
- What can moral psychology tell us about the risks of distancing individuals or teams from ethical deliberation?
- Why is it important to ensure that ethical deliberation does not become fully automated?

I hope this series will generate some interesting and thought-provoking discussion. It is closely related to an ongoing research project, as well as an article that is almost nearing completion. I will likely write a short piece on this once it's ready. As always, please feel free to get in touch if you have any thoughts!
