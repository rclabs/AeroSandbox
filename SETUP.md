# AeroSandbox Local Setup

## 1) Create the virtual environment

Run from the repository root:

```bash
cd /home/ravi/workspace/AeroSandbox
uv python install 3.12
uv venv --python 3.12 --seed --clear .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
python -m pip install -e '.[full]'
```

Notes:
- `aerosandbox[full]` currently works best on Python 3.12 in this environment.
- Installing inside `.venv` avoids dependency conflicts with your global Python packages.

## 2) Verify installation

```bash
pip check
python -c "import aerosandbox as asb; print(asb.__version__)"
```

## 3) Activate env for daily use

Each new terminal session:

```bash
cd /home/ravi/workspace/AeroSandbox
source .venv/bin/activate
```

## 4) Use with VS Code notebooks

If needed, install kernel support in the venv:

```bash
cd /home/ravi/workspace/AeroSandbox
source .venv/bin/activate
python -m pip install ipykernel
```

Then in VS Code:
1. Open a notebook (`.ipynb`).
2. Click the kernel picker in the top-right.
3. Select the interpreter at `/home/ravi/workspace/AeroSandbox/.venv/bin/python`.

Optional (if you use Jupyter outside VS Code):

```bash
cd /home/ravi/workspace/AeroSandbox
source .venv/bin/activate
python -m pip install jupyterlab ipykernel
python -m ipykernel install --user --name aerosandbox-venv --display-name "Python (.venv AeroSandbox)"
jupyter lab
```
