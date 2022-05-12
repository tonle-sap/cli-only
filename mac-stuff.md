# Mac Stuff
Ref
    https://github.com/andrewconnell/osx-install
    https://brew.sh/

## MacOS Software Update

    softwareupdate -l       #list updates
    softwareupdate -i NAME  #install specific update
    softwareupdate -i -a    #install all software
    
## Homebrew
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    

## Change Mac Screenshot default dumps from going to Desktop folder

    defaults write com.apple.screencapture location ~/Downloads/screenshots

## Reset shell without closing terminal

    exec zsh -l

## Set full path on Finder's bar

    defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
    killall Finder
    

## Tree

    brew install tree
    

## Shell Stuff ~/.zshrc

    export PATH=$PATH:~/devops/scripts/
    
    #Function for git mgmt - stages all, commit, and push to origin
    function gitme() {
        git add --all
        git commit -a -m "$1"
        git push
    }


## Switch between different versions of terraform

    brew install warrensbox/tap/tfswitch

 
