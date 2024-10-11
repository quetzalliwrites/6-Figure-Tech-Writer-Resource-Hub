# 🏆 Git Cheatsheet for Documentation Workflows 

My cheatsheet covers typical Git commands used in documentation workflows, common git errors, and their solutions.

## Table of Contents
1. [Common Git Commands for Documentation Workflows](#common-git-commands-for-documentation-workflows)
2. [Common Git Command Errors and Solutions](#common-git-command-errors-and-solutions)

---

## 🧠 Common Git Commands for Docs Workflows 

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

---

## 🤯 Common Git Command Errors and Solutions

### Error 1: `fatal: not a git repository (or any of the parent directories): .git`
**Cause**: You’re trying to run a Git command outside of a Git repository.

**Solution**:
- Navigate to the root of an existing Git repository, or
- Run `git init` to initialize a new Git repository.

### Error 2: `error: Your local changes to the following files would be overwritten by merge`
**Cause**: You have uncommitted changes that would be overwritten by a merge.

**Solution**:
1. Commit your changes: `git add .` and `git commit -m "Save changes"`
2. Or, stash your changes: `git stash` before merging.

### Error 3: `fatal: Authentication failed`
**Cause**: The authentication credentials for the remote repository are incorrect.

**Solution**:
- Update your credentials for the remote repository.
- Use a Personal Access Token (PAT) instead of a password if using HTTPS.
- Ensure your SSH keys are configured correctly if using SSH.

### Error 4: `error: failed to push some refs`
**Cause**: Your local branch is behind the remote branch, or there are conflicts.

**Solution**:
1. Fetch the latest changes: `git fetch`
2. Rebase or merge: `git rebase origin/[branch-name]` or `git pull`
3. Resolve any conflicts, then push again.

### Error 5: `merge conflict in [file-name]`
**Cause**: There are conflicting changes between your branch and the branch you’re merging.

**Solution**:
1. Open the conflicting file and resolve the conflicts.
2. Mark the file as resolved: `git add [file-name]`
3. Complete the merge: `git commit`

### Error 6: `detached HEAD state`
**Cause**: You’ve checked out a specific commit instead of a branch.

**Solution**:
- Switch back to a branch: `git checkout [branch-name]`
- Or create a new branch from the current state: `git checkout -b [new-branch-name]`

### Error 7: `remote: Repository not found`
**Cause**: The remote repository URL is incorrect or the repository does not exist.

**Solution**:
- Verify the repository URL: `git remote -v`
- Update the remote URL if needed: `git remote set-url origin [new-repo-url]`

### Error 8: `fatal: refusing to merge unrelated histories`
**Cause**: You’re trying to merge branches from repositories with different histories.

**Solution**:
- Use the `--allow-unrelated-histories` flag: `git merge [branch-name] --allow-unrelated-histories`

### Error 9: `error: pathspec '[branch-name]' did not match any file(s) known to git`
**Cause**: The branch you’re trying to check out does not exist.

**Solution**:
- Verify the branch name is correct.
- List all available branches: `git branch -a`

### Error 10: `cannot rebase: You have unstaged changes.`
**Cause**: There are unstaged changes in your working directory.

**Solution**:
- Stage the changes: `git add .`
- Or stash the changes: `git stash`
- Then proceed with the rebase.

