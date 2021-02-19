---
title: "Widening the Sphere of Ethical Considerations for ML Operations"
date: 2021-02-19T12:31:39Z
Tags: [MLOps, fairness, automation, ML lifecycle]
Categories: [Automating Ethics]
DisableComments: true
---
***This is the second post in a series on the topic of automating ethical deliberation in data science and AI. For the first post, [click here](/blog/automating-ethics/automating-ethics).***

## Introduction

> *The Machine is stopping, I know it, I know the signs.' She burst into a peal of laughter. He heard her and was angry, and they spoke no more. 'Can you imagine anything more absurd?' she cried to a friend. 'A man who was my son believes that the Machine is stopping. It would be impious if it was not mad.*   
  -- E. M. Forster (1909) The Machine Stops

There are many benefits to automation.

As someone who routinely forgets to do things, having a smartphone that automatically prompts me to complete important tasks is invaluable. Of course, many of the tasks that I use technology to automate are mere conveniences. And it seems that technology developers, motivated by the usual financial desires that drive "innovation", are more than happy to fulfil our *insatiable appetite for convenience*. One only needs to look at the ever-growing panoply of smart home gadgets to recognise the inherent magnetism of convenience-based automation.

Some will see these developments as justification for raising concern that we're sleepwalking into a dystopian future where we become dependent on a ubiquitous sociotechnical system that we no longer understand, and which one day suddenly stops—as is the case in E. M. Forster's short story, from which the introductory quote at the start of this post was taken.

As a lover of science fiction, it would be easy for me to dedicate a blog post to throwing speculative shade on such technologies. However, while this post does in fact concern the topic of automation, the technologies it is concerned with are not those we see or interact with on a daily basis—assuming "we" are those fortunate to have the financial means to purchase technologies of convenience.

Instead, the technologies I consider here are those that run in the background, invisible to most, but increasingly important to the efficient running of our digital infrastructure. Therefore, I think it's important that we understand their limitations.

## Machine Learning Operations (MLOps)

In the [first post](/blog/automating-ethics/automating-ethics) in this series, I introduced MLOps—a practice of automating key stages of the ML lifecycle. In this post I want to dive deeper into the ethical implications of this practice. First, let's look at the practice itself.

Simply put, MLOps is the application of DevOps principles to the processes of machine learning—a compound of “machine learning” and “operations”.  Like DevOps, it follows an Agile methodology with the aim of making the development lifecycle of ML systems more efficient (i.e., shortening the time between development and deployment of an ML system). To achieve this, MLOps implements practices from DevOPs, such as continuous delivery (CD) and integration (CI), but also incorporates novel practices like continuous training (CT). Most importantly, these processes (where possible) are automated.

As [Google's own document on MLOps](https://cloud.google.com/solutions/machine-learning/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) states:

> Practicing MLOps means that you advocate for automation and monitoring at all steps of ML system construction, including integration, testing, releasing, deployment and infrastructure management.

Let's start by extracting a few salient points from the above quotation that will be returned to throughout this post:

- First, we have the emphasis on **automation** and **monitoring.**
- Second, we have the application of automation and monitoring to **all steps** of ML system construction.
- And, finally, we have the **processes** that are to be automated and monitored: integration, testing, releasing, deployment, and infrastructure management.

Presumably the processes identified within the quote is intended to be non-exhaustive. Nevertheless, they are only representative of development and operational practices—a point that is, perhaps, unsurprising given the grounding in *DevOps*. Or, using the terminology employed in my previous post: *development* and *deployment* practices.[^deployops]

[^deployops]: There are two reasons for choosing the term 'deployment' over alternatives, such as 'operations', 'implementation' or 'use'. The first is to help distinguish the ML model from the system that it is deployed within. Sometimes, this is referred to as model operationalisation, but to avoid confusion I refrain from using this term because I am often writing about the operationalisation of ethical principles. The second reason is simply that I like the alliteration of design, development, and deployment, which think makes the stages easier to remember.

Now, any systems or software engineer will recognise that there are many advantages that come from a clear focus and careful delineation of key stages in a system's lifecycle, including a greater degree of control, more robust and predictable pipelines, or flexibility from modularisation. This likely explains why the use of [containers](https://www.ibm.com/uk-en/cloud/learn/containerization) is an increasingly popular method in software and systems engineering, due to the wide range of benefits that stem from modularisation (or, containerisation), including portability (i.e., code can be written once and run anywhere), security management, fault isolation, easier collaboration, and so on.[^container]

[^container]: Containerization involves packaging up software code with any configuration files, dependencies, or libraries that are required to run the code, enabling it to run consistently on any infrastructure. The resulting package is referred to as a 'container'. Put simply, containerization allows applications to be “written once and run anywhere.” This portability is important in terms of the development process and vendor compatibility. It also offers other notable benefits, like fault isolation, ease of management and security, to name a few.

However, because MLOps has this narrow focus on the development and deployment of ML systems, there is a natural boundary placed on the types of ethical decisions that are considered as "falling within the scope of a ML developer".

I expect that this framing is partially responsible for the implicit assumption that certain ethical decisions are "not the responsibility of the ML developer", or the attitude that ethical principles are only valuable when they can be formalised and operationalised within the technical context of a ML project. However, there are many ethical choices that exist prior to the choice of how to tune one's hyperparameters, for example, and many of these choices do not lend themselves to an automated approach. To make this clear we need an alternative framing that helps to widen the sphere of ethical considerations.

## The ML Lifecycle

There are, invariably, many ways of carving up a process, and such choices often reflect the priorities of the individual or organisation involved.[^dennett] The way I carve up the ML lifecycle is no exception.

[^dennett]: I feel a need here to acknowledge an underlying influence of Daniel Dennett's Real Patterns on my way of thinking.

Therefore, to make my own priorities clear, Figure 1 is a representation of a *typical ML* project lifecycle, which serves as a useful heuristic for understanding the ethical governance and evaluation of ML and similar data-driven technologies. Moreover, it helps draw attention to the many stages that precede the type of development and deployment activities that are the focus of MLOps.

{{< figure src="/images/lifecycle.png" alt="A diagram of the ML Lifecycle, depicting an interlinked process of (project) design, (model) development, and (system) deployment." caption="Figure 1. The ML Lifecycle: an interlinked process of (project) design, (model) development, and (system) deployment." width="100%" >}}

It is important to recognise that in practice there are rarely strict boundaries between design, development, and deployment, nor between the lower-level tasks within each stage. Rather, the processes undertaken throughout a ML project will often shade into one another, overlap with subsequent stages, and sometimes repeat where a task requires an iterative approach. For instance, consider a project that needs to perform data matching between two separate datasets. Data matching requires identifying and matching the respective data schemas (or, ontologies), then matching the individual records, and, finally, integration into a single, cleaned dataset. This process may span the DATA EXTRACTION —> DATA ANALYSIS —> PREPROCESSING stages, requiring multiple iterations, as the project team consider various goals such as accuracy, representativeness, and bias mitigation. Therefore, the divisions between the three overarching stages in Figure 1 should not be misconstrued as suggesting the existence of practical boundaries.

Figure 1 also treats the lifecycle as a *diachronic* process (i.e., as one that evolves and develops over time), which explains why it is represented as a spiral. For instance, the completion of the deployment stage (e.g., the deprovisioning of a system) returns us to the design process, but at a later stage in time. Hopefully, as the spiral continues, the project team will have a greater awareness and sensitivity to the ethical implications of their system.

With these caveats in mind, let's return to the claim that the practice of ML Ops requires one to "advocate for automation and monitoring at **all steps** of ML system construction".

We must acknowledge that many of the tasks in the ML lifecycle (Figure 1) not only lend themselves to automation and monitoring but would likely benefit from it. This seems to be one motivation behind Google's recent project to automate the production of [Model Cards for *Model Reporting*](https://ai.googleblog.com/2020/07/introducing-model-card-toolkit-for.html)—a topic for another blog post! However, others clearly resist automation. For example, PROJECT PLANNING requires careful reflection, deliberation, and (in some cases) public justification for proceeding with a potentially controversial use of ML, such as automated facial recognition technology, or automated decision-making systems in criminal justice and healthcare.

Now, the "advocate" of MLOps could easily respond here with the claim that these activities do not fall within the scope of 'MLOps proper', and that the ML lifecycle as I portray it widens the sphere of ethical considerations at great expense to many of the operational requirements for the large-scale production of ML systems. Furthermore, they could also claim that it's fine to automate the sorts of development and deployment processes they do, because they are purposefully siloed away from the ethical decisions at the start and end of a project lifecycle. Unfortunately, these responses would fail to appreciate several things about the cascading effects of prior decisions.

This series of blog posts is, in brief, simply an investigation of these *cascading effects* through the ML lifecycle—which explains the purpose of having a representation of the ML lifecycle (Figure 1). Here, let's just look at two of the cascading effects.

## The Ethics of Responsibility and the Risk of Moral Deskilling

Our first response to the advocate of MLOps is that ethics is not a checklist task that you perform at the start or end of a project. It's a continual process of reflective deliberation, action, and justification that ought to be embedded in all stages of a project. Failure to do so risks leading to the sorts of hollow assurance and vacuous claims that many have come to expect from large technology companies, and which end up eroding public trust in the long-term.

When a choice is outsourced, and an automated ML pipeline replaces a key part of ethical decision-making, one is choosing to also offload the *moral responsibility* we all have for our actions—a result of our *human condition*[^arendt]. There are two practical consequences of this choice.

[^arendt]: Arendt, H. (1958/1998). The Human Condition (2nd Edition). University of Chicago Press.

The first has to do with the practical and technical constraints placed on a project as a result of prior decisions. This point should be easy enough to accept. For instance, if a choice is made early on in the PROJECT PLANNING stage to develop a highly accurate classification system that relies on a deep learning approach, this will constrain the choices that the project team can make regarding the interpretability and explainability of the final system. The ethical implications that can arise from this trade-off between ACCURACY ←→ INTERPRETABILITY are well-known: (e.g., inhibiting user understanding, autonomy, and informed consent). As a greater portion of the ML lifecycle becomes automated, a greater number of decisions with downstream effects are also likely to be automated. While this can lead to a greater consistency and the mitigation of (some) human cognitive biases, it can also create a complacency or myopia in the minds of those who ought to remain responsible for the effects of their decisions, resulting in an increased risk of so-called "*unintended* consequences", some of which may have been identified and averted had a human being carefully monitoring the project's evolution.

This leads us on to the second consequence, which addresses the impact of increased automation on the developers themselves.

Many experiments in moral and social psychology have exposed the vicissitudes of moral reasoning, such as the effect that increased physical or psychological distance has on our level of sympathy or compassion for some individual.[^greene] In fact, such psychological distance has long been exploited by behavioural economists and financial services (e.g., payment for goods with credit cards decreases feeling of loss aversion). The philosopher, Emmanuel Levinas also captured a related point when he described how *face-to-face* relations (*rapport de face à face*) "order and ordain" us into recognising the moral commitments we have to the Other[^sep].

[^greene]: Joshua Greene's book, [Moral Tribes: Emotion, Reason and the Gap Between Us and Them](https://www.penguinrandomhouse.com/books/299057/moral-tribes-by-joshua-greene/), is a great overview of a lot of this work.

[^sep]: https://plato.stanford.edu/entries/levinas/

The concern I am trying to capture here is that the more we are *distanced* from the process of ethical reflection, decision-making, and justification, due to increased automation that separates us from processes of decision-making, the greater the risk that we will neglect salient moral factors. Over time, this could result in the atrophying of our capacity for moral deliberation. Now, admittedly, this concern has been raised many times before in relation to the risks of automation, and may be perceived by some as having a flavour of the dystopian worries alluded to at the start of this post. While this is not a reason to dismiss the concern wholesale, it is unlikely to convince the skeptic. They may simply argue that the sorts of decisions that MLOps automates have little ethical significance. Therefore, let's turn to the second issue to bolster our defence.

## Algorithmic Fairness and Missing Data

There are two areas where the automation of ML development have, in recent years, closely overlapped with ethical principles: fairness and explainability. This is unsurprising in many ways. There exist a wide range of regulatory compliance and legal obligations, which create an acute incentive/disincentive structure that promotes the development of techniques that can, for example, produce automated explanations with sufficient fidelity, or automatically verify that an ML system does not discriminate on the basis of protected characteristics. We're going to restrict our focus to the topic of algorithmic fairness in this post.

Others have already argued[^wachter] that there are good reasons to be cautious about the promise of FairML or algorithmic fairness:

> "the EU’s current requirements [for bringing a claim under EU non-discrimination law] are too contextual, reliant on intuition, and open to judicial interpretation to be automated. Many of the concepts fundamental to bringing a claim, such as the composition of the disadvantaged and advantaged group, the severity and type of harm suffered, and requirements for the relevance and admissibility of evidence, require normative or political choices to be made by the judiciary on a case-by-case basis." (Wachter et al. 2020)

[^wachter]: Wachter, S., Mittelstadt, B., & Russell, C. (2020). Why Fairness Cannot Be Automated: Bridging the Gap Between EU Non-Discrimination Law and AI. SSRN Electronic Journal. https://doi.org/10.2139/ssrn.3547922

Again, lest the skeptic remains unconvinced by the existing arguments, we can go further. And let's do so by meeting the skeptic in their own territory.

If we restrict our evaluation of the fairness of an ML system to the domain of MLOps, we restrict ourselves to interventions within the development or deployment stages. In the case of a simple classifier, for instance, this means that we could employ a variety of techniques during pre-processing (e.g., adjusting the feature space to avoid correlations with a sensitive attribute), during training time (e.g., implementing a formal fairness optimization constraint), or during post-processing (e.g., correcting the outputs of the classifier to better meet the fairness definition). There are pros and cons to all of these options. However, they all suffer from the same limitation—their dependence on the available data.

Consider the following scenario. A team is developing an object classifier for an autonomous vehicle, and are weighing up the ethical implications of various settings for the classifier's decision threshold (i.e., the point at which the outcome of the classifier changes). For instance, they are exploring what effect different thresholds have on the vehicle's behaviour in possible collision scenarios, and to what extent the behaviour is discriminatory (e.g., it prioritises pedestrians over cyclists). They run a large number of simulations, based on data collected from a wide range of driving situations, to see what happens in the different scenarios. They have also made sure to consider, for example, the possibility of disparate performance that some of their sensors may have for pedestrians with darker skin[^surveillance]. After training, testing, and comparing the performance of a variety of models, they settle on the classifier that they believe has the best overall performance (according to some pre-determined metric). Now, let's also assume that the resulting model has a slight bias that compensates for the difficulty of detecting cyclists—that is, it has higher sensitivity to minimise the number of cyclists that it misses. In their testing, this results in some cases where the system overcompensates and collides with another vehicle or a pedestrian. However, the number of collisions with cyclists is reduced to almost zero. From a safety and fairness perspective the team consider this to be a positive outcome.

[^surveillance]: See the following report and explainer on bias in facial recognition technologies for more on this issue: [https://www.turing.ac.uk/research/publications/understanding-bias-facial-recognition-technologies](https://www.turing.ac.uk/research/publications/understanding-bias-facial-recognition-technologies)

Unfortunately, as alluded to earlier, there is an inherent limitation in our team's approach that cannot be compensated for by technical tweaks to the development of the system. This is known as the problem of *missing data*.

In our hypothetical (and admittedly simplified) scenario, the training data is primarily visual. As such, our team chooses not to infer the sex of the individuals, as they realise that the available methods for doing so would be highly unreliable—especially in the case of cyclists and motorists. Therefore, the team cannot evaluate the impact of their system on different sexes during model testing. However, by building in a bias that favours cyclists their system may inadvertently create a social bias. As it turns out, the team's data does not include demographic information which could show that more men cycle than women—this is an assumption, but perhaps an [accurate reflection of reality](https://www.cyclinguk.org/statistics), at least in England.[^criado] As such, even if their model and system is "fair" at one level, it may fail to retain legitimacy when we widen our ethical sphere of consideration to include broader conceptions of social justice, due to the fact that it inadvertently favours a certain sex due to the variations transportation usage in society. As such, the evidence that our team could offer about their model testing—perhaps produced automatically as a model card for model reporting—may end up appearing like a hollow assurance for those concerned with the wider social impact of autonomous vehicles.

Now, ultimately, this is just a hypothetical scenario used to illustrate a point, and it doesn't really matter for the purpose of illustration whether such a system would in fact discriminate against women (or some other demographic group) if it turned out that more pedestrians were women. However, in [her book](https://www.penguin.co.uk/books/111/1113605/invisible-women/9781784706289.html), *Invisible Women: Exposing Data Bias in a World Designed for Men*, Caroline Criado Perez has many other examples of how a failure to consider wider social patterns leads to outcomes that disproportionately affect women. It's an important book that all data scientists should read, as it provides a compelling case for the extent of implicit biases that exist within society. It is rare to be able to spot these biases by solely looking at the data, for the simple fact that a lot of the time the relevant data is simply missing—perhaps because it was never collected in the first place. And here we come to one of the main challenges for the advocate of MLOps: it is simply not possible to automate or monitor your system for ethical principles such as fairness, explainability, sustainability, and more, given the wide ranging considerations that factor into such decisions, and which go well beyond the information contained within a dataset.

## Conclusion

The main goal in this post was to set out some challenges, and (hopefully) convince the reader that MLOps, despite being a worthwhile practice, is unlikely to automate **all steps** in the lifecycle of a ML project if we wish to maintain awareness of the social, ethical, and legal impact of ML technologies. Perhaps no one really needed convincing of this point!

However, in future posts I hope to make these challenges more concrete by using actual, rather than hypothetical, cases, and diving deeper into specific issues. Furthermore, I also hope to offer practical and positive recommendations for how to respond to the challenges I discuss. As always, please feel free to get in touch with any comments or feedback.
