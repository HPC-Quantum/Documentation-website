# Quantum–HPC Workflow Scenarios

This section presents a set of **static workflow scenarios** that illustrate common execution patterns in hybrid Quantum–HPC systems.

Each scenario uses simplified, step-by-step diagrams to show how classical HPC resources and quantum resources (QPU) interact over time. It also shows where execution stalls arise, and how orchestration choices shape overall utilization.

The scenarios are directly motivated by — and map back to — some of the bottlenecks discussed in the accompanying article:  
[Hybrid Quantum–HPC Systems: Bottlenecks, Tradeoffs, and Practical Solutions](https://medium.com/@claudia.friedsam/hybrid-quantum-hpc-systems-bottlenecks-tradeoffs-and-practical-solutions-1faa3e21db23)

They are intended to provide **conceptual orientation**, not performance prediction.

---

## Scenario Overview

| Scenario | Short Name | Focus / What You Learn | Dominant Bottleneck (Article) | Example Use Cases |
|--------|------------|------------------------|-------------------------------|---------------------------|
| **A** | Idealized Baseline | What a *clean*, loosely coupled hybrid run looks like | None (reference case) | toy examples, demos, low-frequency QC calls, one-off runs |
| **B** | Synchronization Wall | How global barriers force HPC-wide waiting | Bottleneck 3 (synchronization + serial QC) | VQE, QAOA, variational optimization, collective updates |
| **C** | Latency / Data Wall | How data transfer & control overhead dominate fast jobs | Bottleneck 1 (latency / data movement) | Monte Carlo, genomics, multi-omics, PDE state exchange |
| **D** | Throttled Execution | Why rate-limiting is required even without synchronization | Bottleneck 3 (serial service capacity) | batched VQE, kernel evaluation, high-throughput hybrids |


---


The scenarios are ordered to progressively introduce tighter coupling and stronger constraints between classical and quantum execution. Together, they form a visual companion to the bottleneck analysis in the Medium article.

An interactive **Quantum–HPC Workflow Explorer** that allows users to experiment with orchestration parameters (queue limits, latency, submission rate) is under development and will be linked here when available.
