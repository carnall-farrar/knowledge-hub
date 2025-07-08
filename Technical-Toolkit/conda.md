# Conda
Conda is a popular open-source, cross-platform package and environment management system. It's designed to simplify the installation, management, and updating of software packages and their dependencies, particularly for data science, machine learning, and AI workflows. Conda is language-agnostic, but is widely used for Python and R.

It's key features:

* **Environment Management**: Conda allows you to create isolated environments for different projects, ensuring that dependencies for one project don't conflict with those of another.

* **Package Management**: Conda handles the installation, updating, and removal of software packages, including Python libraries and other dependencies.

To install conda, checkout out the [Getting Setup guide](../How-To/getting-setup.md).

## Helpful commands

#### Create an environment

- From scratch:
```bash
conda create -n <env-name> python=3.10
```

- From an environment file:
```bash
conda env create -f <path-to-environment.yml>
```

#### Delete an environment
```bash
conda env remove -n <env-name>
```

#### Activate/Deactivate an environment
```bash
conda activate <env-name>
```

```bash
conda deactivate
```

#### List available conda environments
```bash
conda env list
```

#### List packages installed within active environment
```bash
conda list
```

#### Uninstall all packages within an environment
```bash
conda remove --name <env-name> --all
```

#### Export conda environment
```bash
conda env export > environment.yml --no-builds
```

#### Juupyter notebook kernels with conda environments

To create an ipykernel which uses a conda environment:

```bash
conda activate <env-name>
uv pip install ipykernel
python -m ipykernel install --user --name=<env-name>
```

Run `jupyter kernelspec list` to get the paths of all available kernels

To uninstall a kernel:
```bash
jupyter kernelspec uninstall <unwanted-kernel>
```