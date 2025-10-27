# 📜 Git Cheatsheet

A quick reference for working with git from the **terminal**. 
[Official Git Documentation](https://git-scm.com/doc)

---

## SETUP (Local)

```bash
  echo "# my-app" >> README.md                   # Create README.md (with simple content)
  git init                                       # Initialize a new repo
  git add README.md                              # Add new file (created README.md)
  git commit -m "first commit"                   # Commit changes/updates
  git branch -M main                             # Create master branch (i.e. main)
  git remote add origin https://github.com/<username>/<repo-name>.git           # Add repo remote origin
  git push -u origin main                        # (Initial push to main branch)
```

## BRANCHES

```bash
    git branch -a                                # List all branches
    git branch <branch-name>                     # Create a new branch

    git checkout <branch-name>                   # Switch branches
    git checkout -b <branch-name>                # Create and switch branch

    git merge <branch-name>                      # Merge another branch into current branch

    git branch -d <branch-name>                  # Delete a branch (locally)
    git push origin --delete <branch-name>       # Delete a branch (remotely)
```

---

## STAGE & COMMIT

```bash
    git status                                   # See current changes & staging area

    git add <file-path>                          # Add changes (specific file)
    git add .                                    # Add changes (all)

    git commit -m "Message"                      # Commit staged changes
    git commit -am "Message"                     # Add and commit tracked files (in one step)
    git commit                                   # Commit with long commit messages (opens editor)
    git log                                      # View commit history
```

## PUSH & PULL

```bash
    git push                                     # Push commits to remote
    git push origin <branch-name>                # Push specific branch

    git pull                                     # Fetch and merge from remote
```

---

## TAGS

- **Create**

```bash
  git tag <tagname>                              # Create a lightweight tag
  git tag -a <tagname> -m "message"              # Create an annotated tag (recommended)
  git tag -s <tagname> -m "message"              # Create a signed tag (GPG)
  git tag <tagname> <commit-hash>                # Tag a specific commit
```

- **View**

```bash
  git tag                                        # List all tags
  git tag -l "v1.*"                              # List tags matching a pattern
  git show <tagname>                             # Show details about a tag (commit info, message)
  git describe --tags                            # Show nearest tag reachable from current commit
  git describe --tags --abbrev=0                 # Show the most recent tag only
```

- **Edit/Move & Delete**

```bash
  git tag -f <tagname> <commit>                  # Force-move a tag to another commit
  git tag -a <tagname> -f -m "new msg"           # Recreate annotated tag with new message

  git tag -d <tagname>                           # Delete a local tag
  git push origin :refs/tags/<tagname>           # Delete a remote tag
```

- **Push & Fetch/Pull**

```bash
  git push origin <tagname>                      # Push a specific tag
  git push origin --tags                         # Push all tags

  git fetch --tags                               # Fetch all tags from remote
  git pull --tags                                # Pull and fetch tags
```

---

## CONFIGURATIONS

- **Remote Repo**

```bash
    git remote -v                                # List all remote URLs
    git remote add origin <repo-url>             # Add a new remote
    git remote set-url origin <new-url>          # Change remote URLs
    git remote remove origin                     # Remove remote URLs

    git clone <repo-url>                         # Clone an existing repo
```

- **User Config**

```bash
    git config --list                                      # List current config
    git config --global user.name "Your Name"              # Set username
    git config --global user.email "you@example.com"       # Set email
```

---

## UNDO CHANGES

- **Commits**

```bash
  # Working Directory (Unstaged changes)

  git restore <file>                # Restore file from last commit (Discard local file edits)
  git restore .                     # Restore all modified files (Discard local file edits)
```

```bash
  # Staging Area (Staged but not committed)

  git diff --staged                 # See what's staged
  git restore --staged <file>       # Unstage a single file (keep changes in working dir)
  git restore --staged .            # Unstage everything (keep changes in working dir)
```

```bash
  git reset --soft HEAD~1           # Undo the last commit, keep changes
  git reset HEAD~1                  # Undo the last commit, unstage but keep changes
  git reset --hard HEAD~1           # Completely undo the last commit and its changes, ⚠️ Destructive: wipes permanently.
```

```bash
  git revert <commit-hash>          # Creates a new commit that undoes the specified one, safe for shared branches.

  # Undo multiple commits safely
  git revert --no-commit <old>..<new>
  git commit -m "Revert range of commits"

  git commit --amend                # Amend the last commit
```

- **Selective Undo**

```bash
  git restore --source=<commit> <file>      # See all HEAD history (even deleted commits)
  git rm --cached <file>                    # Untrack a file (stop Git tracking it)
```

- **Reflog**

```bash
  git reflog                                # See all HEAD history (even deleted commits)
  git reset --hard <reflog-id>              # Recover from catastrophe
```
