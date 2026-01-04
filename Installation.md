# Installation Help

This content was created to assist users who may be unfamiliar with environment/image/wheel setups. In plain terms, the docker image shown and implemented here serves as a template for a miniaturized computer system, included with packages/libraries from different languages. In general, a docker image allows a user to easily implement a fully operational container environment, with this one specifically created and tailored toward the [Qiskit-C-API-Demo](https://www.ibm.com/quantum/blog/c-api-enables-end-to-end-hpc-demo).

## Implementing GitHub Codespace

Here we will describe how to create a GitHub codespace through an existing fork created by Jonah Sachs. GitHub codespaces allow you to run a custom development environment through GitHub. For more information, see [GitHub Codespaces](https://docs.github.com/en/codespaces).

**Using My Fork** Go to my already created [Fork](https://github.com/Jsachs14/docker_qiskit-c-api-demo/tree/main). If you want to make and keep changes, fork this repository (or use it as a template) and create a codespace from your copy. You won’t be able to push changes directly to this repository’s `main` branch.

To create the codespace, click **Code**, and then the **Codespaces** tab. From here click **Create codespace on main** to create your codespace. Then, a UI similar to VS Code should open up. In your terminal, you should be in:

    /workspaces/docker_qiskit-c-api-demo

### What happens automatically

When the codespace is created, the devcontainer will build automatically using `.devcontainer/Dockerfile`. After the container finishes building, a post-create script will run automatically:

- `.devcontainer/setup.sh` (triggered by `postCreateCommand` in `devcontainer.json`)

This script will:

- Initialize git submodules (`git submodule update --init --recursive`)
- Build the Qiskit C extension (`deps/qiskit`, `make c`)
- Build the QRMI service (`deps/qrmi`, `cargo build --release`)
- Configure + build the demo (`cmake ..` then `make`)

You’ll know setup is complete when you see:

    === [setup] Done. Binaries are in build/ ===

Once this completes, you will still need to add your IBM Quantum credentials.

### IBM Quantum credentials

**Important:** Do not put credentials in `code.py` (recommended: use a Codespaces Secret).

1. Create a GitHub Codespaces secret named `QISKIT_IBM_TOKEN` containing your IBM Quantum API token.
2. (Optional but recommended) Create a second Codespaces secret named `QISKIT_IBM_INSTANCE` containing your IBM Quantum instance (instance name or CRN). This helps avoid ambiguity and makes configuration more reliable.
3. Inside the codespace terminal, verify the secrets are present as environment variables:

    echo "$QISKIT_IBM_TOKEN" | head -c 4; echo
    echo "$QISKIT_IBM_INSTANCE" | head -c 4; echo

4. Save credentials:

   **If you set `QISKIT_IBM_INSTANCE` (recommended):**

    python3 -c "import os; from qiskit_ibm_runtime import QiskitRuntimeService as S; S.save_account(channel='ibm_quantum_platform', token=os.environ['QISKIT_IBM_TOKEN'], instance=os.environ['QISKIT_IBM_INSTANCE'], set_as_default=True, overwrite=True)"

   **If you did NOT set `QISKIT_IBM_INSTANCE` (token only):**

    python3 -c "import os; from qiskit_ibm_runtime import QiskitRuntimeService as S; S.save_account(channel='ibm_quantum_platform', token=os.environ['QISKIT_IBM_TOKEN'], overwrite=True)"

For additional instructions on how to configure your IBM Quantum account and how to save your credentials, refer to the official documentation:

- [Cloud setup](https://quantum.cloud.ibm.com/docs/en/guides/cloud-setup)
- [Save credentials](https://quantum.cloud.ibm.com/docs/en/guides/save-credentials#save-credentials-that-access-a-specific-instance)

### Codespaces billing / limits

GitHub may charge for Codespaces usage after a certain amount of compute/storage. For a free user this is **120 core-hours monthly** and **15 GB of storage**. Ensure you do not reach this limit to avoid being billed. If you do not add a billing method, GitHub will hard-limit Codespaces usage once the free quota is exhausted.

### Using this devcontainer locally

You can also use the `.devcontainer` folder in your own local copy of the Qiskit C API demo repo. Copy the `.devcontainer/` folder into your working directory and run:

    bash .devcontainer/setup.sh
