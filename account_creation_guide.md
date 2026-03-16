# GitHub CLI Setup Guide

This guide walks you through installing and configuring the GitHub CLI (`gh`) on your laptop.  
Run these steps **after** you have created your GitHub account.

---

## What is the GitHub CLI?

The GitHub CLI (`gh`) is an official command-line tool from GitHub.  
It lets you authenticate, clone repos, create pull requests, and manage your account — all from the terminal.

---

## Mac / Linux

### Step 1 — Install the GitHub CLI

**Mac (using Homebrew):**

```bash
brew install gh
```

If you do not have Homebrew installed, install it first:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Linux (Debian / Ubuntu):**

```bash
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
&& sudo mkdir -p -m 755 /etc/apt/keyrings \
&& out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
&& cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

**Linux (Fedora / RHEL / CentOS):**

```bash
sudo dnf install gh
```

### Step 2 — Verify the installation

```bash
gh --version
```

You should see output similar to:

```
gh version 2.x.x (2024-xx-xx)
```

### Step 3 — Log in to GitHub

```bash
gh auth login
```

Follow the prompts:

1. Select `GitHub.com`
2. Select `HTTPS` as the preferred protocol
3. Select `Login with a web browser`
4. Copy the one-time code shown in the terminal
5. Press Enter — your browser will open
6. Paste the code on the GitHub device activation page
7. Click **Authorize GitHub CLI**

Back in the terminal you should see:

```
Logged in as your-username
```

### Step 4 — Configure Git identity

Set your name and email so your commits are correctly attributed:

```bash
git config --global user.name "Your Full Name"
git config --global user.email "you@example.com"
```

Verify:

```bash
git config --global --list
```

### Step 5 — Clone the workshop repository

```bash
gh repo clone [instructor-username]/task-manager
cd task-manager
python main.py
```

---

## Windows

### Step 1 — Install the GitHub CLI

**Option A — Windows Package Manager (recommended):**

Open **Command Prompt** or **PowerShell** as Administrator and run:

```powershell
winget install --id GitHub.cli
```

**Option B — Manual installer:**

1. Go to [https://cli.github.com](https://cli.github.com)
2. Click **Download for Windows**
3. Run the `.msi` installer
4. Accept the defaults and click through to finish

### Step 2 — Restart your terminal

Close and reopen **Command Prompt** or **PowerShell** so the new `gh` command is available.

### Step 3 — Verify the installation

```powershell
gh --version
```

You should see output similar to:

```
gh version 2.x.x (2024-xx-xx)
```

### Step 4 — Log in to GitHub

```powershell
gh auth login
```

Follow the prompts:

1. Select `GitHub.com`
2. Select `HTTPS` as the preferred protocol
3. Select `Login with a web browser`
4. Copy the one-time code shown in the terminal
5. Press Enter — your browser will open
6. Paste the code on the GitHub device activation page
7. Click **Authorize GitHub CLI**

Back in the terminal you should see:

```
Logged in as your-username
```

### Step 5 — Configure Git identity

```powershell
git config --global user.name "Your Full Name"
git config --global user.email "you@example.com"
```

Verify:

```powershell
git config --global --list
```

> **Note:** If `git` is not recognised, download Git for Windows from [https://git-scm.com](https://git-scm.com) and install it first. The installer includes Git Bash and integrates with Command Prompt and PowerShell.

### Step 6 — Clone the workshop repository

```powershell
gh repo clone [instructor-username]/task-manager
cd task-manager
python main.py
```

---

## Troubleshooting

| Problem                                      | Solution                                                               |
| -------------------------------------------- | ---------------------------------------------------------------------- |
| `gh: command not found`                      | Close and reopen your terminal after installation                      |
| `git: command not found` on Windows          | Install Git for Windows from git-scm.com                               |
| Browser does not open during `gh auth login` | Copy the URL from the terminal and paste it manually into your browser |
| Authentication fails                         | Run `gh auth logout` and then `gh auth login` again                    |
| `git config` name/email not saving           | Make sure you include the `--global` flag                              |

---

## Quick Reference — Commands Used Today

| Command                                | What it does                          |
| -------------------------------------- | ------------------------------------- |
| `gh auth login`                        | Authenticate with your GitHub account |
| `gh auth status`                       | Check if you are logged in            |
| `gh repo clone user/repo`              | Clone a repository using the CLI      |
| `git config --global user.name "..."`  | Set your commit display name          |
| `git config --global user.email "..."` | Set your commit email                 |
| `git status`                           | See what has changed                  |
| `git add .`                            | Stage all changes                     |
| `git commit -m "message"`              | Save a snapshot                       |
| `git push`                             | Upload to GitHub                      |

---

## Next Step

Once you are logged in and have cloned the repository, open `main.py` in your editor and follow the workshop activity in the slides.
