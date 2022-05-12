# Mac Stuff
Ref
    https://github.com/andrewconnell/osx-install  
    https://brew.sh/
    
## List user accounts
    dscl . list /Users | grep -v “^_”

## Add admin group/user to no password required for sudo
sudo vi /etc/sudoers  
    `%admin  ALL=(ALL) NOPASSWD: ALL`
    
## MacOS Software Update

    softwareupdate -l       #list updates
    softwareupdate -i NAME  #install specific update
    softwareupdate -i -a    #install all software
    
## Mac Apple Store
    brew install mas
    # get Apple ID
    echo ""
    echo "Enter AppleID to signin to Mac App Store:"
    read -p "  AppleID (virath@gmail.com): " APPLEID

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
    --cask iterm2 \
    --cask firefox \
    --cask microsoft-edge \
    --cask google-chrome \
    --cask visual-studio-code \
    --cask postman \
    --cask slack \
    --cask zoom \
    --cask microsoft-teams \
    --cask virtualbox \
    --cask cyberduck \
    --cask wireshark \
    --cask dbeaver-community \
    --cask lastpass \

    
    
    

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

 
