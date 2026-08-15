# slc9000-api-notebook

Jupyter notebook for testing the SLC9000 API.

## SLC9000 API Jupyter Notebook

This repository contains a Jupyter notebook (`slc9000_api.ipynb`) that demonstrates how to interact with an SLC9000 device via its REST API.

## Prerequisites

- Python 3.10+ installed  
- `git` installed  
- Access to an SLC9000 device and credentials  
- Optional but recommended: `python -m venv` available for virtual environments  

## 1. Clone the repository

```bash
git clone <YOUR-REPO-URL>
cd <YOUR-REPO-DIRECTORY>
```

Replace `<YOUR-REPO-URL>` and `<YOUR-REPO-DIRECTORY>` with your actual repository URL and folder name.

## 2. Create and activate a virtual environment

From the root of the repository, create a virtual environment:

```bash
python -m venv .venv
```

Activate the virtual environment:

On macOS / Linux:

```bash
source .venv/bin/activate
```

On Windows (PowerShell):

```powershell
.\.venv\Scripts\Activate.ps1
```

## 3. Install dependencies

From the root of the repository (with the virtual environment activated):

```bash
pip install -r requirements.txt
```

## 4. Configure connection settings

The notebook can be configured in **two ways**: environment variables or a `config.json` file.

### Option A: Environment variables

Set the following environment variables before starting Jupyter:

- `SLC9K_USER` – username for the SLC9000 (e.g. `sysadmin`)  
- `SLC9K_PW` – password for the SLC9000  
- `PERCEPXION_HOST` – Percepxion cloud endpoint host (e.g. `api.gopercepxion.ai`)  

Example (macOS / Linux):

```bash
export SLC9K_USER=youruser
export SLC9K_PW=yourpassword
export PERCEPXION_HOST=api.gopercepxion.ai
```

### Option B: `config.json` file

Instead of environment variables, you can use the provided `config.json` file. The notebook’s `load_config` function reads this file and populates the connection settings.

Create or edit `config.json` in the repository root with content like:

```json
{
  "TIMEOUT": 10,
  "VERIFY": false,
  "USERNAME": "youruser",
  "PASSWORD": "yourpassword",
  "PERCEPXION_HOST": "api.gopercepxion.ai"
}
```

On startup, the notebook calls:

```python
load_config()
```

which updates the global `TIMEOUT`, `VERIFY`, `USERNAME`, `PASSWORD`, and `PERCEPXION_HOST` values from this file. Any values not present in `config.json` will fall back to their existing defaults (or environment variables, if you choose to use both).

## 5. Launch JupyterLab / Jupyter Notebook

From the repository root (with the virtual environment activated):

```bash
jupyter lab
```

or

```bash
jupyter notebook
```

Then open `slc9000_api.ipynb` and run the cells from top to bottom to authenticate to the SLC9000, inspect system status, and exercise the various REST API endpoints.