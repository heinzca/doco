# Git Config

Use:  
--global to set values for all repositories; or  
--local to set values for the current repository only  


| Command | Action |
| ----- | ----- |
| git config --global user.name "Your Name" | Configure your user name|
| git config --global user.email "you@example.com" | Configure your email address|
| git config --list | See all of your git config settings |
| git config user.name | See a specific value - define it. e.g. user.name |
| run same git config command with new value | To replace an existing value |
| git config --global --unset global user.name | To unset a specific value use the --unset tag |
| git config --global init.defaultBranch main | Set the default branch to the defined value. e.g. "main" in this isntance |
| git config user.name "Project Name" | Set a local user name config |
| git config --global user.name "Global Name"| Set a global user name config |
| git config --system user.name "System Name" | Set a system user name config |

<br><br>

# Initialize a Git Directory

- A Git repository is a folder that Git tracks for changes.  
- The repository stores all your project's history and versions.  
- When you run git init, git creates a hidden folder '.git' where all info for the git repository is stored.  

<br>

| Command | Action |
| ----- | ----- |
| mkdir myproject| Create the project directory |
| cd myproject | Change directory to new project |
| git init | Initialize the git directory |

<br><br>

# Git Staging

| Command | Action |
| ----- | ----- |
| git add filename.md | Stage a single file called filename.md |
| git add --all or git add -A | Stage all changes - multiple files|
| git add . | Stage all files in current directory |
| git status | See what has changed |
| git restore --staged <file> | Un-stage a file (fails if no prior commits)|
| git rm --cached <file> | Alternative un-stage |

<br><br>

# Git Commit

| Command | Action |
| ----- | ----- |
| git commit -m "message" | Commit staged changes with a message |
| git commit -a -m "message" | Commit all tracked changes without staging + message. Be careful. Can commit unwanted changes. |
| git commit | Commit with prompt for message. Allows multi line messages via text editor |
| git commit --allow-empty -m "message" | Commit an empty project with a message - useful for initiating a new project |
| git commit --amend -m "corrected message" | Add a file to last commit. git add first, then amend with updated message |
| git commit --amend --no-edit | Add a file to last commit. git add first, but keeps original message |
| git log | View commit history. Show a log of all commits |
| git log --oneline | Show a log of all commits -> one per line|
| git log --stat | Show which files changed in each commit|
| git reset --soft HEAD~1 | Undo the last commit and keep your changes staged |

<br><br>

# Git Tagging

| Command | Action |
| ----- | ----- |
| git tag v1.0 | Add a simple name / tag for a commit |
| git tag -a v1.0 -m "Version 1.0 release" | An annotated tag also stores your name, the date, and a message. |
| git tag v1.1 bb3ecbd | Tag a specific commit |
| git tag | List all tags in your repository |
| git show v1.0 | See details about a tag and the commit it points to |
| git push origin v1.0 | Push a specific tag to remote repository |
| git push --tags | Push all your local tags to the remote at once (useful if you've created several tags) |
| git tag -d v1.0 | Delete a tag locally |
| git push origin --delete tag v1.0 | Delete a tag from the remote repository |
| git tag -f v1.0 <new-commit-hash> | Move a tag to a different commit (-f is force); and |
| git push --force origin v1.0 | Push the update to remote |

<br><br>

## Tagging Best Practices

- Use tags to mark releases, major milestones, or stable points in your project.  
- Always use annotated tags (with -a -m) for anything public or shared.  
- Create tags after passing all tests or before deploying/releasing code.  

<br><br>

## Tagging Troubleshooting


- Tag already exists? Use git tag -d <tagname> to delete it, then re-create.  
- Pushed the wrong tag? Delete it locally and remotely, then push the correct tag.  
- Tag not showing on remote? Remember to push tags with git push origin <tagname> or git push --tags.  
- Need to overwrite a tag on the remote? You can force-push a tag with git push --force origin <tagname>, but be careful! This will overwrite the tag for everyone using the remote.  

<br><br>

# Git Stash

| Command | Action |
| ----- | ----- |
|  |  |

<br><br>

# Git Template
| Command | Action |
| ----- | ----- |
|  |  |

<br><br>
