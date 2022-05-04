Change Mac Screenshot default dumps from goign to Desktop folder <p>
```$ defaults write com.apple.screencapture location /some-path/```

Reset shell without closing terminal <p>
```exec zsh -l```

Set full path on Finder's bar
```
defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
killall Finder
```
  
Tree <p>
`brew install tree`
  
~/.zshrc
```
export PATH=$PATH:~/devops/scripts/

#Function for git mgmt - stages all, commit, and push to origin
function gitme() {
    git add --all
    git commit -a -m "$1"
    git push
}
```

  
switch between different versions of terraform <p>
```brew install warrensbox/tap/tfswitch```

 
