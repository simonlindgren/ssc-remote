# VS Code Remote on Swedish Science Cloud (GPU-ready)

This guide describes how to set up a **single-user research machine** on Swedish Science Cloud (SSC) and work on it using **VS Code Remote (SSH)** instead of JupyterHub/JupyterLab.

The result is a powerful remote Linux workstation with:
- full terminal access
- Python environments
- Git
- Jupyter notebooks (inside VS Code)
- long-running jobs
- optional GPU acceleration (A100)

---

## 1. Get access to SSC

If you work at a Swedish university, you can apply for free computing resources from Swedish Science Cloud (via NAISS).

1. Go to https://supr.naiss.se and create an account using your university credentials.
2. Create a new proposal and wait for approval (usually 1–2 days).
3. Once approved, go to https://cloud.snic.se and open a dashboard for the appropriate region (WEST-1, EAST-1, or NORTH-1).

---

## 2. Create a virtual machine

1. Go to **Compute → Images**.
2. Pick an OS and click **Launch**.  
   Recommended: **Ubuntu 22.04 LTS**.

### Launch Instance settings

- **Details**  
  Enter an instance name.

- **Source**  
  Make sure the chosen OS is selected.  
  Set **Volume Size (GB)** to up to `1000` (SSC allows max 1 TB).

- **Flavor**  
  Choose hardware, for example:  
  `ssc.gpu.8c.32gb.1xA100`

- **Networks**  
  Select the **NAISS** network.

- **Network Ports**  
  Skip.

- **Security Groups**  
  Make sure `default` is selected.

- **Key Pair**  
  Create a new key pair.  
  Give it a name and leave *Key Type* empty.  
  Download and save the key locally as a `.pem` file (for example `key.pem`).  
  Restrict permissions:
  ```bash
  chmod 600 key.pem
