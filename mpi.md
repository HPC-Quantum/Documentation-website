# MPI Mini-Lab

MPI (Message Passing Interface) is the dominant programming model for **distributed-memory parallelism**. Unlike shared-memory approaches, MPI programs consist of multiple processes, each with its own memory space, that communicate explicitly by sending and receiving messages.

MPI is fundamental to large-scale HPC applications and is widely used in hybrid quantum–classical workflows that need to scale beyond a single node.

---

## What This Mini-Lab Demonstrates

This mini-lab introduces the core ideas behind MPI:

- Multiple processes executing the same program
- Process ranks and communicators
- Explicit communication between processes
- Scaling execution across multiple processes (and potentially nodes)

The examples are intentionally small and focused.

---

## Running the MPI Example

A minimal compile-and-run workflow looks like this:

```bash
mpicc hello_mpi.c -o hello_mpi
mpirun -np 4 ./hello_mpi
```

- `mpicc` compiles the MPI program
- `mpirun -np 4` launches four parallel processes
- Each process has its own memory and execution context

On HPC systems, MPI programs are often launched through the job scheduler.

---

## Full Lab and Exercises

The complete MPI mini-lab, including explanations, exercises, and scaling experiments, is maintained in the following repository:

👉 **https\://github.com/friedsam/hpc-qc-mini-labs**

This documentation page serves as an entry point; the lab repository contains the full material.

---

## MPI and Job Schedulers

On production HPC systems, MPI programs are typically launched using a scheduler such as Slurm, for example via `srun` or `sbatch`. Scheduler integration allows MPI jobs to run across multiple nodes in a controlled and reproducible way.

Details and example job scripts are provided in the mini-labs repository.

