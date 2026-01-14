# Introduction to High‑Performance Computing (HPC)

High‑Performance Computing (HPC) refers to using **many computational resources in parallel** to solve problems that are too large, slow, or complex for a single laptop or workstation. In practice, HPC allows researchers and engineers to scale simulations, data analysis, and hybrid quantum‑classical workflows beyond what is possible on a single machine.

In the context of **quantum computing**, HPC is not a competitor but an *enabler*: large‑scale simulations, circuit compilation, hybrid algorithms, and classical pre‑/post‑processing all rely heavily on HPC techniques.

---

## What Makes a System “HPC”?

At a high level, an HPC system is built from:

- **Compute nodes** – individual machines (often with many CPU cores and/or GPUs)
- **High‑speed interconnects** – fast networks connecting nodes
- **Parallel software** – programs designed to run on many cores or nodes at once
- **Shared infrastructure** – schedulers, filesystems, and software environments

A typical user does *not* log in and run programs interactively. Instead, work is submitted as **jobs** that the system schedules and executes.

<!-- PLACEHOLDER FIGURE 1: Laptop vs single node vs multi‑node HPC cluster -->

---

## Nodes, Cores, and Memory Models

Two distinctions are essential for understanding HPC:

### Nodes vs. Cores
- A **node** is one physical (or virtual) machine.
- A **core** is an individual processing unit within a CPU.

A single node may have tens or hundreds of cores, and an HPC job may span multiple nodes.

### Shared vs. Distributed Memory
- **Shared‑memory** systems: all threads see the same memory space (typical within one node).
- **Distributed‑memory** systems: each process has its own memory; communication happens explicitly (typical across nodes).

Most real HPC applications use one or both of these models.

---

## Core HPC Technologies You Will Encounter

### OpenMP (Shared‑Memory Parallelism)
OpenMP is a programming model for parallelism **within a single node**. It uses threads that share memory and is commonly used to speed up loops and numerical kernels on multi‑core CPUs.

Typical use cases:
- Parallelizing existing C/C++ or Fortran code
- Exploiting many cores on one node
- Incremental performance improvements with minimal code changes

### MPI (Distributed‑Memory Parallelism)
MPI (Message Passing Interface) enables programs to run **across multiple processes and nodes**. Each process has its own memory, and data is exchanged explicitly via messages.

Typical use cases:
- Scaling applications beyond one node
- Large simulations and distributed workflows
- Hybrid quantum‑classical algorithms that distribute workloads

### Slurm (Job Scheduling)
Most HPC systems use a scheduler to manage shared resources. **Slurm** is one of the most common.

Key ideas:
- You request resources (nodes, cores, time)
- You submit a job script
- Slurm decides *when* and *where* your job runs

Users interact with Slurm via commands like `sbatch`, `srun`, and `squeue`.

### Containers (Reproducible Environments)
Containers provide a way to package **software, dependencies, and runtime environments** together.

In HPC contexts, containers are used to:
- Ensure reproducibility across systems
- Simplify complex software stacks
- Bridge local development and cluster execution

While Docker is commonly used for building images, HPC systems often run containers using tools such as Apptainer/Singularity. In this project, containerization is also used to package and distribute demo applications for easier builds.

<!-- PLACEHOLDER FIGURE 2: Native build vs containerized workflow -->

---

## How This Fits into HPC‑Quantum Workflows

In practice, many quantum workflows rely on HPC techniques for:
- Classical simulation of quantum circuits
- Parallel parameter sweeps and benchmarking
- Hybrid algorithms combining quantum execution with large‑scale classical processing
- Efficient compilation and data handling

Understanding the HPC building blocks makes it easier to reason about performance, scalability, and system limitations when working with quantum software stacks.

---

## Hands‑On: OpenMP and MPI Mini‑Labs

To make these concepts concrete, this documentation includes **small, self‑contained mini‑labs** demonstrating:

- OpenMP for shared‑memory parallelism
- MPI for distributed‑memory parallelism

The labs are maintained in a single repository:

👉 **https://github.com/friedsam/hpc-qc-mini-labs**

Each lab focuses on:
- Minimal code examples
- Compilation and execution
- Observing how performance and behavior change with parallelism

You can explore these labs locally, on HPC systems, or inside containers, depending on your environment.

---

## Where to Go Next

- Explore the **OpenMP** and **MPI** pages in this documentation for quickstart guidance
- Run the mini‑labs to build intuition
- Continue to **Qiskit on HPC** to see how these concepts integrate with quantum workflows

This page is meant to orient you—not to exhaust the topic. HPC is best learned incrementally, through hands‑on experimentation and real workflows.