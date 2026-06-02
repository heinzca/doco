# Git Reference

[Back to README](README.md)

**Sub-headings:**

- [Git Config](#git-config)
- [Initialize a Git Directory](#initialize-a-git-directory)
- [Git Staging](#git-staging)
- [Git Commit](#git-commit)
- [Git Tagging](#git-tagging)
- [Git Stash](#git-stash)
- [Git History](#git-history)
- [Git Help](#git-help)
- [Git Branch](#git-branch)
- [Git Merge](#git-merge)
- [Git Workflow](#git-workflow)
- [Git Best Practices](#git-best-practices)

## Git Config  

([top](#git-reference))

**Use**:

- `--global` to set values for all repositories; or  
- `--local` to set values for the current repository only  

| Command | Action |
| ----- | ----- |
| `git config --global user.name "Your Name"` | Configure your user name |
| `git config --global user.email "you@example.com"` | Configure your email address |
| `git config --list` | See all of your git config settings |
| `git config user.name` | See a specific value - define it. e.g. user.name |
| `run same git config command with new value` | To replace an existing value |
| `git config --global --unset global user.name` | To unset a specific value use the --unset tag |
| `git config --global init.defaultBranch main` | Set the default branch to the defined value. e.g. "main" in this instance |
| `git config user.name "Project Name"` | Set a local user name config |
| `git config --global user.name "Global Name"` | Set a global user name config |
| `git config --system user.name "System Name"` | Set a system user name config |

## Initialize a Git Directory

([top](#git-reference))

- A Git repository is a folder that Git tracks for changes.  
- The repository stores all your project's history and versions.  
- When you run git init, git creates a hidden folder '.git' where all info for the git repository is stored.  

| Command | Action |
| ----- | ----- |
| `mkdir myproject` | Create the project directory |
| `cd myproject` | Change directory to new project |
| `git init` | Initialize the git directory |

## Git Staging

([top](#git-reference))

| Command | Action |
| ----- | ----- |
| `git add filename.md` | Stage a single file called filename.md |
| `git add --all` or `git add -A` | Stage all changes - multiple files |
| `git add .` | Stage all files in current directory |
| `git status` | See the current status, as well as the current branch |
| `git restore --staged <file>` | Un-stage a file (fails if no prior commits) |
| `git rm --cached <file>` | Alternative un-stage |

## Git Commit

([top](#git-reference))

| Command | Action |
| ----- | ----- |
| `git commit -m "message"` | Commit staged changes with a message |
| `git commit -a -m "message"` | Commit all tracked changes without staging + message. Be careful. Can commit unwanted changes. |
| `git commit` | Commit with prompt for message. Allows multi line messages via text editor |
| `git commit --allow-empty -m "message"` | Commit an empty project with a message - useful for initiating a new project |
| `git commit --amend -m "corrected message"` | Add a file to last commit. git add first, then amend with updated message |
| `git commit --amend --no-edit` | Add a file to last commit. git add first, but keeps original message |
| `git log` | View commit history. Show a log of all commits |
| `git log --oneline` | Show a log of all commits -> one per line |
| `git log --stat` | Show which files changed in each commit |
| `git reset --soft HEAD~1` | Undo the last commit and keep your changes staged |

## Git Tagging

([top](#git-reference))

| Command | Action |
| ----- | ----- |
| `git tag v1.0` | Add a simple name / tag for a commit |
| `git tag -a v1.0 -m "Version 1.0 release"` | An annotated tag also stores your name, the date, and a message. |
| `git tag v1.1 bb3ecbd` | Tag a specific commit |
| `git tag` | List all tags in your repository |
| `git show v1.0` | See details about a tag and the commit it points to |
| `git push origin v1.0` | Push a specific tag to remote repository |
| `git push --tags` | Push all your local tags to the remote at once (useful if you've created several tags) |
| `git tag -d v1.0` | Delete a tag locally |
| `git push origin --delete tag v1.0` | Delete a tag from the remote repository |
| `git tag -f v1.0 <new-commit-hash>` | Move a tag to a different commit (-f is force); and |
| `git push --force origin v1.0` | Push the update to remote |

### Tagging Best Practices

- Use tags to mark releases, major milestones, or stable points in your project.  
- Always use annotated tags (with -a -m) for anything public or shared.  
- Create tags after passing all tests or before deploying/releasing code.  

### Tagging Troubleshooting

- Tag already exists? Use `git tag -d <tagname>` to delete it, then re-create.  
- Pushed the wrong tag? Delete it locally and remotely, then push the correct tag.  
- Tag not showing on remote? Remember to push tags with `git push origin <tag name>` or `git push --tags`.  
- Need to overwrite a tag on the remote? You can force-push a tag with `git push --force origin <tag name>`, but be careful! This will overwrite the tag for everyone using the remote.  

## Git Stash

([top](#git-reference))

Sometimes you need to quickly switch tasks or fix a bug, but you're not ready to commit your work.  

git stash lets you save your uncommitted changes and return to a clean working directory.  

You can come back and restore your changes later.  

Here are some common use cases:

- Switch branches safely: Save your work before changing branches.
- Handle emergencies: Stash your work to fix something urgent, then restore it.
- Keep your work-in-progress safe: Avoid messy commits or losing changes.  

Each time you run `git stash`, your changes are saved on top of a stack.  
The most recent stash is on top, and you can apply or drop stashes from the top down, or pick a specific one from the list.  

| Command | Action |
| ----- | ----- |
| `git stash` | Stash your changes. Tracked file (staged and unstaged) are tracked by default. Untracked are not stashed by default. |
| `git stash -u` | Includes untracked files in your stash. |
| `git stash push -m "stash message"` | Add a  message to remember what you stashed. |
| `git stash list` | See your saved stashes (stack). |
| `git stash apply` | Restore your most recent stashed changes (keeps the stash in the stack) |
| `git stash apply stash@{n}` | Restore a specific stash from the list. |
| `git stash pop` | Apply the latest stash from the stack and remove it from the list |
| `git stash drop stash@{0}` | Delete a specific stash when you no longer need it. |
| `git stash clear` | Delete all of your stashes at once. |
| `git stash branch new-feature stash@{0}` | Create a new branch and apply a stash to it. Useful if your stashed work should become its own feature branch. |

## Git History

([top](#git-reference))

| Command | Action |
| --------------- | ----- |
| `git log` | Show full commit history. All commits including author, date and message. Use arrow keys to scroll and q to quit.  To search within th results type /word, enter then n to jump to next. |
| `git log --oneline` | Show a summary of commits. SIngle line per commit and a short commit ref. |
| `git show <commit>` | Show details of a specific commit. |
| `git show HEAD` | Show details of the latest commit. |
| `git diff` | Unstaged changes. Shows the difference between your working directory and the last commit. |
| `git diff --staged` | Staged changes. Shows the difference between your staged files and the last commit. |
| `git diff <commit1> <commit2>` | See what chnaged between any 2 commits. |
| `git log --author="Heinz"` | Show commits by a defined Author. |
| `git log --since="2 weeks ago"` | Show commits within the specific timeframe. |
| `git log --oneline --since="21/04" --until="24/04"` | Date filters, plus summarizing as oneline. |
| `git log --stat` | See which files were changed in each commit and how many lines were added or removed. |
| `git log --graph` | ASCII graph of your branch history (great for visualizing merges). |
| `git log --graph --oneline` | Oneline version of the ASCII graph. |

## Git Help

([top](#git-reference))

| Command | Action |
| ----- | ----- |
| `git help <command>` | See the manual page for a command |
| `git <command> --help` | Same as above |
| `git <command> -h` | See a quick summary of options |
| `git help --all` | List all possible Git commands |
| `git help -g` | List guides and concepts |

While viewing help pages:  

- Use the arrow keys or Space to scroll down, b to scroll up.
- Type / followed by a word to search (e.g., /option), then n for next match.
- Press q at any time to quit the help view.

## Git Branch

([top](#git-reference))

Common reasons to create a branch:  

- Developing a new feature
- Fixing a bug
- Experimenting with ideas  

| Command | Action |
| ----- | ----- |
| `git branch branch-name` | Create a new branch. |
| `git branch` | Show a list of all branches. The `*` next to a listed branch indicates the active branch. |
| `git checkout branch-name` or `git switch branch-name` | Switch to the defined branch. |
| `git checkout -b new-branch` | Create new branch and switch to it. |
| `git branch -d emergency-fix` | Deletes a branch, assuming it is already merged. |
| `git branch -D emergency-fix` | Deletes an unmerged branch. |
| `git branch -m old-name new-name` | Rename a branch |

### Best Practices for Working with Branches

- Use clear, descriptive branch names (like feature/login-page or bugfix/header-crash).
- Keep each branch focused on a single purpose or feature.
- Regularly merge changes from the main branch to keep your branch up-to-date.
- Delete branches that are no longer needed to keep your repository clean.

## Git Merge

([top](#git-reference))

### Merge Tips

- Switch to the branch you want to merge into before conducting the merge.
- Always commit or stash your changes before starting a merge.
- Regularly merge from the main branch into your feature branch to minimize conflicts.
- Read and resolve conflicts carefully-don't just accept all changes blindly.
- Write clear and descriptive merge commit messages.

| Command | Action |
| ----- | ----- |
| `git merge emergency-fix` | Merge the emergency-fix branch into the main branch, assuming you switched to main first. Since the emergency-fix branch came directly from master, and no other changes had been made to master while we were working, Git sees this as a continuation of master. So it can "Fast-forward", just pointing both master and emergency-fix to the same commit. |
| `git merge --no-ff feature-branch` | By default, if your branch can be merged with a fast-forward (no new commits on the base), Git just moves the branch pointer forward. If you want to always create a merge commit (to keep history clearer), use `git merge --no-ff [branch name]`. |
| `git merge --squash` | If you want to combine all the changes from a branch into a single commit (instead of keeping every commit), use `git merge --squash {branch name]`. This is useful for cleaning up commit history before merging. |
| `git merge --abort` | If you run into trouble during a merge (like a conflict you don't want to resolve), you can cancel the merge and go back to how things were before with `git merge --abort`. |

### Merge Conflicts

- A merge conflict happens when changes in two branches touch the same part of a file and Git doesn't know which version to keep.
- Think of it like two people editing the same sentence in a document in different ways-Git needs your help to decide which version to use.
- To resolve:
  - Abort the merge via: git merge --abort
  - You need to open the file, look for lines like `<<<<<<< HEAD` and `=======`, and decide what the final version should be.
  - Then, stage and commit your changes.

## Git Workflow

([top](#git-reference))

Git uses a distributed workflow that allows you to work on your code, stage changes, and commit them to your local repository before sharing with others.  

Understanding this workflow is essential for effective version control.  

**The Three Areas of Git**:

- Working Directory: Where you make changes to your files.
- Staging Area (Index): Where you prepare changes before committing.
- Repository: Where your committed history is stored.

**Workflow diagram**:

    1. --make changes--> [Working Directory]
    2. --git add--> [Staging Area]
    3. --git commit--> [Repository]

| Stages | Description |
| ----- | ----- |
| Working Directory (pwd) | This is where you make changes to your files.  Think of it as your workspace or desk.  Files here can be new, modified, or deleted, but Git won't save these changes until you stage and commit them. |
| Staging Changes (git add) | When you are happy with your changes, you "stage" them with git add.  This puts your changes in the Staging Area, like putting your finished letter in an envelope. |
| Committing Changes (git commit) | Committing saves your staged changes to your local repository.  It's like mailing your letter-you can't change it after it's sent! You can also use `git commit -a -m "message"` to stage and commit all modified and deleted files in one step (but not new files). |
| Alternative - add and commit together | You can also use `git commit -a -m "message"` to stage and commit all modified and deleted files in one step (but not new files). |
| Pushing changes (git push) | After you commit, your changes are only in your local repository.  Use git push to send your commits to a remote repository (like GitHub or Bitbucket) so others can see them. |
| Checking Status (git status) | Use git status to see which files are staged, unstaged, or untracked.  This helps you keep track of what you still need to add or commit. |
| Undoing and Amending Changes | Made a mistake? Git lets you fix things before you push! See below for the related commands. |

### Undoing your changes

| Command | Action |
| ----- | ----- |
| `git restore <file>` | Undo changes in your working directory (before staging). |
| `git restore --staged <file>` | Unstage a file (move it out of the Staging Area). |
| `git reset HEAD~` | Undo your last commit (keeps changes in your working directory). |
| `git commit --amend` | Change the last commit message or add files to your last commit. |

## Git Best Practices

([top](#git-reference))

**Summary of Git Best Practices**:

- Commit Often
  - Small frequent commits make it easier to keep track and find bugs.
- Write Clear Commit Messages
  - Be specific: Say what and why, not just "Update" or "Fix".
  - Use the imperative mood: For example, "Add login validation" instead of "Added login validation".
- Use Branches
  - Create branches for features, fixes and experiments.
  - Why? Branches let you test and develop independently, and make collaboration safer.
  - Name branches clearly: For example, feature/login-form or bugfix/user-auth.
- Pull Before You Push
  - Always git pull before pushing.
  - This updates your local branch with changes from others, helps you avoid conflicts, and ensures your push will succeed.
  - Why? If someone else has pushed changes since your last pull, your push may be rejected or cause conflicts.
- Review Changes Before Committing
  - Use git status and git diff to review your changes before you commit.
  - This helps you catch mistakes early.
- Keep Repositories Small
    Avoid adding large files or unnecessary dependencies.
  - This keeps your repository fast and easy to clone.
  - Tip: For large files (*like videos or datasets*), use Git LFS (*Large File Storage*) instead of adding them directly to your repo.
- Use the .gitignore file
  - Exclude files that shouldn't be tracked (*like build artifacts, log files, or secrets*) by adding them to a .gitignore file.
  - Note: .gitignore only prevents new files from being tracked.
  - Files already tracked by Git will remain in the repository until you remove them with `git rm --cached <file>`.
- Tag Releases
  - Use tags to mark release points (*like v1.0*) so you can easily find and reference important versions.
  - This helps you keep track of your project's history and make it easier to roll back to previous versions if needed.

**Note:**

 Good Git habits make it easier for your team (*and your future self*) to understand and build on your work.

([top](#git-reference))
