# Day 006 - Ruff and Black Code Quality Setup

## Task Overview

The xFusionCorp Industries ML team enforces code quality standards using **Ruff** and **Black** for every pull request.

The project located at:

```
/root/code/fraud-detection/
```

was failing both Ruff lint checks and Black formatting checks.

The objective was to configure Ruff and Black correctly and ensure the source code passes both validation tools.

---

## Initial Issue

The project contained a `pyproject.toml` file with incorrect configurations:

* Ruff line length was not set to the required value.
* Ruff lint rule selection was incomplete.
* Black line length was not configured correctly.
* Source files contained linting and formatting issues.

---

## Solution

Updated `pyproject.toml` configuration:

```toml
[project]
name = "fraud-detection"
version = "0.1.0"

[tool.ruff]
line-length = 120

[tool.ruff.lint]
select = ["E", "F", "W", "I"]

[tool.black]
line-length = 120
```

### Ruff Configuration

Configured Ruff with:

* Line length: `120`
* Enabled lint rules:

  * E (pycodestyle errors)
  * F (Pyflakes)
  * W (pycodestyle warnings)
  * I (Import sorting)

---

## Fixing Code Issues

Executed Ruff auto-fix:

```bash
ruff check src/ --fix
```

This fixed issues including:

* Unused imports
* Incorrect import formatting

Then formatted the source code using Black:

```bash
black src/
```

---

## Verification

Checked Ruff:

```bash
ruff check src/
```

Result:

```
All checks passed!
```

Checked Black:

```bash
black --check src/
```

Result:

```
All done! ✨ 🍰 ✨
```

---

## Final Status

✅ Ruff configured successfully
✅ Black configured successfully
✅ Line length set to 120 for both tools
✅ Ruff rules E, F, W, I enabled
✅ Source code passes Ruff checks
✅ Source code passes Black formatting checks

Task 6 completed successfully.
