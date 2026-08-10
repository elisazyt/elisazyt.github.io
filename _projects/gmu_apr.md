---
layout: project-detail
see_more: true
title: Multi-agent system for automated program repair
workplace: George Mason University
date_range: 12/2023-01/2025, 06/2025-07/2026
categories: [research]
description: Designed, implemented, and tested a multi-agent LLM system which automatically patches Java bugs. Agents are provided with various prompts and tools to explore the codebase by parsing the program, performing static analysis, and retrieving relevant context via lexical and semantic search. Agent interactions are implemented using AutoGen. Presented first author poster at 2024 ACM CCS; 2025 Regeneron STS top 40 finalist; 2025 Davidson Fellows Scholarship honorable mention; code available on GitHub.
primary_tags: [python]
tags: [LLM agents, autogen, RAG, static analysis, docker]
---

**PI:** Dr. Kun Sun \
**Mentor:** Shiyu Sun

---

**Publications, honors, and code:**
- First author poster, ["Repairing Bugs with the Introduction of New Variables: A Multi-Agent Large Language Model"](https://dl.acm.org/doi/pdf/10.1145/3658644.3691412), accepted to and presented at the 2024 ACM Conference on Computer and Communications Security (CCS).
- Selected as a top 40 finalist in the [2025 Regeneron Science Talent Search (STS)](https://www.societyforscience.org/regeneron-sts/2025-finalists/) for this project: ["Patching Multi-Location Bugs: A Multi-Agent Large Language Model Framework for Automated Code Repair"](https://www.societyforscience.org/regeneron-sts/2025-student-finalists/elisa-zhang/)
- Received a [2025 Davidson Fellows Scholarship](https://www.davidsongifted.org/gifted-programs/fellows-scholarship/fellows/current-and-past-fellows/2025-fellows/) Honorable Mention
- Code is available on [GitHub](https://github.com/elisazyt/multiagent-program-repair)

---

**Project description:**

The following poster, created for Regeneron STS finals week, provides a detailed overview of the project as of March 2025. Since then, the following updates have been made:
- New context retrieval tools for agents, utilizing static analysis and vector retrieval
- More advanced multi-agent conversation patterns, agent routing, and message handling
- Fully automated pipeline, including test suite execution and containerized deployment

![Regeneron STS poster: Patching Multi-Location Bugs](/assets/sts_full_poster.jpg)

As of July 2026, the most up-to-date multi-agent system consists of the following: 1 admin agent, 4 patching agents, 1 context retrieval agent, 1 summary agent, 1 testing agent, and 1 patch selection agent
- Admin agent: orchestrates all agents by routing and logging messages from one agent to another
- Patching agents: generate patches in parallel, given different prompts and tools
- Context retrieval agent: performs context retrieval via tool calls and passes the retrieved context to the corresponding patching agent. The patching agent can request that the context retrieval agent perform the following on demand:
    - Extract syntactic information via AST traversal
    - Perform control flow analysis via code property graphs
    - Retrieve top-k relevant code/text snippets via BM25 search
    - Retrieve top-k relevant code snippets via semantic search using UniXcoder embeddings
- Summary agent: condenses the context retrieval agent's results before sending them to the patching agent
- Testing agent: runs the Defects4J test suites and returns the failing test information, if applicable
- Patch selection agent: selects the best patch out of all candidate patches to return

Please refer to the [GitHub repo](https://github.com/elisazyt/multiagent-program-repair) for full implementation and usage details.