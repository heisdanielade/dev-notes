# 📜 Git Cheat Sheet

A quick reference for working with git from the **terminal**.

---

## Repository Setup

- **Create README.md (with simple content):**

```bash
  echo "# nofwergw" >> README.md
```

- **Initialize a new repo:**

```bash
  git init
```

- **Add new file (created README.md):**

```bash
  git add README.md
```

- **Commit changes/updates:**

```bash
  git commit -m "first commit"
```

- **Create master branch (i.e. main):**

```bash
  git branch -M main
```

- **Add repo remote origin:**

```bash
  git remote add origin https://github.com/<username>/<repo-name>.git
```

- **Initial push to main branch:**

```bash
  git push -u origin main
```

## Branching

- **See all branches**:

```bash
    git branch -a
```

- **Create a new branch**:

```bash
    git branch <branch-name>
```

- **Switch branches**:

```bash
    git checkout <branch-name>
```

- **Create and switch branch**:

```bash
    git checkout -b <branch-name>
```

- **Merge another branch into current branch**:

```bash
    git merge <branch-name>
```

- **Delete a branch (locally)**:

```bash
    git branch -d <branch-name>

```

- **Delete a branch (remotely)**:

```bash
    git push origin --delete <branch-name>
```

## Remote

- **See all remote URLs**:

```bash
    git remote -v
```

- **Add a new remote**:

```bash
    git remote add origin <repo-url>
```

- **Change remote URLs**:

```bash
    git remote set-url origin <new-url>
```

- **Remove remote URLs**:

```bash
    git remote remove origin
```

## Configurations

- **List current config**:

```bash
    git config --list
```

- **Set username**:

```bash
    git config --global user.name "Your Name"

```

- **Set email**:

```bash
    git config --global user.email "you@exaample.com"

```

- **Initialize a new repo**:

```bash
    git init
```

- **Clone a git remote repo**:

```bash
    git clone <repo-url>
```

## Status & Staging

- **See current changes & staging area**:

```bash
    git status
```

- **Add changes (specific file)**:

```bash
    git add <file-path>
```

- **Add changes (all)**:

```bash
    git add .
```

## Commiting

- **Commit staged changes**:

```bash
    git commit -m "Message"
```

- **Add and commit tracked files (in one step)**:

```bash
    git commit -am "Message"
```

- **Commit with long commit messages (opens editor)**:

```bash
    git commit
```

- **View commit history**:

```bash
    git log
```

## Pushing & Pulling

- **Push commits to remote**:

```bash
    git push
```

- **Push specific branch**:

```bash
    git push origin <branch-name>
```

- **Fetch and merge from remote**:

```bash
    git pull
```

## Undoing changes

- **Undo changes in workout directory**:

```bash
git checkout -- <file-name>
```

- **Unstage a file**:

```bash
git reset <file-name>
```

- **Reset to specific commit (CAREFUL!)**:

```bash
git reset --hard <commit>
```

---

[Official Git Documentation](https://git-scm.com/doc)
