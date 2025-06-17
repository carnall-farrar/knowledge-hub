# Getting Set-up

## 0: Rami

Message Rami on teams to get setup with the following:
- Github
- Athena
- Hedwig

## 1: Get `Elevate To Admin` privileges on your MAC

Email moof (support@moof-it.co.uk), CF's 3rd party IT support partner, to request access to the `Elevate To Admin` tool. This tool allows you administrator access to your MAC computer, which is necessary for the installation and configuration of various software. We'll need this for a few of the steps to come.

The email needs to provide a justification for receiving access to this tool. Here's a simple template:

```
Hi moof,

My name is <Your Name Here>, and I'm a new data scientist/engineer at CF. I'm writing to request admin rights to my laptop. I need admin rights to install and configure development tools. 

Thanks so much for your help!

Cheers,
<Your Name Here>
```

Please cc our office manager Rebecca Cummins (rebecca.cummins@carnallfarrar.com) to gain her approval.

Once granted:
1. Please open the application 'Self Service' on your computer
2. Search 'Elevate To Admin' in the search bar
3. Click `Elevate`.

This will give you temporary admin rights, however you can run this policy has many times as you need.


## 2: Install VSCode

At CF, our IDE (Integrated Development Environment) of choice is [VSCODE](https://code.visualstudio.com/).
You can find the download link [here](https://code.visualstudio.com/download#)

Some extensions we're obsessed with are:
- Data Wrangler
- Jupyter
- Rainbow CSV
- Python Debugger


## 3: Install Brew

Homebrew is a package manager for MacOS and Linux. It installs the stuff you need that Apple (or your Linux system) didn’t.

You can install homebrew by downloading the `.pkg` file from [here](https://brew.sh/) or by pasting this command into a MAC terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 4: Install Conda

Currently, our python environment manager of choice is `conda`. We use miniconda, a miniature installation of the `Anaconda` distribution that includes only conda, Python, the packages they both depend on, and a small number of other useful packages.

To download miniconda, visit [this link](https://www.anaconda.com/download/success) and download the miniconda installer for Apple Silicon and run it.


## 5: Install UV

UV is an extremely fast Python package manager and installer, written in Rust.
Here, we use Conda as our package manager and UV as the package installer (replacing `pip install` or `conda install` where possible). We'll be using UV to install packages into project-specific conda environments.

The instructions to install uv can be found [here](https://docs.astral.sh/uv/#getting-started). For MacOS or Linux;

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

or through Homebrew

```bash
brew install uv
```

## 6: Git

To install git, run

```bash
brew install git
```

We think the best way to configure git local access is to use the `Git Crendential Manager` (over SSH keys). GCM is a tool that securely stores your Git credentials on macOS, simplifying authentication with Git repositories. It eliminates the need to manually enter credentials every time you interact with a remote repository. GCM supports various authentication methods, including HTTP/HTTPS username/password and SSH key file authentication. To install, run:

```bash
brew install --cask git-credential-manager
```

Configure git globally as such:

```bash
git config --global user.name "<Your Name>"
git config --global user.email "<Your Email>"
git config --global init.defaultBranch main
```

When you interact with a Git repository for the first time (e.g., cloning, pushing, pulling), Git will launch a browser window for you to authenticate. After successful authentication, your credentials are saved in the macOS keychain, a secure system for storing sensitive information. 


## 7: You're all set up!