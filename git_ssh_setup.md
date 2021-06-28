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







## Collect the files in the array $files
files=( ~/.ssh/* )
## Enable extended globbing. This lets us use @(foo|bar) to
## match either 'foo' or 'bar'.
shopt -s extglob

## Start building the string to match against.
string="@(${files[0]}"
## Add the rest of the files to the string
for((i=1;i<${#files[@]};i++))
do
    string+="|${files[$i]}"
done
## Close the parenthesis. $string is now @(file1|file2|...|fileN)
string+=")"

## Show the menu. This will list all files and the string "quit"
select file in "${files[@]}" "quit"
do
    case $file in
    ## If the choice is one of the files (if it matches $string)
    $string)
        ## Do something here
        echo "$file"
        ## Uncomment this line if you don't want the menu to
        ## be shown again
        # break;
        ;;

    "quit")
        ## Exit
        exit;;
    *)
        file=""
        echo "Please choose a number from 1 to $((${#files[@]}+1))";;
    esac
