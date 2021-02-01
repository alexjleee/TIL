# Git Basics

## What Is Git?

Git stores data as a stream of **snapshots** (of what the project files look like at the moment). It enables us to record the changes in the project and go back to a specific version.
Git is a **Distributed** Version Control System, which means each developer can have a working copy and the full change history locally.

## How To Use Git

### 1. Setup

```bash
$ git --version
$ git config --global user.name <user-name>
$ git config --global user.email <user-email>
```

### 2. Create Repository

A repository contains all the project files and revision history.

```bash
$ mkdir new-project
$ cd new-project
$ git init
```

### 3. Commit

1. Check the status (untracked, modified, staged)

```bash
$ git status
```

2. Stage files

```bash
$ git add <file-name>
```

3. Make commits

```bash
$ git commit -m "commit message"
```

- How to write commit message
  - Don't end your commit message with a period
  - Keep the message concise (less than 50 characters)
  - Use active voice ('add' instead of 'added')
    To check the commit history
  - Make it explicit

```bash
$ git log
```

To go back to the previous commit

```bash
$ git checkout <commit-hash>
```

To go back to the latest commit

```bash
$ git checkout master
```

### 4. Branch & Merge

Git branches allow us to have divergent project history.

1. Create a branch

```bash
$ git branch <new-branch-name>
```

2. Switch to a different branch

```bash
$ git checkout <branch-name>
```

3. Create & Switch to a new branch at the same time

```bash
$ git checkout -b <new-branch-name>
```

4. To go back to the master

```bash
$ git checkout master
```

5. Merge a branch into the current branch

```bash
$ git merge <branch-name>
```

6. To delete a branch

```bash
$ git branch -d <branch-name>
```
