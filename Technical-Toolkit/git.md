# Introduction to Git
Git is a version control system—a tool that helps developers manage and track changes to their code over time. Think of it as a detailed history book for your project, recording what was changed, when, and by whom. This makes it easy to collaborate with others, experiment without fear, and roll back to previous versions if something goes wrong.

Originally created by Linus Torvalds in 2005 to manage the Linux kernel, Git has since become the industry standard for source code management. It powers collaboration on everything from solo side projects to massive enterprise applications.

## How Git Works
Git operates as a distributed version control system, which means every developer has a full copy of the entire project history stored locally on their machine. This is different from centralized systems, which rely on a single server to hold the history.

Here’s a high-level overview of how Git works:

* **Repository (repo)**: A Git repository is the project’s database. It stores all your code, along with the complete history of changes. A repo can be local (on your computer) or remote (on platforms like GitHub or GitLab).

* **Commits**: A commit is a snapshot of your project at a specific point in time. When you make changes to your code and commit them, Git records those changes, along with a message describing what was done.

* **Branches**: A branch is a parallel version of your project. Developers use branches to work on features or bug fixes without affecting the main (or “production”) codebase. Once the work is complete, it can be merged back into the main branch.

* **Merge and Pull Requests**: When you’re ready to combine changes from one branch into another, you use a merge. On protected branches, this involves a pull request (PR), where others can review your changes before they’re merged.

* **Remote Repositories**: Git lets you sync your local repo with remote ones, allowing multiple people to collaborate. You use commands like push (to send your changes) and pull or fetch (to get changes from others).

## Core commands

#### git clone

When you want to download and start working on an existing project, `git clone` creates a copy of a remote repository on your local machine.

```bash
git clone https://github.com/organisation/repository-name.git
```

What it does:
- Downloads the full codebase and its entire history
- sets up a connection to the remote repository so you can pull updates or push your changes later.

#### git add 

When you've made changes to files and want to include them in your next commit, `git add` stages changes in your working directory to be committed.

```bash
# Stages a specific file
git add <path/to/file>

# Stages all changes 
git add .
```

What it does:
- Tells Git which changes to "prepare" for the next commit.
- You can selectively add specific files or all modified files.

> TIP: Changes are staged in preparation for a commit. Keep the changes concise. Don't bundle too many changes into one commit.

#### git commit
When you’ve staged your changes and are ready to log them as part of the project history, `git commit` saves a snapshot of your staged changes to the repository’s history. 

> TIP: Use descriptive commit messages for better collaboration.

```bash
git commit -m "Updates list of ICD10 codes used in classifying diabetic cohorts"
```

What it does:
- Records the staged changes along with a message describing what was done.
- Commits are saved only in your local repository (not yet shared with others).

#### git push
When you want to share your changes with collaborators or back them up to the remote server, `git push` sends your commits to the remote repository on GitHub.

```bash
git push
```

What it does:
- Transfers your commits to the specified branch on the remote repo.
- Collaborators can now see and build on your work.

#### git status
To check which files have been modified, staged, or are untracked, use `git status`. It shows the current state of your working directory and staging area.

```bash
git status
```

What it does:
- Tells you which changes are staged for commit.
- Shows which files are modified or new but not yet staged.
- Helps you keep track of what’s going on in your local repo.

#### git pull
To update your local project with the latest changes from the remote repository, use `git pull`. This fetches and integrates changes from the remote repository into your local branch.

```bash
git pull
```


## Branching

See the [contributing guide](../How-To/contributing-guide.md) for a guide on branching.

To switch to an existing branch:

```bash
git checkout dev
```

To create a new branch, making a copy of the current active branch:

```bash
git checkout -b <branch-name>
```

## Other commands

- `git log`: 
- `git branch`: Shows all local branches
- `git merge <branch>`: Merges changes from the specified branch to the active branch
- `git diff`: Shows line-by-line changes between your working directory and the staging area (changes made but not yet staged with `git add`)
- `git diff --cached`: Compares changes that have been staged
- `git branch -d <branch-name>` Delete a branch locally
- `git push -d <remote-name> <branch-name>` Delete a branch on the remote repository

#### Undo commits or unstage changes
- Undo a commit without rewriting history (safer than `git reset` for shared branches). Creates a new commit that undoes a previous commit

```bash
git revert <commit-hash>
```

- Undo the last commit but keep the changes:

```bash
git reset --soft HEAD~1
```

- Completely undo the last commit and discard changes:

```bash
git reset --hard HEAD~1
```

> CAUTION: --hard is destructive. It deletes changes permanently if not backed up.

#### Pull a specific file from another branch
```bash
git checkout <source-branch> -- <path/to/file>
```

#### Change git remote
```bash
git remote -v
git remote set-url origin <ssh link>
```

#### How to create a tag to a certain commit
```bash
git tag -a <tag-name> <commit> -m "Tag Message"
git push <remote-name> <tag-name>
```
e.g: `git tag -a M1 e3afd03 -m “Milestone One!”`

#### Squash recent commits into one:
```bash
git reset --soft HEAD~n
git commit
git push —force
```

#### Cherry Picking commits
- To cherry-pick a single commit: 
```bash
git cherry-pick <commit-hash>
```

- To cherry-pick multiple commits:
```bash
git cherry-pick <commit1> <commit2> <commit3> <commit4> <commit5>
```

- To cherry-pick a range of commits INCLUDING the beginning commit: 

```bash   
git cherry-pick beginning_commit~..ending_commit
```

OR
```bash
git cherry-pick beginning_commit~1..ending_commit
```

OR 
```bash
git cherry-pick beginning_commit^..ending_commit
```

- To cherry-pick a range of commits EXCLUDING the beginning commit:  
```bash
git cherry-pick beginning_commit..ending_commit
```

#### Steps to delete untracked Git files
* Run `git clean -n` to see a dry run.
* Run `git clean -f` to force untracked file deletion.
* Use `git clean -f -d` to remove untracked directories.
* Use `git clean -f -x` to remove untracked `. gitignore` files.
* Add the `-i` switch to do an interactive git clean.