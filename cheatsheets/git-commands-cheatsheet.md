# 🏆 Common Git Commands: Cheatsheet

My cheatsheet documents common Git commands you'll need for documentation workflows.


| Command                                  | Description                                                                                   |
|------------------------------------------|-----------------------------------------------------------------------------------------------|
| `git clone [repository URL]`             | Clone a repository to your local machine.                                                      |
| `git status`                             | Check the status of your working directory (e.g., modified files, untracked files).            |
| `git add [file]`                         | Stage a file for commit. Use `.` to stage all changes in the working directory.                |
| `git commit -m "Commit message"`         | Commit staged changes with a descriptive message.                                              |
| `git pull`                               | Fetch and merge changes from the remote repository into your current branch.                   |
| `git push`                               | Push local commits to the remote repository.                                                   |
| `git checkout [branch]`                  | Switch to an existing branch.                                                                  |
| `git checkout -b [new-branch-name]`      | Create a new branch and switch to it.                                                          |
| `git merge [branch-name]`                | Merge changes from the specified branch into the current branch.                               |
| `git fetch`                              | Download objects and references from the remote repository without merging.                    |
| `git rebase [branch-name]`               | Reapply commits on top of another base branch. Useful for keeping a feature branch up to date. |
| `git reset [file]`                       | Unstage a file while keeping its changes in the working directory.                             |
| `git log`                                | View a list of commit history for the current branch.                                          |
| `git diff`                               | Show changes made to tracked files that haven't been staged.                                   |
| `git stash`                              | Save changes that aren’t ready to be committed, allowing you to work on something else.        |
| `git stash pop`                          | Reapply the most recently stashed changes and remove them from the stash list.                 |
| `git rm [file]`                          | Remove a file from the repository and the working directory.                                   |
| `git revert [commit-hash]`               | Create a new commit that undoes changes from a specific commit.                                |

