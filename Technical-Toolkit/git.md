# Git

- `git add <file name>` moves to staging area, starts tracking changes
- `git add .` adds all items in the current directory to staging area
- `git commit -m "commit message"`
- `git log`
- `git checkout -b <branch-name>` (creating a branch. To switch to existing branch,
take out ‘-b‘)
- `git branch` (to see all local branches)
- git merge <source-branch> (while switched to the branch you want to
merge too. This merges changes from the branch typed in the command to the
current branch)
git push -u origin master
git pull
git reset --soft HEAD^1 (Undo commit)
git reset --hard HEAD~2
git rm --cached <file-name> (remove file from staging area)
git revert -m 1 --no-commit 21a4d80..HEAD
git revert <commit hash>
git stash [-u] (-u for stashing untracked changes)
git stash pop
https://www.atlassian.com/git/tutorials/saving-changes/git-
stash#:~:text=Invoking%20git%20stash%20encodes%20any,files%20as%20an%
20additional%20commit.
Delete a branch:
1.
2.
git push -d <remote
name> <branch
_
_name> //remotely
git branch -d <branch
_name> //locally
How To Rename a Local and Remote Git Branch
https://linuxize.com/post/how-to-rename-local-and-remote-git-branch/
How to pull a specific file from another branch
While in <to branch>:
git checkout <from
_
branch> -- <path/to/file>
Change git remote
git remote -v
git remote set-url origin <ssh link>
How to create a tag to a certain commit
git tag -a <tag name> <commit> -m "Tag Message"
git push <remote name> <tag name>
e.g: git tag -a M1 e3afd03 -m “Milestone One!”
Creating gh-pages:
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "Initializing gh-pages branch"
git push origin gh-pages
git checkout -
Ref: https://jiafulow.github.io/blog/2020/07/09/create-gh-pages-branch-in-
existing-repo/
Squash recent commits into one:
–
–
git reset --soft HEAD~n
git commit
git push —force
Cherry Picking commits
to cherry-pick a single branch or commit named commit: git cherry-pick
commit
to cherry-pick multiple commits: git cherry-pick commit1 commit2
commit3 commit4 commit5
to cherry-pick a range of commits
–
INCLUDING the beginning_
commit: git cherry-pick
beginning_
commit~..ending_
commit
–
OR (same as above): git cherry-pick
beginning_
commit~1..ending_
commit
OR (same as above): git cherry-pick
–
–
–
–
1.
2.
beginning_
commit^..ending_
commit
NOT including the beginning_
commit: git cherry-pick
beginning_
commit..ending_
commit
To undo a non-squashed merge in-between proper squash merge commits:
Git reset to the last PR commit before the mess (git reset —hard commit)
Cherry pick the range of proper commits following the mess
Search Issues and PRs by Branch name:
head:HEAD
BRANCH
_
base:BASE
BRANCH
_
Squash specific commits
Link
https://docs.github.com/en/search-github/searching-on-github/searching-issues-
and-pull-requests#search-by-branch-name
Renaming a branch:
https://docs.github.com/en/repositories/configuring-branches-and-merges-in-
your-repository/managing-branches-in-your-repository/renaming-a-branch