# slc9000-api-notebook
Jupyter notebook for testing the SLC9000 API

# SLC9000 API Jupyter Notebook

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

On Windows (Command Prompt):

```cmd
.\.venv\Scripts\activate.bat
```

You should see `(.venv)` at the beginning of your shell prompt once it is activated.

## 3. Install dependencies

The project dependencies are listed in `requirements.txt`. Install them with:

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## 4. Set environment variables

The notebook expects the following environment variables to be set so it can authenticate to the SLC9000:

- `SLC9K_USER` — API username
- `SLC9K_PW` — API password

On macOS / Linux:

```bash
export SLC9K_USER="your-username"
export SLC9K_PW="your-password"
```

On Windows (PowerShell):

```powershell
$env:SLC9K_USER="your-username"
$env:SLC9K_PW="your-password"
```

On Windows (Command Prompt):

```cmd
set SLC9K_USER=your-username
set SLC9K_PW=your-password
```

Alternatively, you can use the `config.json` file as described in the notebook to provide connection and authentication settings.

## 5. Launch JupyterLab (or Jupyter Notebook)

From the activated virtual environment in the repo root, start Jupyter:

```bash
jupyter lab
```

or, if you prefer the classic interface:

```bash
jupyter notebook
```

This will open Jupyter in your default web browser.

## 6. Open and run the notebook

1. In the Jupyter UI, navigate to the repository folder.
2. Open `slc9000_api.ipynb`.
3. Run the cells in order (e.g., using **Run → Run All Cells** or `Shift+Enter` per cell).

The notebook will:

- Configure a `requests` session for the SLC9000 API.
- Optionally load settings from `config.json`.
- Authenticate to the SLC9000 and obtain a session token.
- Demonstrate various API calls (status, firmware, network interfaces, etc.).
- Show a workaround for PUT request timeouts using `curl`.

## 7. Deactivate the virtual environment

When you are finished, you can deactivate the virtual environment with:

```bash
deactivate
```

## Troubleshooting

- If `requests` to the SLC9000 fail with TLS/SSL errors, verify that the `VERIFY` setting and certificate handling match your environment.
- Ensure the SLC9000 IP address and credentials in `config.json` or environment variables are correct.
- If Jupyter does not open automatically, copy the URL printed in the terminal (including the token) and paste it into your browser.