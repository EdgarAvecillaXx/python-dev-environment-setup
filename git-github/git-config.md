# Git & GitHub Configuration

This document explains how to configure Git locally and connect it with GitHub for version control.

## 1. Installing Git
- **Download Git**: Visit the [official Git website](https://git-scm.com/downloads) and download the installer for your operating system.
- **Installation**: Follow the installation instructions. On Windows, you may choose the default options unless you need specific configurations.

## 2. Verifying Git Installation
After installation, verify that Git is installed correctly by checking its version:
```bash
git --version
```
This command displays the installed Git version, confirming that Git is ready for use.

## 3. Configuring User Information
Set your global username and email to ensure your commits are correctly attributed:

```bash
git config --global user.name "Your name"
git config --global user.email "your_email@example.com"
```
The `--global` flag applies this configuration for all repositories on your system. These settings are stored in the `~/.gitconfig` file.

To verify your settings:

```bash
git config --global --list
```
This command lists all global configurations, allowing you to confirm your user information.

## 4. Additional Git configuration
Consider configuring the following for an optimized experience:
- **Default editor**: Set your preferred text editor for Git. For example, to set Visual Studio Code as your default editor:
  ```bash
  git config --global core.editor "code --wait"
  ```
- **Color UI**: Enable colored output for better readability:
  ```bash
  git config --global color.ui auto
  ```
- **Default Branch Name**: Set the default branch name for new repositories to `main` (available in Git 2.28 and later):
  ```bash
  git config --global init.defaultBranch main
  ```
  This configuration ensures that new repositories use `main` as the default branch name.
- **Pull Behavior**: Configure the behavior of `git pull` to merge (default) or rebase:
  - To set pull to merge (default behavior):
    ```bash
    git config --global pull.rebase false
    ```
  - To set pull rebase:
    ```bash
    git config --global pull.rebase true
    ```
    Setting `pull.rebase` to `true` makes `git pull` use rebase instead of merge, which can result in a cleaner project history.

For more advanced configurations, consult the [Git documentation](https://git-scm.com/doc).

---
For further details on Git commands and workflows, refer to the [Git Book](https://git-scm.com/book/en/v2).

