
# 🧠 Git & GitHub Comprehensive Cheat Sheet (Full Advanced Edition)

## 📘 Overview
**Git** is a distributed version control system for tracking code changes.  
**GitHub** is a cloud-based hosting service for Git repositories, adding collaboration tools like pull requests, issues, and CI/CD.

---

## 🗂️ Common Git Terminology (Glossary)

| Term | Description |
|------|--------------|
| **Repository (Repo)** | Directory containing your project and its version history. |
| **Commit** | A snapshot of staged changes. |
| **Branch** | A parallel line of development. |
| **Merge** | Combines changes from one branch into another. |
| **Clone** | Copies a remote repository locally. |
| **Fork** | A personal copy of another GitHub repository. |
| **Pull Request (PR)** | Proposal to merge code changes. |
| **Remote** | Reference to a hosted repo (like GitHub). |
| **HEAD** | Points to the latest commit in current branch. |
| **Stash** | Temporarily saves uncommitted work. |
| **Tag** | Marks a specific commit. |
| **Rebase** | Moves commits to a new base for linear history. |
| **Cherry-Pick** | Applies a specific commit from another branch. |

---

## ⚙️ Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list
git help <command>
```

---

## 🏁 Repository Management

```bash
git init
git clone <url>
git remote -v
git remote add origin <url>
git fetch
git pull
git push
```

---

## 🌿 Branching & Merging

```bash
git branch
git branch <name>
git switch <name>
git checkout -b <name>
git merge <branch>
git branch -d <branch>
git merge --abort
```

---

## 🧱 Committing & Staging

```bash
git status
git add <file>
git add .
git commit -m "message"
git commit --amend
git reset <file>
```

---

## 🔍 History & Logs

```bash
git log
git log --oneline --graph
git show <commit>
git diff
git diff --staged
git blame <file>
```

---

## 🍒 Cherry-Pick & Rebase

```bash
git cherry-pick <commit>
git rebase <branch>
git rebase -i HEAD~3
git rebase --continue
```

---

## 💾 Stashing

```bash
git stash
git stash list
git stash pop
git stash apply stash@{2}
```

---

## 🧩 Tagging

```bash
git tag
git tag -a v1.0 -m "Release 1.0"
git push origin --tags
```

---

## 🔄 Undoing Changes

```bash
git checkout -- <file>
git reset --hard HEAD
git revert <commit>
```

---

# 🌐 GitHub CLI (gh) — Advanced Usage

The **GitHub CLI (`gh`)** integrates GitHub operations directly into your terminal.

### 🔐 `gh auth login`
Authenticate your CLI with GitHub:
```bash
gh auth login
```
Choose **GitHub.com** or **Enterprise**, and authenticate via **web browser** or **token**.

---

### 📂 `gh repo clone <user>/<repo>`
Clone a GitHub repository:
```bash
gh repo clone octocat/Hello-World
```

---

### 🪧 `gh issue create`
Create a new issue from terminal:
```bash
gh issue create --title "Bug: login fails" --body "Steps to reproduce..."
```

---

### 🔀 `gh pr create`
Create pull requests from CLI:
```bash
gh pr create --base main --head feature-login --title "Add login feature"
```

---

### 🧾 `gh pr status`
View PR status for current branch:
```bash
gh pr status
```

---

### Other Useful GitHub CLI Commands

| Command | Description |
|----------|-------------|
| `gh pr checkout <number>` | Checkout a pull request locally. |
| `gh pr merge <number>` | Merge PR (`--merge`, `--squash`, or `--rebase`). |
| `gh repo view` | View repo info or open in browser. |
| `gh gist create <file>` | Create GitHub Gist from a file. |

---

# 🧰 Advanced Git Tools — In-Depth

### 🧭 `git reflog`
Track every movement of HEAD. Recover lost commits or undo resets:
```bash
git reflog
```

---

### 🧩 `git bisect`
Find the commit that introduced a bug:
```bash
git bisect start
git bisect bad
git bisect good <commit>
git bisect reset
```

---

### 🧬 `git submodule`
Manage repositories within repositories:
```bash
git submodule add <repo_url> path/to/submodule
git submodule update --init --recursive
```

---

### 🧮 `git rev-list`
List all commit hashes:
```bash
git rev-list --all
```

---

### 🧱 `git gc`
Optimize and clean repository storage:
```bash
git gc --prune=now --aggressive
```

---

### 🧾 `git blame`
Show last modified commit for each line:
```bash
git blame <file>
```

---

# 🚀 Uploading an Existing Project to GitHub (First-Time Setup)

Follow these steps to push a local project folder to a **new GitHub repository** for the first time.

### 🪜 Step-by-Step Guide

1. **Initialize Git inside your project folder:**
   ```bash
   cd path/to/your/project
   git init
   ```

2. **Add your project files:**
   ```bash
   git add .
   ```

3. **Commit your changes:**
   ```bash
   git commit -m "Initial commit"
   ```

4. **Create a new repository on GitHub:**
   - Go to [https://github.com/new](https://github.com/new)
   - Name your repository (e.g., `my-project`)
   - Leave it **empty** (no README or .gitignore if already exists locally)

5. **Connect local repo to GitHub:**
   ```bash
   git remote add origin https://github.com/username/my-project.git
   ```

6. **Push to GitHub:**
   ```bash
   git push -u origin main
   ```
   *(If your branch is `master`, replace `main` with `master`)*

---

# 🔑 Using GitHub Personal Access Tokens (PAT)

GitHub **no longer supports password authentication** for HTTPS pushes and pulls.  
Instead, use **Personal Access Tokens (PATs)**.

### 🧩 How to Generate a Token

1. Go to **GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (Classic)**  
2. Click **Generate new token**  
3. Give it a **name** (e.g., “Windows Git Access”)  
4. Choose **repo**, **workflow**, and **read:org** scopes  
5. Copy the generated token (you won’t see it again)

---

### 🧠 How to Use the Token

When pushing for the first time:
```bash
git push origin main
```
Git will prompt for:
```
Username: your_github_username
Password: <paste_your_token_here>
```

To store credentials securely for future use:
```bash
git config --global credential.helper manager-core
```

This saves your token in Windows Credential Manager, so you don’t have to re-enter it.

---

# 💻 Maintaining Multiple Git Repositories with Different User IDs on Windows

You can maintain **separate Git identities** on the same machine using per-folder config or SSH keys.

### 🔹 Option 1: Per-Repository Git Configuration

Each repository can have its own user identity:

```bash
cd D:/Projects/work_repo
git config user.name "Work User"
git config user.email "work@example.com"

cd D:/Projects/personal_repo
git config user.name "Personal User"
git config user.email "personal@example.com"
```

---

### 🔹 Option 2: SSH Key-based Authentication

1. Generate separate SSH keys:
   ```bash
   ssh-keygen -t rsa -C "work@example.com" -f ~/.ssh/id_rsa_work
   ssh-keygen -t rsa -C "personal@example.com" -f ~/.ssh/id_rsa_personal
   ```

2. Add to SSH agent:
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa_work
   ssh-add ~/.ssh/id_rsa_personal
   ```

3. Configure `~/.ssh/config`:
   ```
   Host github-work
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa_work

   Host github-personal
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa_personal
   ```

4. Clone using host alias:
   ```bash
   git clone git@github-work:workuser/work-repo.git
   git clone git@github-personal:personaluser/personal-repo.git
   ```

---

### 🔹 Option 3: Credential Manager for HTTPS
```bash
git config credential.helper manager-core
```
Each repository will store separate credentials via Windows Credential Manager.

---

# ✅ Summary Table — Multi-Account Setup

| Method | Ideal For | Key Setup |
|--------|------------|-----------|
| **Per-Repo Config** | Same GitHub account, multiple repos | `.git/config` |
| **SSH Keys** | Multiple GitHub accounts | Separate SSH keys |
| **Credential Manager** | HTTPS-based auth | Windows Credential Store |

---

## 📚 Resources
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [GitHub CLI Manual](https://cli.github.com/manual/)
- [Pro Git Book](https://git-scm.com/book/en/v2)
