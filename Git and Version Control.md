> Understand how to track code changes, manage project history, collaborate with developers, and maintain reliable software projects using Git.

## 1. Introduction

Version Control is a system that tracks changes made to files over time.

It allows developers to:

- Track modifications.
    
- Restore previous versions.
    
- Compare changes.
    
- Collaborate with other developers.
    
- Maintain project history.
    
- Manage different development branches.
    

**Git** is a widely used distributed version control system.

It is commonly used in software development, cybersecurity projects, automation scripts, and open-source collaboration.

## 2. What Is Git?

Git is a distributed version control system created by Linus Torvalds in 2005.

Unlike centralized version control systems, Git allows each developer to maintain a local copy of the repository and its history.

Git can work without an internet connection.

Example:

```
Project/
│
├── main.py
├── README.md
└── config.json
```

Git can track changes to these files and record snapshots called commits.

## 3. What Is Version Control?

Version Control helps maintain different versions of a project.

Without version control:

- Old files may be overwritten.
    
- Changes can be difficult to track.
    
- Collaboration becomes complicated.
    
- Recovering previous work may be difficult.
    

With version control:

- Changes are recorded.
    
- Previous versions can be restored.
    
- Developers can work independently.
    
- Project history is maintained.
    

## 4. Types of Version Control Systems

### 4.1 Local Version Control

Changes are tracked on a single computer.

### 4.2 Centralized Version Control

A central server maintains the main repository.

Developers access and update the shared repository.

### 4.3 Distributed Version Control

Each developer maintains a local repository containing project history.

Git is a distributed version control system.

## 5. Git Architecture

Git uses three important areas:

1. Working Directory
    
2. Staging Area
    
3. Repository
    

### Working Directory

The working directory contains the project files you edit.

### Staging Area

The staging area contains changes selected for the next commit.

### Repository

The repository stores committed snapshots and project history.

### Basic Workflow

```
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Local Repository
       |
       | git push
       v
Remote Repository
```

## 6. Git vs GitHub

Git and GitHub are not the same thing.

|Git|GitHub|
|---|---|
|Version control system|Hosting and collaboration platform|
|Installed locally|Accessed through a website or Git tools|
|Tracks project history|Hosts remote Git repositories|
|Works offline|Requires connectivity for remote operations|
|Created by Linus Torvalds|Operated by GitHub|

Other Git hosting platforms include GitLab and Bitbucket.

## 7. Installing Git

Download Git from:

[https://git-scm.com/](https://git-scm.com/)

Verify installation:

```
git --version
```

Example output:

```
git version 2.x.x
```

The exact version depends on the installed release.

## 8. Initial Git Configuration

Configure your Git identity:

```
git config --global user.name "Your Name"
```

```
git config --global user.email "you@example.com"
```

Check configuration:

```
git config --global --list
```

These values are recorded in commit metadata.

Use an email address appropriate for your Git hosting account if you want your commits associated with that account.

## 9. Creating a Git Repository

Navigate to your project directory:

```
cd my-project
```

Initialize Git:

```
git init
```

Git creates a hidden `.git` directory containing repository metadata.

Check repository status:

```
git status
```

## 10. Basic Git Commands

|Command|Purpose|
|---|---|
|`git init`|Initialize a repository|
|`git status`|Show repository status|
|`git add`|Stage changes|
|`git commit`|Record staged changes|
|`git log`|Display commit history|
|`git diff`|Compare changes|
|`git restore`|Restore working-tree files|
|`git rm`|Remove tracked files|
|`git mv`|Rename or move tracked files|

### 10.1 Git Add

Stage a specific file:

```
git add main.py
```

Stage all changes in the current directory and its subdirectories:

```
git add .
```

### 10.2 Git Commit

Create a commit:

```
git commit -m "Initial project setup"
```

A commit records the staged changes with a message.

### 10.3 Git Log

View commit history:

```
git log
```

Compact history:

```
git log --oneline
```

### 10.4 Git Diff

View unstaged changes:

```
git diff
```

View staged changes:

```
git diff --staged
```

## 11. Git Branching

A branch is an independent line of development.

Branches allow developers to work on features or fixes without immediately changing the main development branch.

Example:

```
          feature
         /
main ---●---●---●
```

Common commands:

Create a branch:

```
git branch feature-login
```

List branches:

```
git branch
```

Switch branches:

```
git switch feature-login
```

Create and switch to a branch:

```
git switch -c feature-login
```

Merge a branch:

```
git switch main
git merge feature-login
```

The default branch may be named `main`, but repositories can use other names.

## 12. Git Merge

Merging combines changes from one branch into another.

Example:

```
git switch main
git merge feature-login
```

Git attempts to integrate the changes.

If conflicting changes cannot be automatically combined, Git reports a merge conflict.

## 13. Merge Conflicts

A merge conflict occurs when Git cannot automatically reconcile changes.

Example conflict:

```
<<<<<<< HEAD
print("Hello")
=======
print("Welcome")
>>>>>>> feature-login
```

The markers indicate conflicting versions.

To resolve the conflict:

1. Open the affected file.
    
2. Decide which changes to keep.
    
3. Edit the file and remove conflict markers.
    
4. Stage the resolved file.
    
5. Complete the merge commit if Git requires it.
    

```
git add main.py
git commit
```

Do not leave conflict markers in the final source code.

## 14. Remote Repositories

A remote repository is another copy of a Git repository hosted elsewhere.

For example, a project may be hosted on GitHub.

Add a remote:

```
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

View remotes:

```
git remote -v
```

Push commits:

```
git push -u origin main
```

The `-u` option sets the upstream branch for future pushes.

## 15. Git Pull and Git Fetch

### Git Fetch

Downloads remote updates without automatically integrating them into the current branch.

```
git fetch origin
```

### Git Pull

Fetches remote changes and integrates them into the current branch.

```
git pull
```

The integration behavior depends on Git configuration and command options.

## 16. Git Clone

Git Clone creates a local copy of an existing remote repository.

Example:

```
git clone https://github.com/USERNAME/REPOSITORY.git
```

It downloads the repository and its available history.

## 17. .gitignore

`.gitignore` specifies intentionally untracked files that Git should ignore.

Create a file named:

```
.gitignore
```

Example:

```
# Python cache
__pycache__/
*.pyc

# Virtual environments
venv/
.env/

# Secrets
.env
*.key
*.pem

# Editor settings
.vscode/

# Temporary files
*.log
```

Important: `.gitignore` does not automatically remove files that are already tracked by Git.

If a sensitive file has already been committed, ignoring it is not enough. Remove it from tracking, rotate exposed credentials, and consider whether repository history needs remediation.

## 18. Git Tags

Tags identify specific points in repository history.

They are often used to mark software releases.

Create a tag:

```
git tag v1.0.0
```

List tags:

```
git tag
```

Push a tag:

```
git push origin v1.0.0
```

## 19. Git Revert and Reset

These commands handle changes to repository history in different ways.

### Git Revert

Creates a new commit that reverses the changes introduced by an earlier commit.

```
git revert COMMIT_ID
```

This is generally safer for reversing changes already shared with others.

### Git Reset

Moves the current branch reference to another commit and can change the staging area and working directory depending on the option.

```
git reset --soft HEAD~1
```

Moves the branch back one commit while keeping changes staged.

```
git reset --mixed HEAD~1
```

Moves the branch back one commit and unstages the changes while keeping the working-tree files.

```
git reset --hard HEAD~1
```

Moves the branch back one commit and discards corresponding staged and working-tree changes.

**Warning:** `--hard` can permanently discard uncommitted work. Understand the consequences before using it.

Avoid rewriting shared history unless the team has agreed to do so.

## 20. GitHub Workflow

A common workflow for publishing a project is:

1. Create a repository on GitHub.
    
2. Initialize Git locally.
    
3. Add project files.
    
4. Create a commit.
    
5. Connect the local repository to GitHub.
    
6. Push the commit.
    

Example:

```
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

Replace `USERNAME` and `REPOSITORY` with the actual GitHub account and repository details.

If the local repository already has a remote, do not add the same remote again.

## 21. Git Security Best Practices

Git repositories can contain sensitive information.

Follow these practices:

- Never commit passwords or API keys.
    
- Use `.gitignore` for local secrets and temporary files.
    
- Review staged changes before committing.
    
- Use appropriate repository permissions.
    
- Enable multi-factor authentication on Git hosting accounts.
    
- Review third-party code before using it.
    
- Protect important branches.
    
- Use code review for sensitive changes.
    
- Avoid committing private certificates and credentials.
    
- Rotate credentials if they are accidentally exposed.
    

### Inspect Changes Before Committing

```
git status
git diff
git diff --staged
```

These commands help identify unintended changes before a commit.

## 22. Git in Cybersecurity

Git is useful in cybersecurity because it helps maintain and audit security-related projects.

Examples include:

### 1. Security Scripts

Track changes to Python automation and analysis tools.

### 2. Configuration Management

Maintain versions of configuration files and infrastructure code.

### 3. Security Research

Document experiments and track research scripts.

### 4. Detection Rules

Maintain changes to SIEM detection rules and security signatures.

### 5. Collaborative Development

Allow multiple security researchers to contribute to tools and documentation.

### 6. Incident Documentation

Track changes to incident-response scripts and investigation documentation.

## 23. Practical Lab

**Objective:** Create a local Git repository and publish a project to GitHub.

### Lab A — Create a Project

```
mkdir git-lab
cd git-lab
```

Create a file named `main.py`:

```
print("ROOTLOG Git Lab")
print("Learning version control")
```

### Lab B — Initialize Git

```
git init
git status
```

Observe the repository status.

### Lab C — Stage and Commit

```
git add main.py
git status
git commit -m "Add initial Python file"
```

### Lab D — Modify the File

Add another line to `main.py`:

```
print("Version control is useful")
```

Inspect the change:

```
git diff
```

Stage and commit:

```
git add main.py
git commit -m "Update Python file"
```

### Lab E — View History

```
git log --oneline
```

Identify the two commits.

### Lab F — Create a Branch

```
git switch -c feature-message
```

Modify `main.py` and commit the change.

Then return to the main branch:

```
git switch main
```

Merge the feature branch:

```
git merge feature-message
```

### Lab G — Create a .gitignore File

Create `.gitignore`:

```
*.log
.env
__pycache__/
```

Stage and commit it:

```
git add .gitignore
git commit -m "Add gitignore"
```

### Lab H — Publish to GitHub

Create an empty repository on GitHub, then connect your local repository.

```
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

Use your actual repository URL.

## 24. Key Takeaways

- Version Control tracks changes to files over time.
    
- Git is a distributed version control system.
    
- GitHub hosts Git repositories and provides collaboration tools.
    
- The working directory, staging area, and repository are important Git concepts.
    
- Commits record project changes.
    
- Branches support independent development.
    
- Merging combines changes.
    
- Remote repositories support collaboration and backup.
    
- `.gitignore` excludes selected untracked files.
    
- Git security practices help prevent accidental exposure of sensitive information.
    

## 25. Related Topics

- [[Introduction to Programming]]
    
- [[Algorithms]]
    
- [[Python Programming]]
    
- [[Python Modules]]
    
- [[JSON]]
    
- [[APIs and HTTP Requests]]
    
- [[Secure Coding]]
    
- [[Secrets Management]]
    
- [[Practical Labs]]
    
- [[Research Papers]]