# Day 003 - Python Dependency Management with UV

**Date:** July 10, 2026

## 📌 Task Overview

Today's task focused on Python dependency management using **UV**. The objective was to correct an existing `requirements.in` file and generate a pinned `requirements.txt` lockfile containing exact versions of all required packages and their dependencies.

---

## 🎯 Objective

The final solution needed to satisfy the following requirements:

- Correct the `requirements.in` file.
- Include exactly these four top-level packages:
  - `scikit-learn`
  - `mlflow`
  - `pandas`
  - `numpy`
- Generate a pinned `requirements.txt` using UV.
- Ensure all resolved packages are pinned using `==`.

---

## 📂 Initial Situation

The provided `requirements.in` file contained:

```text
# Fraud detection project dependencies
sklearn
mlflow>=100.0
numpy
```

At first glance, it looked simple, but there were several issues that prevented it from meeting the required standards.

---

# 🚧 Challenges I Faced

## 1️⃣ Incorrect Package Name

The file contained:

```text
sklearn
```

Initially, I thought this was correct because we import it in Python using:

```python
import sklearn
```

However, I learned that the package name on PyPI is actually:

```text
scikit-learn
```

### ✅ Solution

Replaced:

```text
sklearn
```

with:

```text
scikit-learn
```

---

## 2️⃣ Invalid Version Constraint

The original file specified:

```text
mlflow>=100.0
```

I wasn't sure why this was incorrect until I realized that such a version doesn't exist. UV could not resolve the dependency because the version requirement was impossible to satisfy.

### ✅ Solution

Removed the invalid version constraint and changed it to:

```text
mlflow
```

This allowed UV to resolve a compatible version automatically.

---

## 3️⃣ Missing Required Package

The task required four top-level packages, but `pandas` was missing.

### ✅ Solution

Added:

```text
pandas
```

---

# ✅ Corrected `requirements.in`

```text
# Fraud detection project dependencies
scikit-learn
mlflow
pandas
numpy
```

---

# 💻 Commands Used

Navigate to the project directory:

```bash
cd /root/code/fraud-detection
```

View the current file:

```bash
cat requirements.in
```

Edit the file:

```bash
nano requirements.in
```

Generate the lockfile:

```bash
uv pip compile requirements.in -o requirements.txt
```

Verify the generated file:

```bash
cat requirements.txt
```

---

# 🎉 Result

The command completed successfully and generated a `requirements.txt` file containing:

- Exact versions (`==`) for all top-level packages.
- All transitive dependencies resolved automatically by UV.

This ensures that every developer working on the project installs the exact same dependency versions.

---

# 📚 Key Learnings

Today I learned:

- The difference between `requirements.in` and `requirements.txt`.
- Why lockfiles are important for reproducible environments.
- The difference between Python import names and package installation names.
- How UV resolves package dependencies automatically.
- Why invalid version constraints can cause dependency resolution failures.

---

# 💡 Reflection

Initially, I thought this task only required editing a text file. After completing it, I understood that dependency management is an essential part of MLOps. Lockfiles help ensure consistency across development, testing, and production environments by guaranteeing that everyone uses the same package versions.

This task also reinforced the importance of carefully reading requirements and understanding package naming conventions.

---

## ✅ Status

**Task Completed Successfully**

### Skills Practiced

- UV
- Python Dependency Management
- Lockfiles
- Dependency Resolution
- MLOps Fundamentals
