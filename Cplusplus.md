# Hello HPC! - C++

This tutorial provides the instructions of installing the necessary software for running CV and C++ Qiskit programs. To facilitate learnig we have aliminated any use of OpenMP and MPI so you can just focus on the actual implementation of C/C++ and not on the parallelism of the system. Once you have finished this tutorial feel free to explore the SQD API complete demo which truly takes advantage of complete HPC capabilities.

The original repository for these materials can be found [here](https://github.com/hernandezj1/Qiskit-C-HPC-HelloWorld) but all instructions and commands have been ported over here for ease of instruction. We also do want to note that every HPOPC system and environment is different and these resources are meant as a a guideline but not as the only way that these codes can be ran whjich should be kept in mind if you run into any issues. 

## Non-Quantum System dependencies

Before creating the Qiskit environment please make sure that your system has the following: 
- Rust (latest stable recommended)
- C compiler with C++17 support
- CMake and Make (available as RPM packages on RHEL-compatible OS)
- Python ≥ 3.11 (including development header files)

Out of these it is very possible that your HPC resource does not install Rust by default. if that is the case run the following: 
```bash
curl https://sh.rustup.rs -sSf | sh
```

If you are working on your local environment please verify that all of these are installed and with approprioate versions.


## Environment creation

Given the need for a particular version of Python it is reccomended that you create a virtual environment for which we will utilize Conda. 
```bash
conda create -n quantum_c python=3.12 #Should be a version higher than 3.11, check those available in your HPC system
conda activate quantum_c
```

Then you can load appropriate environment modules that you will need going forward. The most important among these is a compiler with support for C++ 17 for which we will use gnu/13.2.0

```bash
module purge
module load webproxy # This allows connection to the internet, check the process for your HPC resource
module load gnu/13.2.0
```
:::{note}
Some HPC Centers will enable internet access and other will need to load a module such as the one we showcase here module load webproxy. Please verify your system specifications.
:::

## Qiskit dependendies

Having completed the environment setup we can now proceed to install and makes the Qiskit, Qiskit-Cpp, Qiskit Runtime and Qiskit resource manager interface repos, following the instructions set forth on the [Qiskit-C++ repo](https://github.com/Qiskit/qiskit-cpp/tree/main?tab=readme-ov-file). The Qiskit Runtime-C is not built given onogoing chnages but if desired it can be done if make is above v21.

The following commands are written in a bash script format [here in Installation.sh](https://github.com/hernandezj1/Qiskit-C-HPC-HelloWorld/blob/main/Installation.sh) but can be ran one by one in the appropriate order

#### Qiskit
```bash
git clone https://github.com/Qiskit/qiskit.git
cd qiskit
make c
```

#### Qiskit Runtime C

```bash
git clone https://github.com/Qiskit/qiskit-ibm-runtime-c.git
cd qiskit-ibm-runtime-c
mkdir build
cd build
cmake ..
make
```

#### Qiskit Resource Manager
```bash
git clone https://github.com/qiskit-community/qrmi.git
cd qrmi
cargo build --release
```

#### Qiskit CPP
```bash
git clone https://github.com/Qiskit/qiskit-cpp.git
```

## Building your code
Inside the Qiskit-CPP folder you will now find a folder called samples which should have 4 code samples allowing you try out different functionalities in Qiskit including 2 which allow submissions to the IBM Quantum Cloud. To use them we will now instantiate our environment variables and build them.

#### Step 1 - IBM credentials
Upload your account credentials to $HOME/.qiskit/qiskit-ibm.json (see https://github.com/Qiskit/qiskit-ibm-runtime?tab=readme-ov-file#save-your-account-on-disk) or set the following environment variables.

```bash
QISKIT_IBM_TOKEN=<your API key>
QISKIT_IBM_INSTANCE=<your CRN>
```

#### Step 2- Compile C++ files
Now we can proceed with the following instructions to compile the C++ samples thjat are included in the documentation. 
They are also written in a bash script format [here in Installation.sh](https://github.com/hernandezj1/Qiskit-C-HPC-HelloWorld/blob/main/Build.sh). 
Please make sure to subsitute the appropriate files to the files that need to be linked and to subsistute the resopurcve manager for runtime if wanted

```bash
cd qiskit-cpp/samples
mkdir build
cd build 
cmake  -DQISKIT_ROOT=/path/to/qiskit/ -DCMAKE_EXE_LINKER_FLAGS="-Wl,-rpath=$CONDA_PREFIX/lib" -DQRMI_ROOT=/path/to/qrmi/ ..
make
```

:::{note}
Here you must edit the paths to be preferably absolute paths from your root directory for ease of navigation and to minimize path errors. After this is done proceed.
:::

## Run your code

Having completed all of the above now we will run our codes, which we could do simply by the following line: 

```bash
./circuit-test
```

Which will run the sample script inside the __qiskit-cpp/samples__ folder. 

But given that most HPC centers use some type of job scheduler this is how ti would look in a simple Submit SLURM script for an actual submission to IBM hardware: 

```bash
#!/bin/bash
#SBATCH -J qiskit-job
#SBATCH -t 00:30:00
#SBATCH -A genacc_q
#SBATCH -n 1

#This will vary by HPC center but make sure you can access the web for submission
module load webproxy

# Load conda and activate your environment
module load anaconda
source activate ~/.conda/envs/quantum_c

./qiskit-cpp/samples/build/sampler_test
```








