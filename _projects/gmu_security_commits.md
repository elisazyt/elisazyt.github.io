---
layout: project-detail
see_more: true
title: Python security commit dataset
workplace: George Mason University
date_range: 06/2022-09/2022, 09/2023-10/2023
categories: [research]
description: |
    Constructed a dataset of ~1.2K security commits and ~2.8K non-security commits in Python, consisting of CVE records from MITRE and GitHub commits without a CVE ID. The latter is detected via keyword filtering and a graph-based method which utilizes a compact graph representation capturing the syntax and semantics of code changes. This graph is embedded and fed into a GCN with multi-head attention. Analyzed dataset and summarized common patch patterns. Co-authored and presented research paper at 2023 IEEE ICSME; dataset available on Hugging Face.
primary_tags: [python]
tags: [graph learning, topic modeling, program analysis, security patch]
---

**PI:** Dr. Kun Sun \
**Mentor:** Shiyu Sun

---

**Publication and dataset:** Co-authored and presented research paper, ["Exploring Security Commits In Python"](https://arxiv.org/abs/2307.11853), at the 2023 IEEE International Conference on Software Maintenance and Evolution (ICSME). The dataset is available by request [on Hugging Face](https://huggingface.co/datasets/sunlab/PySecDB).

---

**Project description:**
As more code is written in Python, more vulnerabilities are inevitably introduced. These vulnerabilities are fixed by security commits, but unfortunately, many of the commits aren't linked to a CVE ID and are poorly documented. This means there are many silent fixes in GitHub that developers don't know of. It is important to identify these security commits because they provide insight and can serve as training data for tasks like vulnerability detection and patching. As such, we construct a dataset of ~1.2K security commits and ~2.8K non-security commits in Python. This dataset consists of three subsets: a base dataset, a pilot dataset, and an augmented dataset.

The base dataset is constructed by going through CVE records and collecting all associated GitHub commits. Then, we algorithmically extract a list of security keywords/phrases based on their occurrences in both the security and non-security commits from the base dataset. The pilot dataset is constructed by searching for these keywords in commit messages—specifically, if the keyword frequency exceeds a human-defined threshold, we consider the associated commit to be a security commit candidate and manually verify it.

Finally, we propose a new graph representation of the commits and feed the embedding into a graph learning model to identify candidates for the augmented dataset. In this graph representation, nodes represent lines of code and edges capture syntactic and semantic dependencies. The representation is further simplified by performing bidirectional slicing so we only keep the nodes and edges that are directly relevant to the changed lines of code. We then embed nodes using CodeBERT and edges using 1-hot vectors, and feed these embeddings into a graph convolutional network with multi-head attention. Each convolutional layer aggregates information from neighboring nodes and edges, and we perform a final pooling and vector concatenation before sending the final embedding to an MLP to output the probability of the given commit being a security fix.

Our results show that the keyword filtering and graph-based detection method increase the efficiency of security commit detection and introduce more varied security commits spanning 119 distinct CWEs across 351 popular GitHub projects. We also summarize common repair patterns across the security commits: adding and updating sanity checks, updating API usage, updating regex, and restricting security properties. For more information, see Section V of our paper.