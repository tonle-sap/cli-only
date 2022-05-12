# Mac Stuff

## Ref
https://github.com/andrewconnell/osx-install  
https://brew.sh/  
https://formulae.brew.sh/  

## Which Shell
     echo $0
    
## List user accounts
    dscl . list /Users | grep -v “^_”

## Add admin group/user to no password required for sudo
sudo vi /etc/sudoers  
    `%admin  ALL=(ALL) NOPASSWD: ALL`
    
## MacOS Software Update
    softwareupdate -l       #list updates
    softwareupdate -i NAME  #install specific update
    softwareupdate -i -a    #install all software
    
## Local  IDE Prep
### DevOps Home Dir 
    cat << EOF > /tmp/local-devops-home.sh
    #!/bin/bash
    mkdir -p ~/devops/{repos,scripts,etc}
    chmod +x /tmp/local-devops-home.sh
    EOF
    
    /tmp/local-devops-home.sh
 
### Z Shell Profile
    cat << EOF > ~/.zshrc
    export PATH=$PATH:~/devops/scripts/
    
    #Function for git mgmt - stages all, commit, and push to origin
    function gitme() {
        git add --all
        git commit -a -m "$1"
        git push
    }
    
    #Function to do brew cask install
    brew_cask_install() {
    echo "\nInstalling $1"
    if brew list $1 &>/dev/null; then
        echo "${1} is already installed"
    else
        brew install --cask \ $1 && echo "$1 is installed"
    fi
    }

    
    #Function to do brew install
    brew_install() {
    echo "\nInstalling $1"
    if brew list $1 &>/dev/null; then
        echo "${1} is already installed"
    else
        brew install \ $1 && echo "$1 is installed"
    fi
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

### Brew Install apps  
    cat << 'EOF' > /tmp/brew-apps-install.sh
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
    
    EOF
    
    chmod +x /tmp/brew-apps-install.sh && /tmp/brew-apps-install.sh

### Brew cask install
    cat << 'EOF' > /tmp/brew-apps-cask-install.sh
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
    
    chmod +x /tmp/brew-apps-cask-install.sh && /tmp/brew-apps-cask-install.sh
    
    

## Change Mac Screenshot default dumps from going to Desktop folder

    defaults write com.apple.screencapture location ~/Downloads/screenshots

## Reset shell without closing terminal

    exec zsh -l

## Set full path on Finder's bar

    defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
    killall Finder
    

    

     

## Switch between different versions of terraform

    brew install warrensbox/tap/tfswitch

 
