# Git and GitHub CLI Commands Guide

A comprehensive guide to Git and GitHub CLI commands for various use cases.

## Table of Contents
- [Git Basic Commands](#git-basic-commands)
- [Git Branching and Merging](#git-branching-and-merging)
- [Git Remote Operations](#git-remote-operations)
- [Git History and Diffs](#git-history-and-diffs)
- [Git Configuration](#git-configuration)
- [Git Stashing and Cleaning](#git-stashing-and-cleaning)
- [Git Advanced Operations](#git-advanced-operations)
- [GitHub CLI (gh) Commands](#github-cli-gh-commands)
- [GitHub CLI PR Operations](#github-cli-pr-operations)
- [GitHub CLI Issue Management](#github-cli-issue-management)
- [GitHub CLI Repository Management](#github-cli-repository-management)
- [GitHub CLI Advanced Features](#github-cli-advanced-features)

## Git Basic Commands

### Initialize a Repository
```bash
git init
```

### Clone a Repository
```bash
git clone <repository-url>
git clone <repository-url> <directory>
git clone --depth=1 <repository-url>  # Shallow clone with only recent history
```

### Check Status
```bash
git status
git status -s  # Short status
```

### Add Files
```bash
git add <file>
git add .  # Add all files
git add -A  # Add all changes (new, modified, deleted)
git add -u  # Add only modified and deleted files
```

### Commit Changes
```bash
git commit -m "Commit message"
git commit -am "Commit message"  # Add modified files and commit
git commit --amend  # Amend previous commit
```

### Discard Changes
```bash
git checkout -- <file>  # Discard changes in a file
git restore <file>  # New way to discard changes (Git 2.23+)
git reset --hard  # Discard all local changes
```

## Git Branching and Merging

### Branch Operations
```bash
git branch  # List branches
git branch -a  # List all branches (including remote)
git branch <branch-name>  # Create a branch
git branch -d <branch-name>  # Delete a branch
git branch -D <branch-name>  # Force delete a branch
git branch -m <new-branch-name>  # Rename current branch
```

### Switch Branches
```bash
git checkout <branch-name>
git switch <branch-name>  # New way to switch branches (Git 2.23+)
git checkout -b <new-branch>  # Create and checkout branch
git switch -c <new-branch>  # Create and switch to branch (Git 2.23+)
```

### Merge Branches
```bash
git merge <branch-name>
git merge --no-ff <branch-name>  # Create a merge commit even if fast-forward is possible
git merge --abort  # Abort the merge in case of conflicts
```

### Rebase
```bash
git rebase <branch-name>
git rebase -i HEAD~<n>  # Interactive rebase for last n commits
git rebase --abort  # Abort the rebase
git rebase --continue  # Continue rebase after resolving conflicts
```

## Git Remote Operations

### Remote Repositories
```bash
git remote -v  # List remote repositories
git remote add <name> <url>  # Add a remote repository
git remote remove <name>  # Remove a remote
git remote rename <old-name> <new-name>  # Rename a remote
```

### Fetch, Pull, and Push
```bash
git fetch <remote>  # Fetch changes from remote
git fetch --all  # Fetch from all remotes
git pull  # Fetch and merge changes
git pull --rebase  # Fetch and rebase changes
git push <remote> <branch>  # Push changes to remote
git push -u <remote> <branch>  # Push and set upstream
git push --force  # Force push (use with caution!)
git push --force-with-lease  # Safer force push
```

## Git History and Diffs

### View History
```bash
git log  # View commit history
git log --oneline  # Compact view
git log --graph --oneline --all  # Graphical view of history
git log -p  # Show diffs in each commit
git log -n <number>  # Show only last n commits
git log --author="<name>"  # Filter by author
git shortlog  # Group commits by author
```

### Diff Operations
```bash
git diff  # Show unstaged changes
git diff --staged  # Show staged changes
git diff <commit1> <commit2>  # Compare two commits
git diff <branch1> <branch2>  # Compare two branches
git diff <file>  # Show changes in specific file
```

### Blame
```bash
git blame <file>  # Show who changed what and when in a file
git blame -L <start>,<end> <file>  # Blame specific line range
```

## Git Configuration

### User Configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list  # List all configuration
git config --global core.editor "code --wait"  # Set VS Code as default editor
```

### Aliases
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --graph --oneline --all"
```

## Git Stashing and Cleaning

### Stash Operations
```bash
git stash  # Stash changes
git stash save "message"  # Stash with message
git stash list  # List stashes
git stash apply  # Apply most recent stash
git stash apply stash@{n}  # Apply specific stash
git stash pop  # Apply and remove most recent stash
git stash drop stash@{n}  # Remove specific stash
git stash clear  # Remove all stashes
```

### Cleaning
```bash
git clean -n  # Dry run, show what would be removed
git clean -f  # Remove untracked files
git clean -fd  # Remove untracked files and directories
git clean -fX  # Remove only ignored files
git clean -fx  # Remove ignored and untracked files
```

## Git Advanced Operations

### Cherry-Pick
```bash
git cherry-pick <commit>  # Apply changes from specific commit
git cherry-pick <commit1> <commit2>  # Cherry-pick multiple commits
git cherry-pick --abort  # Abort cherry-pick
```

### Submodules
```bash
git submodule add <repository> <path>  # Add a submodule
git submodule init  # Initialize submodules
git submodule update  # Update submodules
git submodule update --init --recursive  # Initialize and update recursively
```

### Tags
```bash
git tag  # List tags
git tag <tag-name>  # Create lightweight tag
git tag -a <tag-name> -m "message"  # Create annotated tag
git push origin <tag-name>  # Push specific tag
git push --tags  # Push all tags
git tag -d <tag-name>  # Delete local tag
git push origin --delete <tag-name>  # Delete remote tag
```

### Worktree
```bash
git worktree list  # List worktrees
git worktree add <path> <branch>  # Create a new worktree
git worktree remove <path>  # Remove a worktree
```

## GitHub CLI (gh) Commands

### Authentication
```bash
gh auth login  # Login to GitHub
gh auth status  # Check authentication status
gh auth logout  # Logout from GitHub
```

### Repository Operations
```bash
gh repo create  # Create a new repository
gh repo clone <repository>  # Clone a repository
gh repo view  # View repository details
gh repo fork  # Fork a repository
gh repo list  # List your repositories
```

## GitHub CLI PR Operations

### Pull Requests
```bash
gh pr create  # Create a pull request
gh pr list  # List pull requests
gh pr view [<number>]  # View a pull request
gh pr checkout <number>  # Checkout a pull request locally
gh pr merge <number>  # Merge a pull request
gh pr close <number>  # Close a pull request
gh pr comment <number> -b "comment"  # Comment on a pull request
gh pr review <number>  # Review a pull request
gh pr diff <number>  # View pull request diff
```

## GitHub CLI Issue Management

### Issues
```bash
gh issue create  # Create an issue
gh issue list  # List issues
gh issue view <number>  # View an issue
gh issue close <number>  # Close an issue
gh issue reopen <number>  # Reopen an issue
gh issue comment <number> -b "comment"  # Comment on an issue
gh issue status  # View your issues
gh issue transfer <number> <repository>  # Transfer an issue
```

## GitHub CLI Repository Management

### Repository Settings
```bash
gh repo edit  # Edit repository settings
gh repo rename <new-name>  # Rename a repository
gh repo delete <repository>  # Delete a repository
gh repo archive <repository>  # Archive a repository
```

### Releases and Tags
```bash
gh release create <tag> [<files>...]  # Create a release
gh release list  # List releases
gh release view <tag>  # View release details
gh release delete <tag>  # Delete a release
gh release download <tag>  # Download release assets
```

## GitHub CLI Advanced Features

### Workflows and Actions
```bash
gh workflow list  # List workflows
gh workflow view <workflow>  # View workflow details
gh workflow run <workflow>  # Run a workflow
gh run list  # List workflow runs
gh run view <run-id>  # View a workflow run
```

### Gists
```bash
gh gist create <file>...  # Create a gist
gh gist list  # List your gists
gh gist view <gist-id>  # View a gist
gh gist edit <gist-id>  # Edit a gist
gh gist delete <gist-id>  # Delete a gist
```

### Codespaces
```bash
gh codespace create  # Create a codespace
gh codespace list  # List your codespaces
gh codespace stop  # Stop a codespace
gh codespace delete  # Delete a codespace
gh codespace ssh  # Connect to a codespace via SSH
```

---

Last updated: April 18, 2025
