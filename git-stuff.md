
# Git Stuff

## The basics

    - git clone                     # Clone a repo i.e git clone git@ssh.dev.azure.com:v3/intermexteam/ITOps/coeus
    - git branch BranchName         # Creates local branch to work off from the main local branch that was clone
    - git checkout BranchName       # Checkout out the local branch to be worked on
    - git status                    # Get status of working Git directory - which changes have been track and which aren't
    - git add --all                 # Add all unstaged files to local branch
    - git commit -m "commit title"  # Commit all staged files and folders to local branch)
    - git push origin BranchName    # Pushes local "origin" branch to source code - Azure Devops
    - git branch -d BranchName      # Remove local branch

## Fetch remote branc

    git fetch --all                 # Fetch all branches
    git fetch origin BranchName     # Fetch this one branch

## Shell Stuff ~/.zshrc
    
    #Function for git mgmt - stages all, commit, and push to origin
    function gitme() {
        git add --all
        git commit -a -m "$1"
        git push
    }
 
