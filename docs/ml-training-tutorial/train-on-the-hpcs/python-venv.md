# Python virtual venv

It is important to create a python virtue environment for running your python
code on an HPC for three reasons:

- it provides you with a Python environment that is required for running your
  Python code.
- in the Python virtue environment, you can have the freedom to install any
  Python packages that are required to run your code. It is usually not allowed
  to install Python packages in the HPC, because you simply will not have
  permission to do so.
- you can just create one Python virtue environment and use it for running
  different Python codes.

Creating a Python virtue environment only requires three steps:

**(1)** Log in to the HPC. Check [here](ssh-related.md) for details.

**(2)** Load the Python module available on the HPC. Type, e.g.:

```bash
module load Python/3.10.4
```

then enter. On HPC Sulis you can check the available python module using:

```bash
module spider python
```

**(3)** Create a new virtual environment with:

```bash
python3 -m venv /path-to-new-virtual-python
```

After creating the virtual env, we can activate it by typing:

```bash
source path-to-new-virtual-python/bin/activate
```

Then we can install packages that are in the file `requirements.txt` by typing:

```bash
pip install -r requirements.txt
```

Other information about installing Python virtual environment is available
[here](https://docs.python-guide.org/dev/virtualenvs/#virtualenvironments-ref).
