# The Complete Git Guide

## 1. What is Git?

Git is a distributed version control system (DVCS) used to track changes in source code during software development. It allows multiple developers to work on the same project simultaneously without overwriting each other's work, and it keeps a full history of every change made to a project.

**Key characteristics:**

- Tracks changes to files over time
- Allows reverting to previous versions
- Enables branching and merging
- Works offline (local repository has full history)
- Supports collaboration across distributed teams

---

## 2. History and Founder

- Git was created by **Linus Torvalds** (also the creator of the Linux kernel) in **2005**.
- It was built because the Linux kernel development team needed a fast, distributed system after they lost access to their previous tool, BitKeeper.
- Git was designed with three goals in mind: speed, simplicity, and strong support for non-linear development (many branches running in parallel).
- The name "Git" is British slang for an unpleasant person — Torvalds jokingly named it after himself, saying "I'm an egotistical bastard, so I name all my projects after myself."

---



## 3. Centralized vs Distributed Version Control



### Centralized Version Control System (CVCS)

- A single central server stores all versioned files.
- Developers "check out" files from that central server.
- Examples: SVN (Subversion), CVS, Perforce.

**Drawbacks:**

- Single point of failure — if the server goes down, no one can collaborate or see history.
- Requires network access for most operations.
- Slower for operations like viewing history or committing.



### Distributed Version Control System (DVCS)

- Every developer has a **full copy** of the repository, including its entire history, on their local machine.
- Examples: Git, Mercurial.

**Advantages:**

- No single point of failure.
- Most operations (commit, diff, log, branch) are local and fast.
- Enables offline work.
- Multiple backups exist automatically (every clone is a backup).


| Feature           | Centralized (SVN)       | Distributed (Git)          |
| ----------------- | ----------------------- | -------------------------- |
| Repository copies | One (server)            | Full copy on every machine |
| Offline work      | Limited                 | Fully supported            |
| Speed             | Network-dependent       | Mostly local, fast         |
| Branching         | Heavy/slow              | Lightweight/fast           |
| Failure risk      | Single point of failure | No single point of failure |


---



## 4. Git vs GitHub

This is one of the most commonly confused topics.


| Git                                    | GitHub                                                                        |
| -------------------------------------- | ----------------------------------------------------------------------------- |
| A version control **tool/software**    | A **hosting platform/service** for Git repositories                           |
| Installed and run locally              | Accessed via the web (and APIs)                                               |
| Created by Linus Torvalds (2005)       | Created by Tom Preston-Werner, Chris Wanstrath, PJ Hyett, Scott Chacon (2008) |
| Works without internet                 | Requires internet to access hosted repos                                      |
| No concept of "pull requests" natively | Adds pull requests, issues, actions, project boards                           |
| Open source                            | Owned by Microsoft (acquired 2018)                                            |


**Analogy:** Git is like the engine of a car (the version control mechanism). GitHub is like a car showroom/parking service (a place to store, share, and showcase repositories built with that engine). Other GitHub alternatives include **GitLab** and **Bitbucket**.

---



## 5. Core Git Concepts



### Repository (Repo)

A folder tracked by Git, containing all files plus a hidden `.git` folder storing history and configuration.

### Working Directory

The actual files on your filesystem that you edit.

### Staging Area (Index)

A middle zone where changes are placed before being committed. Lets you choose exactly what goes into the next commit.

### Commit

A snapshot of your staged changes, saved permanently in the repository's history with a unique hash ID, author, timestamp, and message.

### Branch

An independent line of development. The default branch is usually called `main` (previously `master`).

### HEAD

A pointer to the current branch/commit you're working on.

### Remote

A version of your repository hosted elsewhere (e.g., on GitHub), typically named `origin`.

### Clone

A full local copy of a remote repository, including all history.

### Merge

Combining changes from one branch into another.

### Rebase

Reapplying commits from one branch on top of another, creating a linear history.

### Conflict

Occurs when Git cannot automatically reconcile changes made in two different places to the same lines of a file.

---



## 6. The Three States / Areas in Git

```
Working Directory  --->  Staging Area  --->  Repository (.git)
     (edit)              (git add)           (git commit)
```

1. **Modified** — file changed but not staged.
2. **Staged** — file marked to go into the next commit.
3. **Committed** — file safely stored in the local repository history.

---



## 7. Essential Git Commands (Cheat Sheet)



### Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git init                     # initialize a new repo
git clone <url>               # clone an existing repo
```



### Basic Workflow

```bash
git status                    # check current state
git add <file>                # stage a file
git add .                     # stage everything
git commit -m "message"       # commit staged changes
git log                       # view commit history
git log --oneline --graph     # compact visual history
```



### Branching

```bash
git branch                    # list branches
git branch <name>             # create a branch
git checkout <name>            # switch to a branch
git checkout -b <name>          # create and switch in one step
git switch <name>               # modern way to switch branches
git merge <branch>              # merge a branch into current branch
git branch -d <name>             # delete a branch
```



### Remote Repositories

```bash
git remote add origin <url>
git remote -v
git push origin <branch>
git pull origin <branch>
git fetch                       # download changes without merging
```



### Undoing Things

```bash
git restore <file>              # discard changes in working directory
git reset <file>                 # unstage a file
git reset --hard <commit>         # reset repo to a specific commit (destructive)
git revert <commit>                # create a new commit that undoes a previous one
```



### Inspecting Changes

```bash
git diff                        # unstaged changes
git diff --staged               # staged changes
git show <commit>                # details of a specific commit
```



### Stashing

```bash
git stash                       # temporarily save uncommitted changes
git stash pop                    # reapply stashed changes
git stash list                   # view all stashes
```



### Tags

```bash
git tag v1.0                    # create a lightweight tag
git tag -a v1.0 -m "message"      # create an annotated tag
git push origin v1.0              # push a tag
```

---



## 8. Common Git Workflows



### Feature Branch Workflow

1. Create a branch from `main` for each feature: `git checkout -b feature/login`
2. Work and commit changes on that branch.
3. Push the branch and open a pull request (on GitHub/GitLab).
4. After review, merge into `main`.



### Gitflow

A stricter workflow using long-lived branches:

- `main` — production-ready code
- `develop` — integration branch
- `feature/*`, `release/*`, `hotfix/*` — supporting branches



### Forking Workflow

Common in open source: contributors fork a repository into their own account, make changes, and submit a pull request back to the original repository.

---



## 9. Merge vs Rebase


| Merge                                          | Rebase                                                  |
| ---------------------------------------------- | ------------------------------------------------------- |
| Preserves full history including branch points | Creates a clean, linear history                         |
| Adds a merge commit                            | Rewrites commit history                                 |
| Safe for shared/public branches                | Should be avoided on shared branches (rewrites history) |
| `git merge feature`                            | `git rebase main`                                       |


**Rule of thumb:** Never rebase commits that have already been pushed and shared with others.

---



## 10. .gitignore

A file listing patterns of files/folders Git should ignore (not track), such as:

```
node_modules/
.env
*.log
dist/
__pycache__/
```

---



## 11. Pull Request (PR) vs Commit vs Push

- **Commit** — saving a snapshot of changes locally.
- **Push** — sending local commits to a remote repository.
- **Pull Request / Merge Request** — a request (on GitHub/GitLab) asking to merge changes from one branch into another, usually reviewed by teammates before merging.

---



## 12. GitHub-Specific Concepts

- **Issues** — track bugs, tasks, or feature requests.
- **Pull Requests (PRs)** — propose and review code changes before merging.
- **Actions** — CI/CD automation (build, test, deploy pipelines).
- **Forks** — a personal copy of someone else's repository.
- **Stars/Watch** — bookmarking and following repositories.
- **GitHub Pages** — free static site hosting from a repo.

---



## 13. Frequently Asked Questions

**Q: Is Git the same as GitHub?**
No. Git is the version control tool; GitHub is a hosting platform built around Git.

**Q: Who invented Git and why?**
Linus Torvalds created Git in 2005 for managing Linux kernel development after losing access to the previously used proprietary tool, BitKeeper.

**Q: Is Git centralized or distributed?**
Distributed — every clone has the complete project history, unlike centralized systems such as SVN.

**Q: What is the default branch name in Git?**
Historically `master`; most platforms (including GitHub) now default to `main`.

**Q: Can Git be used without GitHub?**
Yes. Git works entirely locally and can be used with any hosting service (GitLab, Bitbucket, self-hosted servers) or no hosting at all.

**Q: What's the difference between** `git fetch` **and** `git pull`**?**
`git fetch` downloads changes from the remote without merging them into your working branch. `git pull` is essentially `git fetch` followed by `git merge`.

**Q: What happens during a merge conflict?**
Git marks the conflicting sections in the file with `<<<<<<<`, `=======`, and `>>>>>>>` markers, and the developer must manually resolve which changes to keep before committing.

**Q: Is Git free and open source?**
Yes, Git is free and open-source software, licensed under the GNU General Public License (GPL v2).

---

