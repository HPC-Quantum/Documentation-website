# Introduction to Quantum-HPC 

Quantum computing is not a replacement for classical high-performance computing (HPC). Today’s most realistic quantum applications are **hybrid**: they combine a Quantum Processing Unit (QPU) with powerful classical compute resources for orchestration, optimization, and post-processing.

This page provides a lightweight overview of **why quantum and HPC belong together**, where the main system bottlenecks appear, and how real platforms mitigate them.

---

## Why Quantum and HPC Belong Together

QPU execution is typically:

- **specialized** (useful for specific subroutines)
- **serial** (limited throughput)
- **noise-limited** (short coherence times)
- **hardware-constrained** (connectivity and qubit count)

HPC systems provide mature, scalable infrastructure for the parts quantum devices do not handle well: large classical parallel workloads, fast data movement, compilation, and scheduling.

In practice, the QPU behaves like an accelerator, while the HPC system provides the surrounding workflow.

---

## Where HPC Is Used Today

In modern hybrid workflows, classical HPC resources are heavily used for:

- **Compilation and transpilation**  
  Mapping circuits to hardware is computationally expensive and parallelizable.

- **Batch execution and parameter sweeps**  
  Variational methods (e.g., VQE/QAOA) require running many circuit instances.

- **Circuit cutting / knitting**  
  Larger circuits are decomposed into subcircuits that fit on available devices, then recombined classically.

- **Post-processing and error mitigation**  
  Aggregation, mitigation, and uncertainty estimation are classical tasks well suited to HPC.

---

## Key Constraints

Hybrid quantum–HPC workflows face several system-level constraints:

- **Latency** between the classical host and remote QPUs can dominate time-to-solution.
- **Queue time variability** makes tightly coupled feedback loops inefficient.
- **Scheduling mismatch** can waste classical resources if large allocations sit idle while waiting on a QPU.

---

## How Platforms Address These Issues

Current platforms typically mitigate these constraints through:

- **Asynchronous or serverless execution** to decouple classical resources from QPU queue time
- **Batching and session-style execution** to amortize overhead
- **Multi-backend execution** when work can be split across devices
- **Careful orchestration** (sometimes via scheduler integration) to reduce idle time

These approaches optimize for practical *time-to-solution*, not theoretical runtime.

---

## Scope of This Project

This project focuses on **practical, reproducible hybrid workflows**, emphasizing:

- HPC concepts that matter for quantum integration (MPI, OpenMP, schedulers)
- Containerized environments for portability and reproducibility
- Clear separation of classical orchestration vs. quantum acceleration

---

## Further Reading

For a deeper discussion of bottlenecks, scheduling tradeoffs, and emerging system architectures in quantum–HPC integration, see the accompanying Medium article:

→ *Hybrid Quantum–HPC Systems: Bottlenecks, Tradeoffs, and Practical Solutions*

