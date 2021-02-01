# Github Basics

## What Is Github

Git hosting service for projects that use Git

## How To Create Github Repository

### 1. Make Github Repo

[https://github.com/new](https://github.com/new)

### 2.1. Clone It

```bash
$ git clone <github-repo-link>
```

### 2.2. Associate Local Repo With The Github Repo

```bash
$ git remote add origin <github-repo-link>
```

### 3. Pull

Pull to get the latest changes from the Github repo.

```bash
$ git pull origin master
```

### 4. Push

Push the local repo codes to the remote Github repo.

```bash
$ git push -u origin master
```

The `-u` flag automatically sets origin as the remote (upstream) target for you. So, after this command, you can push with just `git push`

If you want to push a new branch,

```bash
$ git push origin <new-branch-name>
```
