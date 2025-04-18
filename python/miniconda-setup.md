# Miniconda Installation and Setup Guide

Miniconda is a minimal installer for Conda, Python, and their dependencies. It provides a lightweight alternative to the full Anaconda distribution, allowing users to install only the packages they need.

---

## Table of Contents

1. [System Requirements](#1-system-requirements)
2. [Downloading Miniconda](#2-downloading-miniconda)
3. [Installing Miniconda](#3-installing-miniconda)
   - [Windows Installation](#windows-installation)
   - [macOS Installation](#macos-installation)
   - [Linux Installation](#linux-installation)
4. [Verifying the Installation](#4-verifying-the-installation)
5. [Basic Conda Commands](#5-basic-conda-commands)
6. [Setting Up the Conda Environment](#6-setting-up-the-conda-environment)
7. [Updating Conda](#7-updating-conda-and-packages)
8. [Creating and Managing Environments](#8-creating-and-managing-environments)
9. [Installing Packages](#9-installing-packages)
10. [Uninstalling Miniconda](#10-uninstalling-miniconda)
11. [Troubleshooting](#11-troubleshooting)
12. [Environment Configuration Files](#12-environment-configuration-files)

---

## 1. System Requirements

Miniconda supports the following operating systems:

- **Windows**: Windows 8.1 or newer.
- **macOS**: macOS 10.9 or newer.
- **Linux**: Various distributions.

For Miniconda or Miniforge: Aprox. 400 MB disk space.
For Anaconda Distribution: Minimum 3GB.

---

## 2. Downloading Miniconda

Visit the official Anaconda website to download the Miniconda installer suitable for your operating system:

- **Windows**: [Miniconda3 Windows 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe)
- **macOS**: [Miniconda3 macOS 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh)
- **Linux**: [Miniconda3 Linux 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh)

---

## 3. Installing Miniconda

### Windows Installation

1. **Run the Installer**:

   - Locate the downloaded `Miniconda3-latest-Windows-x86_64.exe` file and double-click to launch the installer.

2. **Follow Installation Prompts**:

   - **License Agreement**: Read and accept the license agreement.
   - **Installation Type**: Select "Just Me" (recommended).
   - **Installation Location**: Choose an installation directory (avoid spaces).
   - **Advanced Options**:
     - Optionally add Miniconda to the system PATH.
     - Optionally register Miniconda as the system Python.

3. **Complete Installation**:
   - Click "Install" and wait for the process to complete.
   - Once finished, click "Finish" to exit the installer.

_For detailed Windows installation instructions, refer to the [conda documentation](https://docs.conda.io/projects/conda/en/stable/user-guide/install/windows.html)._

### macOS Installation

1. **Download the Installer**:

   - Use `curl` to download the Miniconda installer:
     ```bash
     curl -sL "https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh" -o "Miniconda3.sh"
     ```

2. **Verify the Installer (Optional but Recommended)**:

   - Generate the SHA-256 hash of the downloaded installer:
     ```bash
     shasum -a 256 Miniconda3.sh
     ```
     Compare the output with the official hash provided on the Miniconda website to ensure integrity.

3. **Run the Installer**:

   - Make the installer executable:
     ```bash
     chmod +x Miniconda3.sh
     ```
   - Execute the installer:
     ```bash
     ./Miniconda3.sh
     ```

4. **Follow Installation Prompts**:

   - Press Enter to review the license agreement, type `yes` to accept.
   - Specify the installation location or press Enter for default.
   - Choose to initialize Miniconda by running `conda init`.

5. **Complete Installation**:

   - Close and reopen the Terminal to apply changes.

6. **Verify the Installation**:
   - In the Terminal, run:
     ```bash
     conda --version
     ```
     This should display the installed Conda version, confirming a successful installation.

_For detailed macOS installation instructions, see the [conda documentation](https://docs.conda.io/projects/conda/en/stable/user-guide/install/macos.html)._

### Linux Installation

1. **Open Terminal**:

   - Access the terminal emulator specific to your Linux distribution.

2. **Download the Installer**:

   - Using `wget`:

     ```bash
     wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
     ```

     Or using `curl`:

     ```bash
     curl -sL "https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh" -o "Miniconda3.sh"
     ```

3. **Verify the Installer (Optional but Recommended)**:

   - Generate the SHA-256 hash of the downloaded installer:
     ```bash
     sha256sum Miniconda3-latest-Linux-x86_64.sh
     ```
     Compare the output with the official hash provided on the Miniconda website to ensure integrity.

4. **Run the Installer**:

   - Make the installer executable:
     ```bash
     chmod +x Miniconda3-latest-Linux-x86_64.sh
     ```
   - Execute the installer:
     ```bash
     ./Miniconda3-latest-Linux-x86_64.sh
     ```

5. **Follow Installation Prompts**:

   - Press Enter to review the license, then type `yes` to accept.
   - Specify the installation location or press Enter for the default.
   - Allow the installer to initialize Conda.

6. **Complete Installation**:

   - Close and reopen the Terminal to apply changes.

7. **Verify the Installation**:

   - In the Terminal, run:

     ```bash
     conda --version
     ```

     This should display the installed Conda version, confirming a successful installation.

_For detailed Linux installation instructions, refer to the [conda documentation](https://docs.conda.io/projects/conda/en/stable/user-guide/install/linux.html)._

---

## 4. Verifying the Installation

After installation, verify that Miniconda is set up correctly:

1. **Open Terminal or Command Prompt**:

   - On Windows, open "Anaconda Prompt".
   - On macOS or Linux, open the standard terminal.

2. **Check Conda Version**:

   - Run the following command:
     ```bash
     conda --version
     ```
     This should display the installed Conda version, confirming a successful installation.

3. **List Installed Packages**:
   - Run:
     ```bash
     conda list
     ```
     This command displays installed packages, verifying that Conda is functioning properly.

---

## 5. Basic Conda Commands

| Command                             | Description                             |
| ----------------------------------- | --------------------------------------- |
| `conda create -n myenv python=3.13` | create environment with specific Python |
| `conda activate myenv`              | Activate environment                    |
| `conda deactivate`                  | Deactivate current environment          |
| `conda env list`                    | List all environments                   |
| `conda install numpy pandas`        | Install packages                        |
| `conda remove --name myenv --all`   | Delete environment                      |

---

## 6. Setting Up the Conda Environment

Creating isolated environments helps manage dependencies and avoid package conflicts.

1. **Initialize Conda** (if not already initialized):

   ```bash
   conda init
   ```

   Then close and reopen your terminal.

2. **Create a New Environment**:  
   Replace `myenv` with your desired environment name and specify the Python version (e.g., 3.9):

   ```bash
   conda create --name myenv python=3.9
   ```

   Follow the prompts to confirm creation.

3. **Activate the Environment**:

   ```bash
   conda activate myenv
   ```

   Your command prompt should now indicate that the environment is active.

4. **Deactivate the Environment**:
   When finished, run:
   ```bash
   conda deactivate
   ```
   This returns you to the base environment.

---

## 7. Updating Conda and Packages

Keeping Conda and its packages updated is crucial for security and performance.

1. **Update Conda**:

   ```bash
   conda update conda
   ```

   Confirm the update when prompted.

2. **Update All Packages in the Active Environment**:
   ```bash
   conda update --all
   ```
   This command upgrades all installed packages to their latest compatible versions.

---

## 8. Creating and Managing Environments

Beyond creating a single environment, you can manage multiple environments tailored to different projects.

- **List All Environments**:

  ```bash
  conda env list
  ```

  or

  ```bash
  conda info --envs
  ```

- **Remove an Environment**:
  Replace `myenv` with the name of the environment to delete:

  ```bash
  conda remove --name myenv --all
  ```

  This deletes the environment and all its packages.

- **Export an Environment to a YAML File**:

  ```bash
  conda env export --name myenv > environment.yml
  ```

  This file can be shared or used to recreate the environment on another system.

- **Recreate an Environment from a YAML File**:
  ```bash
  conda env create -f environment.yml
  ```

---

## 9. Installing Packages

With an active environment, install additional packages as needed:

1. **Install a Package Using Conda**:
   For example, to install NumPy:

   ```bash
   conda install numpy
   ```

   Conda will resolve dependencies and install the package.

2. **Install a Package Using pip**:
   If a package is not available via Conda, use pip:

   ```bash
   pip install package_name
   ```

   Ensure pip is installed in your environment.

3. **Search for Packages**:
   Use Conda's search functionality:
   ```bash
   conda search package_name
   ```

---

## 10. Uninstalling Miniconda

If you need to remove Miniconda from your system:

1. **Remove the Miniconda Installation Directory**:

   - On macOS/Linux:
     ```bash
     rm -rf /path/to/miniconda
     ```
     Replace `/path/to/miniconda` with your actual installation path.
   - On Windows, delete the Miniconda installation folder using File Explorer.

2. **Remove Conda from Environment Variables**:

   - Edit your shell configuration file (e.g., `.bashrc`, `.bash_profile`, `.zshrc`) or the system environment variables on Windows to remove any references to Miniconda.

3. **Delete Conda Configuration Files**:
   ```bash
   rm -rf ~/.condarc ~/.conda ~/.continuum
   ```
   This cleans up configuration files from your home directory.

---

## 11. Troubleshooting

### Common Issues

**Conda not recognized**:

```bash
source ~/.bashrc  # or restart shell
```

**Package conflicts**:

```bash
conda clean --all && conda update --all
```

**Environment corruption**:

```bash
conda remove --name bad_env --all
conda create --name fresh_env
```

---

## 12. Environment Configuration Files

- [`base-env.yml`](./environments/base-env.yml): Minimal Python environment
- [`data-science-env.yml`](./environments/data-science-env.yml): Includes NumPy, Pandas, Matplotlib

**To install data science stack**:

```bash
conda env create -f environments/data-science-env.yml
```

---

This guide covers all essential steps to install, verify, update, and manage Miniconda and its environments. Feel free to adjust or expand these instructions based on your specific needs.

> **Note**: Always verify environment specifications before installing from YAML files. For advanced configuration, see [Conda documentation](https://docs.conda.io/).
