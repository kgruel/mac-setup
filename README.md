# New MBP Configuration

Configure Homebrew and cask upgrading

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew cask
brew tap buo/cask-upgrade
```

Allow brew installs from the App Store
```
brew install mas
```

## Terminal setup
```
mkdir .dotfiles
touch .dotfiles/.zshrc && ln -s .dotfiles/.zshrc
```
### Setup iterm2 and prompt
```
brew install iterm2
```
Configure iterm2 to have option <- and -> key bindings similar to OSX Terminal
https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x

Setup oh-my-zsh
https://gist.github.com/kevin-smets/8568070

### Useful tools
```
brew install tree wget jq
brew install zsh-completions zsh-syntax-highlighting zsh-autosuggestions
brew install thefuck && echo 'eval $(thefuck --alias)' >> .zshrc
```
## Development setup
```
mkdir ~/Code && cd ~/Code
mkdir java python js go chsarp
```

### Python
Setup basic python environment
```
brew install pyenv	
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
source ~/.zshrc
pyenv install 3.7.0
pyenv install 3.8.0
pyenv global 3.8.0
```
Set up cx_Oracle
```
touch ~/.dotfiles/.zshenv
ln -s ~/.dotfiles/.zshenv ~/.zshenv
echo 'export ORACLE_HOME=/usr/local/lib/share/oracle' >> ~/.zshenv
echo 'export DYLD_LIBRARY_PATH=$ORACLE_HOME' >> ~/.zshenv
echo 'export LD_LIBRARY_PATH=$ORACLE_HOME' >> ~/.zshenv
source ~/.zshenv
mkdir -p $ORACLE_HOME
```
```
cd $ORACLE_HOME
wget https://download.oracle.com/otn_software/mac/instantclient/193000/instantclient-basic-macos.x64-19.3.0.0.0dbru.zip
wget https://download.oracle.com/otn_software/mac/instantclient/193000/instantclient-sdk-macos.x64-19.3.0.0.0dbru.zip
tar -xvf -C . instantclient-basic-macos.x64-19.3.0.0.0dbru.zip
tar -xzf -C . instantclient-sdk-macos.x64-19.3.0.0.0dbru.zip
rm instantclient-*.zip
cd /usr/local/lib
ln -s /usr/local/lib/share/oracle libclntsh.dylib.19.1
ln -s /usr/local/lib/share/oracle libocci.dylib.19.1
```
### Java
```
brew tap adoptopenjdk/openjdk
brew cask install adoptopenjdk8 adoptopenjdk13
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

### Tools
```
brew cask install jetbrains-toolbox sublime-text postman docker sourcetree awscli dash
mas install 412536790  # Codebox
mas install 1461845568 # Gifox 2
mas install 1295203466 # Remote Desktop 10
```

## Apps
### Office
```
brew cask install slack microsoft-office openconnect 
```

### Browsers
```
brew cask install google-chrome brave-browser firefox
```

### QoL
```
brew cask install caffeine shuttle bartender 
mas install 441258766  # Magnet
```

### Rest
```
brew tap homebrew/cask-drivers
brew cask install telegram spotify tweetbot sonos kindle calibre steam discord
```
