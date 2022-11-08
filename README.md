# New MBP Configuration

## Install Homebrew
Install `homebrew` and `mas` to allow app store installations

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install mas
```

## Terminal setup (with oh-my-zsh)
```
brew install iterm2
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
mkdir .dotfiles && ln -s .dotfiles/.zshrc
mv .oh-my-zsh .dotfiles/.oh-my-zsh && sed -i '' 's;/.oh-my-zsh;/.dotfiles/.oh-my-zsh;g' .dotfiles/.zshrc
```

### Add powerlevel10k theme
```
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
sed -i '' 's;robbyrussell;powerlevel10k/powerlevel10k;g' .dotfiles/.zshrc
mv .pk10k.zsh .dotfiles/ && sed -i '' 's;.p10k.zsh;.dotfiles/.p10k.zsh;g' .dotfiles/.zshrc
```
Quit iTerm2 with `⌘Q` and start again. The powerlevel10k configuration will automatically load. There are quite a few options, it will take a few minutes.

### Install plugins
```
brew install zsh-autosuggestions zsh-syntax-highlighting thefuck
curl https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/jsontools/jsontools.plugin.zsh >> $ZSH_CUSTOM/plugins/jsontools.plugin.zsh
sed -i '' 's;(git);(git zsh-autosuggestions jsontools macos);g' .dotfiles/.zshrc && echo 'eval $(thefuck --alias --enable-experimental-instant-mode)' >> .zshrc && echo 'source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh' >> .zshrc && source .zshrc
```

* https://github.com/zsh-users/zsh-autosuggestions
* https://github.com/zsh-users/zsh-syntax-highlighting
* https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/jsontools
* https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/macos
* https://github.com/nvbn/thefuck

### Enable natural text editing in iTerm2
By default, word jumps (option + → or ←) and word deletions (option + backspace) do not work. To enable these, go to "iTerm → Preferences → Profiles → Keys → Key mappings → Presets... → Natural Text Editing"


## Install apps

### Useful tools
```
brew install jetbrains-toolbox sublime-text postman docker awscli
```

### General apps
```
brew install telegram spotify kindle calibre steam discord tweeten tradingview adobe-acrobat-reader pocket-casts nordvpn
```

### QoL Apps
```
brew install intellidock shuttle bartender caffeine
```

### App store apps (Apple ID dependent)
```
mas install 1615798039  # Read-Kit
mas install 441258766   # Magnet
```

### Force Spotlight to reindex
```
sudo mdutil -E /
```


## Development setup
```
mkdir ~/Code && cd ~/Code
mkdir java python js go ruby markdown
```

### Python
```
brew install pyenv	
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> .zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> .zshrc
echo 'eval "$(pyenv init -)"' >> .zshrc
source .zshrc
pyenv install 3.10.8 && pyenv install 3.11.0 && pyenv install 3.9.15
pyenv global 3.11.0
curl -sSL https://install.python-poetry.org | python3 -
echo 'export PATH="/Users/kaygee/.local/bin:$PATH"' >> .zshrc
source .zshrc
```

### Java
```
brew install temurin
brew install maven
```

### Javascript
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
source ~/.zshrc
nvm install node
nvm install 10.17.0
```

### Go
```
brew install golang
```

### Ruby
```
brew install ruby
```
