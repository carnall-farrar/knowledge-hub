# Conda

Blurb about Conda.
How to install: look at getting-setup

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
conda env list
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