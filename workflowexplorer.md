# Quantum–HPC Workflow Explorer

The **Quantum–HPC Workflow Explorer** is the point where the concepts introduced in the previous sections become *actionable*.  
After working through the orchestration patterns and scenario animations, this tool is intended to help you reason about **your own hybrid applications** — not in terms of abstract theory, but in terms of *time*, *cost*, and *architectural choices*.

This is **not** a performance predictor or a simulator in the benchmarking sense. Instead, it is a structured way to develop intuition about how design decisions propagate through a hybrid HPC↔QPU workflow.

---

## Entry point

You can access the Workflow Explorer here:

**👉 https://quantum-hpc-workflow-explorer.vercel.app/**

<img src="./images/workflow-explorer/web/Startpage.png" alt="Workflow Explorer start page" style="max-width:100%; height:auto; margin: 1.5rem 0;" />

The explorer starts from a simple overview page that connects the conceptual material from the documentation to an interactive environment.

---

## Why this tool exists

In near-term hybrid computing, performance is often constrained less by algorithms themselves and more by **how classical and quantum resources are orchestrated**:

- when and how often quantum jobs are submitted  
- how classical ranks synchronize or block  
- how queueing, latency, and batching interact with classical scaling  
- where idle or blocked resources accumulate

For some workloads, these effects are negligible. For others, they dominate end-to-end runtime and cost.  
The Workflow Explorer exists to make these effects *visible* and *thinkable* — especially when mapping the patterns you’ve learned onto **your own project context**.

The goal is not exact prediction, but **informed intuition**:
> *If I structure my workflow this way, what kinds of bottlenecks am I likely to create?  
> Which resources will wait, which will scale, and where will time and money be spent?*

---

## Relationship to the scenario animations

The scenario animations presented earlier correspond directly to the **workflow patterns** used in this explorer.

Those animations:
- isolate specific orchestration behaviors (barriers, queues, latency walls, cascading idle time)  
- show how these behaviors emerge step by step  
- provide a shared vocabulary for discussing hybrid workflows

The Workflow Explorer builds on that foundation.  
Rather than introducing new mechanisms, it allows you to **reuse those same patterns** as building blocks when thinking about an application of your own.

---

## What you can do here

This section of the site is organized into three closely related parts:

### 1) Scenario animations
A curated set of visual workflows that illustrate common hybrid orchestration patterns discussed in detail earlier.  
These animations serve as reference points and mental models — not as prescriptions.

### 2) Builder
A lightweight interface for describing the *structure* of an application workflow.  
Here, you provide high-level information such as execution phases, synchronization points, and initial parameters, which then serve as input to the explorer.

### 3) Workflow Explorer tool
An interactive environment (currently under active development) intended to let you:
- explore how a given workflow structure behaves under queueing, latency, and synchronization  
- adjust parameters and observe qualitative changes in execution flow  
- reason about utilization, blocking, and architectural tradeoffs

The emphasis is on understanding *relationships* rather than producing exact numbers.

---

## What this tool is — and is not

**It is:**
- a thinking aid for hybrid system design  
- a way to connect architectural decisions to qualitative outcomes  
- a bridge between conceptual teaching and applied reasoning  

**It is not:**
- a detailed simulator  
- a benchmarking framework  
- a substitute for profiling or production measurements  

Any numbers or outcomes shown should be interpreted as *illustrative*, not predictive.

---

## Current status

The Workflow Explorer is an evolving prototype.  
At present, its primary value lies in connecting the scenario-based explanations to an interactive mental model. More detailed functionality will be introduced incrementally.

For now, the focus is intentionally on **clarity of structure and intuition**, not completeness.

---

If you’ve worked through the earlier sections, this page is not meant to teach you *something new* —  
it’s meant to give you a place to **apply what you already understand** to the problems you actually care about.