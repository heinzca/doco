# GitHub
<div style="text-align: left; font-size: small;">

[Back to README](README.md)

</div>

**Sub-headings:**
- [Getting Started](#getting-started)
- [Git Security SSH](#git-security-ssh)
- [Add SSH to GitHub](#add-ssh-to-github)
- [Git Set Remote from GitHub](#git-set-remote-from-github)
- [Edit Directly in GitHub](#edit-directly-in-github)
- []()
- []()
- []()
- []()
- []()
- []()


## Getting Started
([top](#github))

1. Go to [github.com](https://github.com/) and sign-up for a free account.
2. Create a new repository.
3. What is a remote repository?
    - A remote repository is a version of your project hosted on the internet.
    - GitHub is a popular platform for hosting remote repositories, enabling you to collaborate with others and back up your code.

<br>

## Git Security SSH
([top](#github))

SSH (Secure Shell) is a way to connect securely to remote computers and services, like Git repositories.

SSH uses a pair of keys (public and private) to make sure only you can access your code.

<br>

### Summary of SSH Concepts and Commands

| Item | Description |
| ----- | ----- |
| SSH key pair | A public and private key for secure access |
| `ssh-keygen` | Generate a new SSH key pair |
| `ssh-add` | Add your private key to the SSH agent |
| `ssh -T git@github.com` | Test SSH connection |
| `ssh-add -l` | List loaded SSH keys |
| `ssh-add -d` | Remove a key from agent |


<br>

### How SSH Keys Work

SSH keys come in pairs: a public key (like a lock) and a private key (like your own key).

You share the public key with the server (like GitHub or Bitbucket), but keep the private key safe on your computer.

Only someone with the private key can access what's locked by the public key.

<br>

### First-Time SSH Key Setup
If you've never used SSH keys before, follow this step to enable the SSH agent on your operating system:  

`eval $(ssh-agent -s)`

<br>

### Generating an SSH Key Pair

To create a new SSH key pair, use this command in the terminal (Linux, macOS, or Git Bash for Windows):  

`h-keygen -t rsa -b 4096 -C "your@email.com"`

<br>

### Adding Your Key to the SSH Agent

After creating your key, add it to the SSH agent so Git can use it:

`ssh-add ~/.ssh/id_rsa`

<br>

### Copying Your Public Key

To use SSH with Git hosting services, you need to copy your public key and add it to your account settings on GitHub, GitLab, or Bitbucket.

- On macOS: pbcopy < ~/.ssh/id_rsa.pub
- On Windows (Git Bash): clip < ~/.ssh/id_rsa.pub
- On Linux: cat ~/.ssh/id_rsa.pub (then copy manually)

<br>

### Listing and Removing SSH Keys

See which keys are loaded in your SSH agent:

`ssh-add -l`

<br>

### Remove SSH Key from Agent

`ssh-add -d ~/.ssh/id_rsa`

<br>

## Add SSH to GitHub
([top](#github))

Now that you have generated your SSH key, you need to add your public key to your GitHub account.

### Copy Your Public SSH Key

- On Windows (Git Bash): clip < ~/.ssh/id_rsa.pub
- On macOS: pbcopy < ~/.ssh/id_rsa.pub
- On Linux: cat ~/.ssh/id_rsa.pub (then copy manually)

<br>

### Add the Key to GitHub

1. Go to GitHub, click your profile in the top right, and select Settings.
2. In the sidebar, select SSH and GPG keys and click the New SSH key button.
3. Give your key a descriptive title, paste your public SSH key into the "Key" field, and click Add SSH Key.
    - You may be prompted to supply your GitHub password or use 2FA to confirm the addition.
    - You will see your new SSH key listed

<br>

## Git Set Remote from GitHub
([top](#github))

Now that your SSH key is added to GitHub, you can securely connect your local repository to GitHub using SSH.

<br>

### Test Your SSH Connection

First, test that your SSH connection to GitHub works:  
`ssh -T git@github.com`

If the last line of the response contains your username on GitHub - all is good.

<br>

### Get Your Repository's SSH Address

On GitHub, go to your repository and click the Code button. Make sure SSH is selected, then copy the SSH URL (it starts with git@github.com:)

<br>

### Add or Update the Remote Origin

To add the remote origin (first time):  
`git remote add origin git@github.com:your-username/your-repo.git`

To update an existing remote to use SSH:  
`git remote set-url origin git@github.com:your-username/your-repo.git`

<br>

## Edit Directly in GitHub
([top](#github))

### Edit any File

- GitHub lets you edit files directly in your browser.
- This is useful for making quick changes without needing to use Git on your computer.
- To edit a file (like README.md), click the file name in your repository, then click the Edit button (pencil icon).
- Make changes to the file in the editor. (You can edit any file, not just README.md.)
- Before saving, you can click Preview changes to see what will change in the file.
- This helps you check your edits before committing.

<br>

### Commit Changes

- After editing scroll down and 'Commit Changes'.
- Add a message if it requires explanation.
- By default, you can commit directly to the main (or master) branch.
- For bigger changes, it's best to create a new branch.
- Select Create a new branch for this commit and start a pull request to work safely. 
- When you choose to create a new branch, GitHub will automatically suggest a branch name.
- After committing, you can open a pull request to propose your changes.

<br>

## Pull from GitHub
([top](#github))

### Pull from Remote

After making chnages directly on GitHub, we want to update our local repository with those changes.

Key pull commands:
- [Fetch](#git-fetch)
- [Merge](#git-merge)
- [Pull](#git-pull)

<br>

### Fetch, Pull and Merge

When working as a team on a project, it is important that everyone stays up to date.

Any time you start working on a project, you should get the most recent changes to your local copy.

With Git, you can do that with pull.

pull is a combination of 2 different commands:

    - fetch
    - merge

Let's take a closer look into how fetch, merge, and pull works.

<br>

### Git Fetch



### Git Merge



### Git Pull



