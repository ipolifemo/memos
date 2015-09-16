make me a sudo

```
sudo su -
touch /etc/sudoers.d/polifemo
echo 'ipolifemo ALL=(ALL) NOPASSWD:ALL'
```

git and prereq

```
sudo apt-get install git-core
sudo apt-get install build-essential
sudo apt-get install -y libssl-dev libreadline-dev zlib1g-dev
```

awscli
```
sudo apt-get install python-pip 
sudo pip install awscli
awscli configure (get crodentials from IAM)
```

- get backups
- install auths
- install fonts

```
mkdir .ssh
# copy certs
chmod 700 .ssh
chmod 600 .ssh/*
chmod 644 .ssh/*.pub
```

zsh

```
sudo apt-get install zsh
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
chsh -s `which zsh`
sudo shutdown -r 0
```

tmux and vim

```
sudo add-apt-repository -y ppa:pi-rho/dev
sudo apt-get update
sudo apt-get install -y tmux=2.0-1~ppa1~t
git clone https://github.com/jimeh/tmuxifier.git ~/.tmuxifier
# add $HOME/.tmuxifier/bin to PATH
# add eval "$(tmuxifier init -)" to zshrc
# export TMUXIFIER_LAYOUT_PATH="$HOME/.tmux-layouts"
sudo apt-get install vim
# because the clipper:
sudo apt-get install vim-gtk
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

rbenv
```
git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
```

dot files
```
cd ~
git clone git@github.com:ipolifemo/dots.git 
cd dots
make terminal
```

post build: install vim plugins calling :PlugInstall

fancy the terminal

(Make sure to backup default theme before applying solarized

```
sudo apt-get install dconf-cli
git clone https://github.com/Anthony25/gnome-terminal-colors-solarized.git term-solar
cd term-solar
./install
```

fancy the desktop
```
sudo apt-get install compizconfig-settings-manager
sudo apt-get install unity-tweak-tool
```

- ambiance
- disable effects using compizconf
- set a desktop gradient background pleaseee!
- set fonts with unity-tweak-tool. I like them cute:
  - default: Graphik Medium 10
  - document: Graphik Medium 11
  - monospace: Souce Code Pro w/ Powerline Semi-Bold 10
  - title: Graphik Semi-Bold 9

flux the screen

```
sudo add-apt-repository -y ppa:kilian/f.lux
sudo apt-get update
sudo apt-get install -y fluxgui
```
