---
kernelspec:
  name: bash
  display_name: bash
---
# Installing Conda

### What is Conda?

:::{figure} ../../images/anaconda-logo.png
:align: center
:::

According to the official website:

> Conda is a powerful command line tool for package and environment management that runs on
> Windows, MacOS, and Linux.

In other words, it is a cross-platform program for installing and managing packages for you.

### Why Bother?

Complex programs often rely on the functionality of other (smaller) programs. We call these _dependencies_. 

When new updates are introduced to the dependencies, the developer of our program should also update their code base to support these changes, otherwise their program may fail. To remedy this problem, each iteration of a program is labeled with a specific **version** as to support backwards compatibility with other programs.

The role of conda is to choose the specific version of each tool to be downloaded as to ensure compatibility. Behind the scenes, conda does the following:

1. Builds a dependency graph for a list of programs to be installed
2. Queries remote repositories to fetch specific versions of the tools.
3. Downloads the tools in an isolated environment, separate from all other programs in your system.

### Installation

A light-weight version of conda is available thru the [miniconda](https://docs.anaconda.com/miniconda/) distribution. To install, select your OS and run the associated commands:

#### Linux

```bash
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

#### MacOS

```bash
mkdir -p ~/miniconda3
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

#### Windows

```PowerShell
wget "https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe" -outfile ".\miniconda.exe"
Start-Process -FilePath ".\miniconda.exe" -ArgumentList "/S" -Wait
del .\miniconda.exe
```

### Basic Usage

The entry point for the program is the `conda` command. It is used in tandem with a subcommand such as `info`, `create`, and `activate`.

Check version and verify install:
```{code-cell} bash
:label: conda-info
conda info
```

Create a new environment called `mbb291`:
```{code-cell} bash
:label: conda-create
conda create --name mbb291
```

Activate the newly created environment:
```{code-cell} bash
:label: conda-activate
conda activate mbb291
```

Install a few tools from the [bioconda](https://bioconda.github.io/) repository in your current environment:
```{code-cell} bash
:label: conda-install
conda install -c bioconda chopper minimap2 flye
```

Exit the environment:
```{code-cell} bash
:label: conda-deactivate
conda deactivate
```
