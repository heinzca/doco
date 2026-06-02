
# GitHub

[Back to README](README.md)

**Sub-headings:**

- [Getting Started](#getting-started)
- [Git Security SSH](#git-security-ssh)
- [Add SSH to GitHub](#add-ssh-to-github)
- [Git Set Remote from GitHub](#git-set-remote-from-github)
- [Edit Directly in GitHub](#edit-directly-in-github)
- [Pull from GitHub](#pull-from-github)
- [Push to GitHub](#push-to-github)
- [GitHub Branches](#github-branches)
- [Pull Remote Branch from GitHub](#pull-remote-branch-from-github)
- [Push a Branch to GitHub](#push-a-branch-to-github)
- [GitHub Flow](#github-flow)

## Getting Started

([top](#github))

1. Go to [github.com](https://github.com/) and sign-up for a free account.
2. Create a new repository.
3. What is a remote repository?
    - A remote repository is a version of your project hosted on the internet.
    - GitHub is a popular platform for hosting remote repositories, enabling you to collaborate with others and back up your code.

## Git Security SSH

([top](#github))

SSH (Secure Shell) is a way to connect securely to remote computers and services, like Git repositories.

SSH uses a pair of keys (public and private) to make sure only you can access your code.

### Summary of SSH Concepts and Commands

| Item | Description |
| ----- | ----- |
| SSH key pair | A public and private key for secure access |
| `ssh-keygen` | Generate a new SSH key pair |
| `ssh-add` | Add your private key to the SSH agent |
| `ssh -T git@github.com` | Test SSH connection |
| `ssh-add -l` | List loaded SSH keys |
| `ssh-add -d` | Remove a key from agent |

### How SSH Keys Work

SSH keys come in pairs: a public key (like a lock) and a private key (like your own key).

You share the public key with the server (like GitHub or Bitbucket), but keep the private key safe on your computer.

Only someone with the private key can access what's locked by the public key.

### First-Time SSH Key Setup

If you've never used SSH keys before, follow this step to enable the SSH agent on your operating system:  

`eval $(ssh-agent -s)`

### Generating an SSH Key Pair

To create a new SSH key pair, use this command in the terminal (Linux, macOS, or Git Bash for Windows):  

`h-keygen -t rsa -b 4096 -C "your@email.com"`

### Adding Your Key to the SSH Agent

After creating your key, add it to the SSH agent so Git can use it:

`ssh-add ~/.ssh/id_rsa`

### Copying Your Public Key

To use SSH with Git hosting services, you need to copy your public key and add it to your account settings on GitHub, GitLab, or Bitbucket.

- On macOS: pbcopy < ~/.ssh/id_rsa.pub
- On Windows (Git Bash): clip < ~/.ssh/id_rsa.pub
- On Linux: cat ~/.ssh/id_rsa.pub (then copy manually)

### Listing and Removing SSH Keys

See which keys are loaded in your SSH agent:

`ssh-add -l`

### Remove SSH Key from Agent

`ssh-add -d ~/.ssh/id_rsa`

## Add SSH to GitHub

([top](#github))

Now that you have generated your SSH key, you need to add your public key to your GitHub account.

### Copy Your Public SSH Key

- On Windows (Git Bash): clip < ~/.ssh/id_rsa.pub
- On macOS: pbcopy < ~/.ssh/id_rsa.pub
- On Linux: cat ~/.ssh/id_rsa.pub (then copy manually)

### Add the Key to GitHub

1. Go to GitHub, click your profile in the top right, and select Settings.
2. In the sidebar, select SSH and GPG keys and click the New SSH key button.
3. Give your key a descriptive title, paste your public SSH key into the "Key" field, and click Add SSH Key.
    - You may be prompted to supply your GitHub password or use 2FA to confirm the addition.
    - You will see your new SSH key listed

## Git Set Remote from GitHub

([top](#github))

Now that your SSH key is added to GitHub, you can securely connect your local repository to GitHub using SSH.

### Test Your SSH Connection

First, test that your SSH connection to GitHub works:  
`ssh -T git@github.com`

If the last line of the response contains your username on GitHub - all is good.

### Get Your Repository's SSH Address

On GitHub, go to your repository and click the Code button. Make sure SSH is selected, then copy the SSH URL (it starts with `git@github.com:`)

### Add or Update the Remote Origin

To add the remote origin (first time):  
`git remote add origin git@github.com:your-username/your-repo.git`

To update an existing remote to use SSH:  
`git remote set-url origin git@github.com:your-username/your-repo.git`

## Edit Directly in GitHub

([top](#github))

### Edit any File

- GitHub lets you edit files directly in your browser.
- This is useful for making quick changes without needing to use Git on your computer.
- To edit a file (like README.md), click the file name in your repository, then click the Edit button (pencil icon).
- Make changes to the file in the editor. (You can edit any file, not just README.md.)
- Before saving, you can click Preview changes to see what will change in the file.
- This helps you check your edits before committing.

### Commit Changes

- After editing scroll down and 'Commit Changes'.
- Add a message if it requires explanation.
- By default, you can commit directly to the main (or master) branch.
- For bigger changes, it's best to create a new branch.
- Select Create a new branch for this commit and start a pull request to work safely.
- When you choose to create a new branch, GitHub will automatically suggest a branch name.
- After committing, you can open a pull request to propose your changes.

## Pull from GitHub

([top](#github))

### Pull from Remote

After making changes directly on GitHub, we want to update our local repository with those changes.

Key pull commands:

- [Fetch](#git-fetch)
- [Merge](#git-merge)
- [Pull](#git-pull)

### Fetch, Pull and Merge

When working as a team on a project, it is important that everyone stays up to date.

Any time you start working on a project, you should get the most recent changes to your local copy.

With Git, you can do that with pull.

pull is a combination of 2 different commands:

- fetch
- merge

Let's take a closer look into how fetch, merge, and pull works.

### Git Fetch

git fetch downloads new data from a remote repository, but does not change your working files or branches. It lets you see what others have pushed before you merge or pull.

- `git fetch origin`

This shows whether any changes have been fetched.

Follow this up with a:

- `git status`

This should show how far behind you are on origin, and next instructions.

You can check the log from origin / main via:

- `git log origin/main`

This would show any commits made on the remote, which we don't yet have locally.

You can check the diff between local and origin via:

- `git diff origin/main`

If changes are as expected, you can safely merge.

### Git Merge

merge combines the current branch, with a specified branch.

We can merge our current branch 'main' with 'origin/main' via:

- `git merge origin/main`

Follow up with a git status to confirm you are now clean and up to date with origin/main.

### Git Pull

If you just want to update your local repository, without going through all those steps, then pull is a combination of fetch and merge.

It is used to pull all changes from a remote repository into the branch you are working on.

If you had a change on the main branch directly on GitHub, then ran the following locally:

- `git pull origin`

It completes the equivalent of both 'fetch' and 'merge' to bring your local into synch with the remote repository.

## Push to GitHub

([top](#github))

When we have made changes locally, we want to update our remote repository with the changes.

Transferring our local changes to our remote is done with a push command.

The key push commands are:

- Basic Push
- Force Push
- Push Tags

### Basic

This command pushes your current branch to the remote repository named origin:

- `git push origin`

This will upload your local commits to GitHub.

You must have already committed your changes with git commit.

### Force

If your push is rejected due to non-fast-forward updates (for example, after a rebase), you can force the push.

**Warning**: This can overwrite changes on the remote repository. Use with caution!

- `git push --force origin feature-branch`

Use --force-with-lease for a safer force push:

- `git push --force-with-lease origin feature-branch`

### Tags

To push all local tags to GitHub:

- `git push --tags`

To push a specific tag, name that tag in the push:

- `git push origin v1.0`

## GitHub Branches

([top](#github))

### Create Branch on Github UI

([top](#github))

On GitHub, access your repository and click the "master" / "main" branch button.

There you can create a new Branch. Type in a descriptive name, and click Create branch

The branch should now be created and active. You can confirm which branch you are working on by looking at the branch button.

You can make changes to a file in context of the new branch.

You can preview, then commit changes to the branch.

To create and immediately switch to the branch via command line:

- `git switch -c branch-name`
- `git checkout -b branch-name`

### Switch Branch

([top](#github))

To switch to another branch in GitHub's web interface, click the branch dropdown and select the branch you want to work on.

To switch branches using the command line:

- `git switch branch-name`
- `git branch branch-name`

### Delete Branch

([top](#github))

To delete a branch on GitHub, go to the branches page, find your branch, and click the delete icon (trash can).

To delete a branch using the command line:

- `git branch -d branch-name`

To delete a remote branch:

- `git push origin --delete branch-name`

### Rename Branch

([top](#github))

To rename a branch using the command line:

- `git branch -m old-name new-name`

### Merge Branch

([top](#github))

To merge a branch into another on GitHub, open a Pull Request (PR) and follow the prompts to merge.

To merge using the command line:

- `git merge branch-name`

### View Branches

([top](#github))

To see all branches in your repository on GitHub, click the branch dropdown at the top of the file list.

To view branches using the command line:

- `git branch`

### Protected Branches

([top](#github))

Some branches (like main) may be protected, meaning you cannot delete or force-push to them without special permissions.

This helps prevent accidental changes to important branches.

## Pull Remote Branch from Github

([top](#github))

### Pull a Remote Branch

([top](#github))

Firstly run a general `git pull`. This will show any changes on the remote, including whether any new remote branches exists.

`git status` should show the state of your current branch.

### Git Branch

([top](#github))

- `git branch` may not show the new branch on the remote on our local git yet.
- We can use the -a option to see all local and remote branches:
  - `git branch -a`
- To view only remote branches:
  - `git branch -r`
- Checkout the remote branch:
  - `git checkout branch-name`
- Then run a `git pull` to see if we are up to date with the remote.
- `git branch` should then show the remote branch in our local git.

## Push a Branch to Github

([top](#github))

### Push a local branch up to GitHub

Firstly create your new branch locally, make changes, then commit your changes.

Push your branch to GitHub via:

- `git push origin branch-name`

You should then be able to see the branch on GitHub.

### Push and Set Upstream

Use this if your branch doesn't exist on GitHub yet, and you want to track it:

- `git push --set-upstream origin update-readme`

### Force Push

**Warning**: This overwrites the branch on GitHub with your local changes. Only use if you understand the risks.

- `git push --force origin update-readme`

### Delete Remote Branch

Remove a branch from GitHub:

- `git push origin --delete update-readme`

### Push All Branches

Push all your local branches to GitHub:

- `git push --all origin`

### Push Tags

Push all your tags to GitHub:

- `git push --tags`

## GitHub Flow

([top](#github))

The GitHub Flow is a simple, effective workflow for collaborating on code using Git and GitHub.

It helps teams work together smoothly, experiment safely, and deliver new features or fixes quickly.

Here's how the GitHub Flow works, step by step:

- **Create a Branch**: Start new work without affecting the main code.
- **Make Commits**: Save progress as you make changes.
- **Open a Pull Request**: Ask others to review your work.
- **Review**: Discuss and improve the changes together.
- **Deploy**: Test your changes before merging.
- **Merge**: Add your finished work to the main branch.

This workflow is designed to be easy for beginners and powerful for teams of any size.

### Create a New Branch

- Branching is the key concept in Git. And it works around the rule that the master branch is ALWAYS deployable.
- That means, if you want to try something new or experiment, you create a new branch!
- Branching gives you an environment where you can make changes without affecting the main branch.
- When your new branch is ready, it can be reviewed, discussed, and merged with the main branch when ready.
- When you make a new branch, you will (almost always) want to make it from the master branch.

**Note**:

- Keep in mind that you are working with others.
- Use descriptive names for new branches, so everyone can understand what is happening.

### Make Changes and Add Commits

- After the new branch is created, it is time to get to work.
- Make changes by adding, editing and deleting files.
- Whenever you reach a small milestone, add the changes to your branch by commit.
- Adding commits keeps track of your work.
- Each commit should have a message explaining what has changed and why.
- Each commit becomes a part of the history of the branch, and a point you can revert back to if you need to.

**Note**:

- Commit messages are very important! Let everyone know what has changed and why.
- Messages and comments make it so much easier for yourself and other people to keep track of changes.

### Open a Pull Request

- Pull requests are a key part of GitHub.
- A Pull Request notifies people you have changes ready for them to consider or review.
- You can ask others to review your changes or pull your contribution and merge it into their branch.

### Review

- When a Pull Request is made, it can be reviewed by whoever has the proper access to the branch.
- This is where good discussions and review of the changes happen.
- Pull Requests are designed to allow people to work together easily and produce better results together!
- If you receive feedback and continue to improve your changes, you can push your changes with new commits, making further reviews possible.

**Note**:

- GitHub shows new commit and feedback in the "unified Pull Request view".

### Deploy

- When the pull request has been reviewed and everything looks good, it is time for the final testing.
- GitHub allows you to deploy from a branch for final testing in production before merging with the master branch.
- If any issues arise, you can undo the changes by deploying the master branch into production again!

**Note**:

- Teams often have dedicated testing environments used for deploying branches.

### Merge

- After exhaustive testing, you can merge the code into the master branch!
- Pull Requests keep records of changes to your code, and if you commented and named changes well, you can go back and understand why changes and decisions were made.

**Note**:

- You can add keywords to your pull request for easier searching!

([top](#github))
