# llm-engineering-lab

## Setup Instructions

1. Open VS Code.
2. Open the project folder: `llm-engineering-lab`.
3. Open the integrated terminal inside VS Code.
4. Run the following command:

```powershell
uv sync
```

5. Activate the virtual environment:

```powershell
.venv\Scripts\activate
```

6. Install the IPython kernel for this project:

```powershell
python -m ipykernel install --user --name=llm-engineering-lab
```
7. Before running any code cell in a Jupyter notebook, select the `llm-engineering-lab` kernel from the top-right kernel selector of the notebook.




---
# 📌 Pinning Python Versions in `uv` Projects

When working with [`uv`](https://github.com/astral-sh/uv), you may notice that projects are often **pinned** to a specific Python version. This ensures consistency across machines and avoids the dreaded "works on my machine" problem.

---

## 🔍 What Does Pinning Mean?

Pinning a Python version tells `uv` to always use a specific interpreter for your project.  

- A `.python-version` file is created in your project directory.  
- This file records the exact Python version (e.g., `3.12.10`).  
- Whenever you run `uv sync`, `uv run`, or other commands inside the project, `uv` enforces that pinned version.  

Think of it as a **lockfile for your interpreter**, similar to how `uv.lock` locks your dependencies.

---

## ⚡ Why Pin Python?

- **Reproducibility**: Everyone working on the project uses the same interpreter version.  
- **Compatibility**: Some packages only support certain Python versions. Pinning avoids accidental mismatches.  
- **Deployment safety**: Servers and CI/CD pipelines can replicate the same environment without surprises.  

---

## 🚨 Common Error: `uv sync` Fails

You might see an error like:

    "error: No interpreter found for Python 3.12.12 in managed installations, search path, or registry"


This happens when the project is pinned to a Python version that isn’t installed or isn’t available for download on your platform.

---

## 🛠️ How to Resolve the Error

Here’s a step-by-step guide:

1. **List available interpreters**
   ```powershell
   uv python ls

This shows which versions are installed or can be downloaded.

2. **Install a supported version**
    ```powershell
    uv python install 3.12.10

(Replace 3.12.10 with the nearest available version from the list.)

3. **Pin the project to that version**
    ```powershell
    uv python pin 3.12.10  

4. **Sync the environment**
    ```powershell
    uv sync

5. **Verify the interpreter**
    ```powershell
    uv run python --version

Output should match the pinned version.