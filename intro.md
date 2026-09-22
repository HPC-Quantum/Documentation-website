# Introduction

Learning quantum computing is no easy feat especially when you combine it with another complicated topic such as high-performance computing. For this reason we have created five suggested pathways that you can utilize to go through the materials here depending on your background. 

:::{figure} images/feynman-quantum-lecture-1963.jpg
:label: fig:Feynman lecture

Richard Feynman responding to students after a quantum mechanics lecture at Caltech, 1963. Courtesy of the Archives, California Institute of Technology.
:::

## Pathways 

Given the differing backgrounds of the users of this page we wanted to make sure that everybody can find relevant and background-specific content easily. Therefore, we have prepared the following pathways which you may use as guidelines to start your exploration of our tutorials & docs.

:::::{dropdown} __Quantum Pathway__
__Background:__ This Pathway is for those who __have__ HPC experience and would like to learn the basics of Qiskit and Quantum computing so they can start exploring quantum workflows. Familiarity with Python and/or C++ is preferred, as well as some comfort with Unix-like systems and bash scripts.

::::{grid} 1 1 2 3

:::{card}
:header: __I.Intro to Quantum Computing__
:link: https://hpc-quantum.github.io/Documentation-website/quantumintro/
This docs page will guide you to the appropriate Qiskit tutorials to start your Quantum journey!
:::

:::{card}
:header: __II.Intro to Quantum-HPC__
:link: https://hpc-quantum.github.io/Documentation-website/hybrid/
This docs page will guide you through the theory of how a hybrid workflow should work!
:::

:::{card}
:header: __III.Hybrid Orchestration__
:link: https://hpc-quantum.github.io/Documentation-website/hybridorch/
Explore system-level concepts including scheduling, synchronization, batching, resource coordination, and bottlenecks in hybrid Quantum-HPC workflows.
:::

:::{card}
:header: __IV.Qiskit on HPC__
:link: https://hpc-quantum.github.io/Documentation-website/qiskitonhpc/
This docs page will cover current work being done to use Qiskit on HPC and current learning materials.
:::
::::

After completing the four lessons above feel free to visit the [Python](/Python.md), [C++](/Cplusplus.md), and [API demo pages](/tutorial.md) at your own pace. We do recommend you grasp the content of the C++ basics page before proceeding to the demo content.

:::::

:::::{dropdown} __HPC Pathway__
__Background:__ This Pathway is for those who __have__ quantum computing experience and would like to learn the basics of High Performance computing before delving into hybrid workflows. Familiarity with Qiskit is expected.

::::{grid} 1 1 2 3

:::{card}
:header: __I.Intro to High Performance Computing__
:link: https://hpc-quantum.github.io/Documentation-website/hpcintro/
This docs page will guide you to the appropriate HPC tutorials to start your HPC journey!
:::

:::{card}
:header: __II.Understanding HPC__
:link: https://hpc-quantum.github.io/Documentation-website/hpctutorial/
This collection of pages will guide you through the use of OpenMP and MPI separate from quantum workflows for ease of learning.
:::

:::{card}
:header: __III.Hybrid Orchestration__
:link: https://hpc-quantum.github.io/Documentation-website/hybridorch/
Explore how classical HPC resources and quantum resources interact through scheduling, synchronization, batching, queueing, and resource coordination.
:::

:::{card}
:header: __IV.Qiskit on HPC__
:link: https://hpc-quantum.github.io/Documentation-website/qiskitonhpc/
This docs page will cover current work being done to use Qiskit on HPC and current learning materials.
:::
::::
:::::

:::::{dropdown} __Beginner Pathway__
__Background:__ This Pathway is for those who __don't__ have experience in either HPC or quantum computing. The introduction sections will redirect you to appropriate beginner materials before you come back for the hybrid workflow content on the rest of our page.


::::{grid} 1 1 2 3

:::{card} 
:header: __I.Intro to Quantum Computing__
:link: https://hpc-quantum.github.io/Documentation-website/quantumintro/
This docs page will guide you to the appropriate Qiskit tutorials to start your Quantum journey!
:::

:::{card} 
:header: __II.Intro to High Performance Computing__
:link: https://hpc-quantum.github.io/Documentation-website/hpcintro/
This docs page will guide you to the appropriate HPC tutorials to start your HPC journey!
:::

:::{card} 
:header: __III.Intro to Quantum-HPC__
:link: https://hpc-quantum.github.io/Documentation-website/hybrid/
This docs page will guide you through the theory of how a hybrid workflow should work!
:::
::::
:::::

:::::{dropdown} __Systems / Workflow Pathway__
__Background:__ This Pathway is for readers who want to focus on the system-level behavior of hybrid Quantum-HPC workflows: how classical and quantum resources interact, where bottlenecks arise, and how orchestration choices affect execution.

::::{grid} 1 1 2 3

:::{card}
:header: __I.Understanding HPC__
:link: https://hpc-quantum.github.io/Documentation-website/hpctutorial/
Review the parallel execution concepts behind OpenMP and MPI before moving into hybrid workflow behavior.
:::

:::{card}
:header: __II.Intro to Quantum-HPC__
:link: https://hpc-quantum.github.io/Documentation-website/hybrid/
Introduce the architecture and basic concepts behind hybrid Quantum-HPC workflows.
:::

:::{card}
:header: __III.Hybrid Orchestration__
:link: https://hpc-quantum.github.io/Documentation-website/hybridorch/
Study scheduling, batching, synchronization, resource coordination, and where hybrid workflows can stall.
:::

:::{card}
:header: __IV.Workflow Scenarios__
:link: https://hpc-quantum.github.io/Documentation-website/workflowscenarios/
Follow step-by-step workflow scenarios that illustrate synchronization, latency, serialization, queueing, and throttled execution.
:::

:::{card}
:header: __V.Workflow Explorer__
:link: https://hpc-quantum.github.io/Documentation-website/workflowexplorer/
Use the interactive Workflow Explorer to apply these orchestration concepts and explore hybrid workflow behavior.
:::
::::
:::::

:::::{dropdown} __Troubleshooting Pathway__
__Background:__ This Pathway is for those who are currently working on Python, C, & C++ HPC workflows with Qiskit. 
::::{grid} 1 1 2 3

:::{card} 
:header: __Hello HPC - Python__
:link: https://hpc-quantum.github.io/Documentation-website/python/
This tutorial guides you through the use of virtual environments to run Python workflows on HPC resources.
:::

:::{card} 
:header: __Hello HPC - C++__
:link: https://hpc-quantum.github.io/Documentation-website/cplusplus/
This tutorial guides you through the use of the Qiskit C++ API without the addition of OpenMP or MPI.
:::

:::{card} 
:header: __Official Qiskit API demo help__
:link: https://hpc-quantum.github.io/Documentation-website/tutorial/
This selection of pages has installation and instruction help to get the official IBM Qiskit C API demo up and running!
:::
::::
:::::





