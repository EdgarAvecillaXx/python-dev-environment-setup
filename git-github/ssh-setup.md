# SSH Setup for GitHub

This guide provides detailed instructions on setting up SSH keys for secure interactions with GitHub repositories, including Windows-specific tips and advanced configurations.

---

## Table of Contents

1. [Checking for Existing SSH Keys](#1-checking-for-existing-ssh-keys)
2. [Generating a New SSH Key](#2-generating-a-new-ssh-key)
3. [Adding the SSH Key to the SSH Agent](#3-adding-the-ssh-key-to-the-ssh-agent)
4. [Adding the SSH Key to Github](#4-adding-the-ssh-key-to-github)
5. [Testing Your SSH Connection](#5-testing-your-ssh-connection)
6. [Configuring SSH for Multiple Accounts](#6-configuring-ssh-for-multiple-accounts)
7. [Advanced SSH Agent Forwarding](#7-advanced-ssh-agent-forwarding)
8. [Troubleshooting Tips](#8-troubleshooting-tips)
   - [Common Issues](#common-issues)
   - [Permission Errors](#permission-errors)
   - [Revoking Compromised Keys](#revoking-compromised-keys)

---

## 1. Checking for Existing SSH Keys

Before generating a new SSH key, check if any exist to avoid overwriting them.

1. **Open Terminal**:

   - **macOS/Linux**: Use the default terminal.
   - **Windows**: Use **Git Bash** or **Windows Terminal** (recommended).

2. **List SSH Keys**:
   ```bash
   ls -al ~/.ssh
   ```
   Look for files like `id_rsa.pub`, `id_ecdsa.pub`, or `id_ed25519.pub`.

---

## 2. Generating a New SSH Key

If no SSH key exists, generate one:

1. **Generate Key Pair**:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   - Use `rsa` instead if your system doesn’t support Ed25519:
     ```bash
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     ```

2. **File Location & Passphrase**:
   - Press `Enter` to save to the default path (`~/.ssh/`).
   - Add a passphrase for extra security.

---

## 3. Adding the SSH Key to the ssh-agent

1. **Start the ssh-agent**:

   - **macOS/Linux**:
     ```bash
     eval "$(ssh-agent -s)"
     ```
   - **Windows** (PowerShell):
     ```powershell
     Start-Service ssh-agent
     ```

2. **Add Your Key**:
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```
   Replace `id_ed25519` if you used a custom filename.

---

## 4. Adding the SSH Key to GitHub

1. **Copy the Public Key**:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

   Copy the output starting with `ssh-ed25519`.

2. **Add Key to GitHub**:

   - Go to **Settings** → **SSH and GPG Keys** → **New SSH Key**.
   - Paste your key and save.

   _Tip_: Use the GitHub CLI for a faster workflow:

   ```bash
   gh auth login --ssh
   ```

---

## 5. Testing Your SSH Connection

Verify the setup:

```bash
ssh -T git@github.com
```

A success message will include your GitHub username.

---

## 6. Configuring SSH for Multiple Accounts

**Use Case**: Separate personal and work accounts.

1. **Generate Unique Keys**:

   - Example: `id_ed25519_personal` and `id_ed25519_work`.

2. **Edit `~/.ssh/config`**:

   ```bash
   Host github.com-personal
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_ed25519_personal

   Host github.com-work
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_ed25519_work
   ```

3. **Clone Repositories with Aliases**:
   ```bash
   git clone git@github.com-personal:username/repo.git
   ```

---

## 7. Advanced: SSH Agent Forwarding

Securely use local SSH keys on a remote server:

1. **Enable Forwarding**:

   ```bash
   ssh -A user@remote-server
   ```

   The `-A` flag forwards your SSH agent.

2. **Permanent Configuration**:
   Add this to `~/.ssh/config`:
   ```bash
   Host remote-server
     ForwardAgent yes
   ```

---

## 8. Troubleshooting Tips

### Permission Errors

Fix overly permissive SSH key/directory permissions:

```bash
chmod 600 ~/.ssh/id_ed25519*  # Sets keys to read/write for owner only
chmod 700 ~/.ssh              # Restricts directory access
```

### Common Issues

- **"Permission Denied (publickey)"**:

  - Ensure the key is added to `ssh-agent` and GitHub.
  - Specify the key explicitly:
    ```bash
    ssh -i ~/.ssh/id_ed25519 git@github.com
    ```

- **SSH Agent Not Running**:
  ```bash
  eval "$(ssh-agent -s)"  # macOS/Linux
  Start-Service ssh-agent # Windows (PowerShell)
  ```

### Revoking Compromised Keys

1. Go to **GitHub Settings** → **SSH and GPG Keys**.
2. Delete the compromised key.
3. Generate and add a new key using the steps above.

---

Your SSH setup is now secure and flexible enough for most workflows. For further details, visit [GitHub’s SSH Documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh). 🚀
