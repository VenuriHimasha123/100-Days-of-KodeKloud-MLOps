# JupyterLab Configuration and Server Setup

## Challenge Objective

The xFusionCorp Industries data science team had a JupyterLab server that was not functioning correctly. The objective was to inspect the existing configuration, identify the incorrect settings, fix them, create any missing directories, and successfully start the JupyterLab server.

---

## Task Requirements

The running JupyterLab server had to satisfy the following requirements:

* Listen on port **8888**
* Bind to **0.0.0.0**
* Use **/root/notebooks/** as the notebook root directory
* Ensure the notebook directory exists
* Start JupyterLab using the provided configuration file

---

## Initial Investigation

First, I checked the contents of the `/root` directory.

```bash
ls /root
```

Output:

```text
code
```

I noticed that the required `notebooks` directory was missing.

---

## Creating the Notebook Directory

I created the required directory using:

```bash
mkdir -p /root/notebooks
```

Then verified it:

```bash
ls /root
```

Output:

```text
code
notebooks
```

---

## Inspecting the Configuration File

I opened the configuration file:

```bash
nano /root/code/jupyter_lab_config.py
```

The following settings were incorrect:

```python
c.ServerApp.root_dir = '/root/wrong-path'
c.ServerApp.port = 8000
c.ServerApp.ip = '1.1.1.1'
```

I corrected them to:

```python
c.ServerApp.root_dir = '/root/notebooks'
c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
```

---

## Problems I Encountered

### 1. Missing Notebook Directory

**Issue**

The `/root/notebooks` directory did not exist.

**Solution**

Created it using:

```bash
mkdir -p /root/notebooks
```

---

### 2. Incorrect Jupyter Configuration

**Issue**

The configuration file contained incorrect values for:

* Notebook root directory
* IP address
* Port number

These settings prevented the server from meeting the task requirements.

**Solution**

Updated the configuration to:

* Root Directory → `/root/notebooks`
* Port → `8888`
* IP Address → `0.0.0.0`

---

### 3. Corrupted Configuration File (My Mistake)

**Issue**

While editing the configuration file with Nano, I accidentally saved Nano interface text into the file.

The file contained unwanted lines such as:

```text
GNU nano 7.2
[ Read 8 lines ]
^G Help
```

When I tried to start JupyterLab, I received:

```text
IndentationError: unexpected indent
```

Because of this error, Jupyter ignored my configuration and started with its default settings.

---

### How I Fixed It

I inspected the configuration file using:

```bash
cat -n /root/code/jupyter_lab_config.py
```

This helped me identify the unwanted lines.

Instead of editing line by line, I replaced the file with a clean configuration containing only the required settings.

After verifying the file, the configuration looked like:

```python
# Jupyter configuration file for the xFusionCorp Industries data science team

# --- xFusionCorp team overrides ---
c.IdentityProvider.token = ''
c.ServerApp.disable_check_xsrf = True
c.ServerApp.root_dir = '/root/notebooks'
c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
```

---

## Starting JupyterLab

Activated the virtual environment:

```bash
source /root/code/ml-env/bin/activate
```

Started the server:

```bash
jupyter lab --config=/root/code/jupyter_lab_config.py --allow-root --no-browser &
```

---

## Verification

Verified that JupyterLab was listening on the correct port:

```bash
ss -tlnp | grep 8888
```

Output confirmed:

```text
0.0.0.0:8888
```

The server also displayed:

```text
Serving notebooks from local directory: /root/notebooks
```

This confirmed that all task requirements had been successfully met.

---

## Commands Used

```bash
ls /root

mkdir -p /root/notebooks

nano /root/code/jupyter_lab_config.py

cat -n /root/code/jupyter_lab_config.py

source /root/code/ml-env/bin/activate

jupyter lab --config=/root/code/jupyter_lab_config.py --allow-root --no-browser &

pkill -f jupyter-lab

ss -tlnp | grep 8888
```

---

## Key Learnings

* Learned how JupyterLab uses a configuration file.
* Understood the importance of binding the server to `0.0.0.0` instead of `127.0.0.1`.
* Learned how to verify open ports using the `ss` command.
* Gained experience troubleshooting Python configuration errors.
* Learned how accidental modifications to configuration files can prevent applications from loading correctly.
* Practiced debugging by reading error messages instead of immediately assuming the server itself was broken.

---

## Outcome

✅ Successfully repaired the JupyterLab configuration.

✅ Created the required notebook directory.

✅ Fixed configuration errors.

✅ Started JupyterLab successfully.

✅ Verified that the server was accessible on **0.0.0.0:8888** with the notebook root directory set to **/root/notebooks**.

**Status:** ✔️ Completed Successfully
