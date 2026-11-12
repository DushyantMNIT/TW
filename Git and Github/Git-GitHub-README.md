# Git & GitHub Version Control — Technical Reference & Mini-Project Guide

A comprehensive, command-line focused reference manual for **Git** and **GitHub**, featuring essential version control workflows, command syntax, branching strategies, pull requests, and a complete step-by-step calculator mini-project.

---

## 1. Introduction to Version Control Systems

A **Version Control System (VCS)** records modifications made to software source code or documentation over time. It allows developers to track change history, identify author contributions, revert faulty code, and collaborate in parallel without overwriting work.

### 1.1 Types of Version Control
1. **Local VCS**: Tracks file versions on a single computer using a local database.
2. **Centralized VCS (CVCS)**: A single server stores the entire project history (e.g., Subversion/SVN). If the central server fails, offline work and recovery become difficult.
3. **Distributed VCS (DVCS)**: Every contributor clones a full copy of the repository history (e.g., **Git**). Local work, committing, and branching occur offline without requiring network connectivity.

### 1.2 Git vs. GitHub Distinction

| Dimension | Git | GitHub |
| :--- | :--- | :--- |
| **Category** | Distributed Version Control CLI tool | Web-based hosting & collaboration platform |
| **Execution** | Runs locally on your machine | Hosted on cloud servers |
| **Primary Purpose** | Tracks file changes via commit history | Hosts repositories, facilitates code reviews & PRs |
| **Network Need** | Completely offline for local actions | Requires internet for syncing & web features |

---

## 2. Git Architecture & The Three Local Areas

Git manages code across three local zones plus remote hosting:

- **Working Directory**: Where project files are edited.
- **Staging Area**: Where changes are selected using `git add`.
- **Local Repository**: Where committed snapshots are stored via `git commit`.
- **Remote Repository**: Shared repository hosted on a platform like GitHub.

---

## 3. Essential Command-Line Reference

### 3.1 Initial Setup & Configuration
```bash
# Set global commit author identity
git config --global user.name "Student Name"
git config --global user.email "student@example.com"

# Verify configuration settings
git config --global --list
```

### 3.2 Repository Initialization & Daily Workflow
```bash
# Initialize a new local Git repository inside current directory
git init

# Check state of working directory and staging area
git status

# Stage a specific file
git add main.py

# Stage all modified and new files in the current directory
git add .

# Record staged snapshot into local repository history
git commit -m "Add initial calculator program"

# Display compact commit history (one line per commit)
git log --oneline

# Display full commit history details
git log
```

### 3.3 Inspection, Differences, and Reversion
```bash
# Compare unstaged changes in working directory against staging area
git diff

# Compare staged changes ready for commit against last commit
git diff --staged

# List all files currently tracked by Git
git ls-files

# Discard unstaged changes in a file (restore to HEAD state)
git restore main.py

# Safely undo a specific past commit by creating a new inverse commit
git revert COMMIT_ID
```

### 3.4 Branching, Merging, and Conflict Resolution
```bash
# List all local branches (current branch marked with *)
git branch

# Create a new branch named feature-subtraction
git branch feature-subtraction

# Switch to an existing branch
git switch feature-subtraction

# Create and switch to a new branch in a single command
git switch -c feature-subtraction

# Merge changes from feature-subtraction into current branch (e.g., main)
git switch main
git merge feature-subtraction
```

#### Resolving Merge Conflicts
When Git cannot automatically merge conflicting changes, it inserts conflict markers into the affected files:

```
<<<<<<< HEAD
result = 10
=======
result = 20
>>>>>>> feature-subtraction
```

**Resolution Steps**:
1. Open the file and edit it to retain the desired code.
2. Remove the conflict markers.
3. Stage the resolved file: `git add main.py`.
4. Finalize the merge commit: `git commit -m "Resolve merge conflict in main.py"`.

### 3.5 Remote Repositories & Collaboration
```bash
# Connect local repository to a remote GitHub URL
git remote add origin REPOSITORY_URL

# Verify configured remotes
git remote -v

# Rename default branch to main and push initial commits
git branch -M main
git push -u origin main

# Clone an existing GitHub repository to your local machine
git clone REPOSITORY_URL

# Fetch latest remote refs without merging into working branch
git fetch origin

# Fetch and merge remote changes into current branch
git pull origin main
```

---

## 4. Hands-on Mini-Project: Version-Controlled Calculator

Follow this exact terminal walkthrough to create, commit, branch, and push a Python calculator repository.

### Step 1: Initialize Local Repository and Create Initial Code
Open terminal and execute:

```bash
# Create project directory and enter it
mkdir calculator
cd calculator

# Initialize Git
git init
```

Create `main.py` containing the following Python code:

```python
print("Calculator")
a = 10
b = 5
print("Sum:", a + b)
```

### Step 2: Record the First Commit
```bash
# Inspect status
git status

# Stage the file
git add main.py

# Commit staged file
git commit -m "Add initial calculator program"

# Inspect commit log
git log --oneline
```

### Step 3: Link and Push to GitHub
Create an empty repository named `calculator` on GitHub, then run:

```bash
# Ensure branch is named main
git branch -M main

# Add your GitHub repository remote
git remote add origin REPOSITORY_URL

# Push local commits to remote main branch
git push -u origin main
```

### Step 4: Implement a Subtraction Feature via Branching
```bash
# Create and switch to a feature branch
git switch -c feature-subtraction
```

Update `main.py` to add the subtraction operation:

```python
print("Calculator")
a = 10
b = 5
print("Sum:", a + b)
print("Difference:", a - b)
```

Stage, commit, and push the feature branch:

```bash
git add main.py
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction
```

### Step 5: Open & Merge a Pull Request (PR) on GitHub
1. Open repository page on GitHub.
2. Click **Compare & pull request** next to `feature-subtraction`.
3. Set base `main` and compare `feature-subtraction`.
4. Title the PR: `Add subtraction feature to calculator`.
5. Click **Create Pull Request**, review, and click **Merge Pull Request**.

### Step 6: Sync Local Main Branch
Return to terminal and pull the merged changes back into your local main branch:

```bash
# Switch to main branch
git switch main

# Pull updated main branch from GitHub
git pull origin main
```

---

## 5. Summary of Best Practices

1. **Logical Commits**: Make frequent, self-contained commits focused on single logical changes.
2. **Clear Commit Messages**: Use imperative summary messages (e.g., `Add input validation`).
3. **Branch Isolation**: Never commit unreviewed code directly to `main`; always use feature branches.
4. **Clean Workspace**: Use `.gitignore` to keep binary builds and temporary files out of repository history.

---
*Git & GitHub Technical Guide — Prepared for Technical Writing Course (MNIT Jaipur).*
