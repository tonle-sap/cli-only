# Mac Stuff

## Ref
https://github.com/andrewconnell/osx-install  
https://brew.sh/  
https://formulae.brew.sh/  
    
## List user accounts
    dscl . list /Users | grep -v “^_”

## Add admin group/user to no password required for sudo
sudo vi /etc/sudoers  
    `%admin  ALL=(ALL) NOPASSWD: ALL`
    
## MacOS Software Update
    softwareupdate -l       #list updates
    softwareupdate -i NAME  #install specific update
    softwareupdate -i -a    #install all software
    
## Local DevOps Home Dir  
    cat << EOF > /tmp/local-devops-home.sh
    #!/bin/bash
    mkdir -p ~/devops/{repos,scripts,etc}
    chmod +x /tmp/local-devops-home.sh
    EOF
    
    /tmp/local-devops-home.sh
    
    cat << EOF > ~/.zshrc
    export PATH=$PATH:~/devops/scripts/
    
    #Function for git mgmt - stages all, commit, and push to origin
    function gitme() {
        git add --all
        git commit -a -m "$1"
        git push
    }
    EOF
    
    exec zsh -l
    
    
    
## Mac Apple Store
    brew install mas
    # get Apple ID
    echo ""
    echo "Enter AppleID to signin to Mac App Store:"
    read -p "  AppleID (foo@foo.com): " APPLEID

    # make sure signed into Mac App Store
    mas signin $APPLEID
    
    # install macos apps
    mas install 715464874 # Disk Map
    mas install 524141863 # Jump Desktop
    mas install 823766827 # OneDrive
    mas install 497799835 # Xcode
    
## Homebrew
### Installation
    NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/{user_folder}/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
    brew update
    brew -v

### Install apps
    cat << 'EOF' > /tmp/brew-apps-install.sh
    #!/bin/bash
    brew install \
    mtr \
    telnet \
    tree \
    cask \
    jq \
    azure-cli \
    awscli \
    git \
    terraform \
    terraform-docs \
    terragrunt \
    go \
    python-tk@3.10 \
    
    brew install --cask \
    iterm2 \
    firefox \
    microsoft-edge \
    google-chrome \
    visual-studio-code \
    atom \
    postman \
    slack \
    zoom \
    microsoft-teams \
    virtualbox \
    cyberduck \
    wireshark \
    dbeaver-community \
    lastpass \
    EOF
    
    chmod +x /tmp/brew-apps-install.sh
    
    

## Change Mac Screenshot default dumps from going to Desktop folder

    defaults write com.apple.screencapture location ~/Downloads/screenshots

## Reset shell without closing terminal

    exec zsh -l

## Set full path on Finder's bar

    defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
    killall Finder
    

## Tree

    brew install tree
    
## Which Shell
     echo $0
     
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

 
