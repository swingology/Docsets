# GIT SSH SETUP
@git: @github: @ssh:
``` bash
# Create a github repo on GitHub and get ssh key

# Create a github repo locally in the desired directory
git init

# Connect/sync the directory and the online github repo
git remote add <project> <ssh git address> 

# Checks which remote repository the directory is connected to 
git remote -v

# Everytime we ssh into github, we want to use the identification file id_rsa_gh_swing
https://superuser.com/questions/232373/how-to-tell-git-which-private-key-to-use
git config core.sshCommand "ssh -i ~/.ssh/id_rsa_gh_swing"

# Create master branch
git branch -M master

# List out all branches
git branch -l

# Create a file
touch file

# Upload
git add .
git commit -m "message"
git push <project> master

```
