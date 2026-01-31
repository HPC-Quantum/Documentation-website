# OpenMP Mini-Lab

OpenMP is a shared-memory parallel programming model designed to exploit **multiple CPU cores on a single node**. It enables developers to parallelize existing C/C++ or Fortran code using compiler directives, often with minimal changes to the original program structure.

In HPC–Quantum workflows, OpenMP is commonly used to accelerate **local classical workloads**, such as numerical kernels, simulations, and pre- or post-processing steps that run on a single compute node.

---

## What This Mini-Lab Demonstrates

This mini-lab focuses on the core ideas behind OpenMP:

- Thread-based parallelism within a single node
- How work is shared among threads
- How performance changes as the number of threads increases
- The relationship between cores, threads, and shared memory

The emphasis is on building intuition rather than achieving peak performance.

---

## Running the OpenMP Example

A minimal compile-and-run workflow looks like this:

```bash
gcc -fopenmp hello_openmp.c -o hello_openmp
export OMP_NUM_THREADS=4
./hello_openmp
```

- `-fopenmp` enables OpenMP support in the compiler
- `OMP_NUM_THREADS` controls how many threads are launched
- The program runs on a **single node** using shared memory

You can experiment by changing the number of threads and observing how the output or runtime changes.

---

## Full Lab and Exercises

The complete OpenMP mini-lab, including explanations, variations, and additional exercises, is maintained in the following repository:

👉 **https://github.com/friedsam/hpc-qc-mini-labs**

This page is intentionally lightweight; the GitHub repository is the source of truth for the full lab material.

---

## Notes on Containers

The OpenMP examples can also be run inside a containerized environment. Containers are useful for:

- Ensuring consistent compiler and library versions
- Running the same workflow locally and on HPC systems
- Simplifying setup for new users

See the mini-labs repository for details on building and running the provided container image.


