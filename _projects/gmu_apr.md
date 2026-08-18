---
layout: project-detail
permalink: /projects/program-repair/
see_more: true
title: Multi-agent system for automated program repair
workplace: George Mason University
date_range: 12/2023-01/2025, 06/2025-07/2026
categories: [research]
description: Designed, implemented, tested, and containerized a multi-agent LLM system that automatically patches Java bugs. Agents are provided with various prompts and tools to explore the codebase via AST parsing, CPG-based static analysis, and lexical and semantic search. Implemented agent interactions and routing, memory management, and message handling using AutoGen. Presented first author poster at 2024 ACM CCS; 2025 Regeneron STS top 40 finalist; 2025 Davidson Fellows Scholarship honorable mention; code available on GitHub.
primary_tags: [python]
tags: [LLM agents, autogen, RAG, static analysis, joern, openai api, docker]
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
- More advanced multi-agent conversation patterns, agent routing, memory management, and message handling
- Fully automated pipeline, including test suite execution and containerized deployment

<div class="poster-embed-wrapper">
  <a class="poster-embed-open-link" href="/assets/sts_full_poster.pdf" target="_blank" rel="noopener noreferrer" aria-label="Open poster PDF in new tab">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
  </a>
  <iframe src="/assets/sts_full_poster.pdf#toolbar=0&navpanes=0&zoom=page-width" class="poster-embed" title="Regeneron STS poster: Patching Multi-Location Bugs"></iframe>
</div>

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