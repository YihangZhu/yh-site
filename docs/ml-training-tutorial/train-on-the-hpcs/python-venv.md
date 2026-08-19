# Python virtual environment

It is important to create a Python virtual environment for running your
Python code on an HPC, for three reasons:

- It provides you with a Python environment that is required for running your
  Python code.
- In the Python virtual environment, you have the freedom to install any
  Python packages required to run your code. It is usually not allowed to
  install Python packages directly on the HPC, because you simply won't have
  permission to do so.
- You can create one Python virtual environment and reuse it for running
  different Python scripts.

Creating a Python virtual environment only requires three steps:

**(1)** Log in to the HPC. Check [here](ssh-related.md) for details.

**(2)** Load the Python module available on the HPC, e.g.:

```bash
module load Python/3.10.4
```

On Sulis, you can check the available Python modules using:

```bash
module spider python
```

**(3)** Create a new virtual environment with:

```bash
python3 -m venv /path-to-new-virtual-python
```

After creating the virtual environment, activate it by typing:

```bash
source /path-to-new-virtual-python/bin/activate
```

Then install the packages listed in `requirements.txt` by typing:

```bash
pip install -r requirements.txt
```

More information on installing a Python virtual environment is available
[here](https://docs.python-guide.org/dev/virtualenvs/#virtualenvironments-ref).
