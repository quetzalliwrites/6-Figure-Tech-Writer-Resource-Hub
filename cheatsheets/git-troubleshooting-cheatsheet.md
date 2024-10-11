
# 🤯 Common Git Command Errors + Solutions: Cheatsheet
My cheatsheet documents common git errors and their solutions.

### 🐛 `fatal: not a git repository (or any of the parent directories): .git`
**Cause**: 
You’re trying to run a Git command outside of a Git repository.

**Solution**:
- Navigate to the root of an existing Git repository, or...
- Run `git init` to initialize a new Git repository.

### 🪲 `error: Your local changes to the following files would be overwritten by merge`
**Cause**: You have uncommitted changes that would be overwritten by a merge.

**Solution**:
1. Commit your changes: `git add .` and `git commit -m "Save changes"`
2. Or, stash your changes: `git stash` before merging.

### 🐁 `fatal: Authentication failed`
**Cause**: The authentication credentials for the remote repository are incorrect.

**Solution**:
- Update your credentials for the remote repository.
- Use a Personal Access Token (PAT) instead of a password if using HTTPS.
- Ensure your SSH keys are configured correctly if using SSH.

### 🦟 `error: failed to push some refs`
**Cause**: Your local branch is behind the remote branch, or there are conflicts.

**Solution**:
1. Fetch the latest changes: `git fetch`
2. Rebase or merge: `git rebase origin/[branch-name]` or `git pull`
3. Resolve any conflicts, then push again.

### 🐞 `merge conflict in [file-name]`
**Cause**: There are conflicting changes between your branch and the branch you’re merging.

**Solution**:
1. Open the conflicting file and resolve the conflicts.
2. Mark the file as resolved: `git add [file-name]`
3. Complete the merge: `git commit`

### 🐹 `detached HEAD state`
**Cause**: You’ve checked out a specific commit instead of a branch.

**Solution**:
- Switch back to a branch: `git checkout [branch-name]`
- Or create a new branch from the current state: `git checkout -b [new-branch-name]`

### 🦍 `remote: Repository not found`
**Cause**: The remote repository URL is incorrect or the repository does not exist.

**Solution**:
- Verify the repository URL: `git remote -v`
- Update the remote URL if needed: `git remote set-url origin [new-repo-url]`

### 🗿 `fatal: refusing to merge unrelated histories`
**Cause**: You’re trying to merge branches from repositories with different histories.

**Solution**:
- Use the `--allow-unrelated-histories` flag: `git merge [branch-name] --allow-unrelated-histories`

### 🐉 `error: pathspec '[branch-name]' did not match any file(s) known to git`
**Cause**: The branch you’re trying to check out does not exist.

**Solution**:
- Verify the branch name is correct.
- List all available branches: `git branch -a`

### 🐱 `cannot rebase: You have unstaged changes.`
**Cause**: There are unstaged changes in your working directory.

**Solution**:
- Stage the changes: `git add .`
- Or stash the changes: `git stash`
- Then proceed with the rebase.

