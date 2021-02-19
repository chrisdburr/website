---
title: "Situated ML"
date: 2021-01-25T11:52:26Z
Tags: [MLOps, bias]
Categories: [Automating Ethics]
DisableComments: true
draft: true
---

In the [first post](/blog/automating-ethics/automating-ethics) in this series, I introduced a schematic that was intended to represent a *typical* ML project workflow as a series of stages associated with one of more of the following categories: project design, model development, and system deployment. As we noted last time, this (admittedly) simplified schematic is intended to help identify significant ethical issues in the design, development, and deployment of ML.

This post will explore this schematic in further detail, laying the foundation for subsequent discussions.

## Exploring the ML Workflow 🔁

To begin with, here's the schematic again as a reminder:

{{< figure src="/images/ml-workflow.png" alt="A schematic of the ML workflow as a process of design, development, and deployment." caption="Figure 2. The ML workflow as a process of design, development, and deployment." width="100%" >}}

There are several features or components of the workflow that are worth emphasising:

  1. The structure of the workflow
  2. The over-arching categories
  3. The tasks
  4. The function of the schematic

Let's take each of these in turn.

### The Structure of the Workflow

Perhaps the most immediate property of the workflow's structure is that it is circular, rather than linear. This design choice was (partially) influenced by Jack Stilgoe's work in *responsible research and innovation*. For instance, Stilgoe claims:

> " Responsible innovation starts from an understanding of innovation as a system, a web of myriad actors, rather than a pipe."[^stilgoe2013]

By representing the workflow as a circular, interconnected (and at times overlapping) series of stages, the schematic re-emphasises Stilgoe's point that the practice of research and development relies upon a web of myriad actors. This is particularly true in the case of commercial data science or machine learning, where a single project may involve not just multiple teams within an organisation, but also multiple organisations serving distinct roles (e.g., market research -> data analytics -> procurement -> data scientists -> software engineers -> business managers).

However, in addition to the web of actors (directly) involved with the design, development, and deployment of the system itself, there is a wider web of stakeholders (e.g., society) that are indirectly involved.

<!-- Hence, the need for a situated perspective -->

[^stilgoe2013]: Stilgoe, J. (2013) *Foreword: Why Responsible Innovation?* (pp. xi-xv) In: Owen, R., Bessant, J. R., & Heintz, M. (Eds.) Responsible innovation. Wiley.

## Situated ML 🌍

### Situating MLOps
