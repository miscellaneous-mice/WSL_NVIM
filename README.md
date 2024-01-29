# WSL_NVIM
Using NVIM on WSL-Debian

## Installtion of WSL
- Follow these steps on powershell/command prompt
```
# wsl --install -d Debian
```
- Download this [distro](https://apps.microsoft.com/detail/9MSVKQC78PK6?hl=en-US&gl=US)

## Using ZSH
- Install zsh and dependencies
```
$ sudo apt-get install zsh wget
```
- we need to make it our default shell
```
$ sudo usermod $USER -s /usr/bin/zsh
$ logout
```
- Install Oh-my-zsh
```
$ touch ~/.zshrc
$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
- Installating useful plugins for zsh
```
$ cd ~/.oh-my-zsh/plugins
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
$ git clone https://github.com/zsh-users/zsh-completions ~/.oh-my-zsh/custom/plugins/zsh-completions
```
- Copy the basic zsh configurations
```
$ git clone https://github.com/miscellaneous-mice/WSL_NVIM.git
$ cp /dir/to/repo/WSL_NVIM/.zshrc ~/
```
- Apply your zsh configuration
```
$ source ~/.zshrc
```
- [Installtion guide](https://computingforgeeks.com/how-to-install-and-configure-zsh-shell-on-linux/?expand_article=1)

## Installation of browser
```
$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

## Installtion of neovim and turning into a ide
- First git clone the repo. Installtion guide is give [here](https://github.com/neovim/neovim/blob/master/INSTALL.md#install-from-source)
```
$ git clone https://github.com/neovim/neovim.git
$ cd neovim
$ make CMAKE_BUILD_TYPE=RelWithDebInfo
$ sudo make install
```
- To uninstall neovim
```
$ sudo cmake --build build/ --target uninstall
```
- Uninstall current python on your system
```
$ sudo apt-get clean
$ sudo apt-get autoremove --purge
$ sudo apt-get remove python3.x python3 python3.x-minimal python3-minimal
$ sudo apt-get autoremove
```
- Install python from source. Installation guide is given [here](https://itslinuxfoss.com/how-to-install-python-on-debian-12/)
```
$ wget https://www.python.org/ftp/python/3.xx.x/Python-3.xx.x.tgz
$ tar -xf Python-3.xx.x.tgz
$ cd Python-3.xx.x && ./configure --enable-optimizations
$ make -j 12
$ sudo make install
```
- Install nodejs. Installtion guide is given [here](https://www.rosehosting.com/blog/how-to-install-node-js-and-npm-on-debian-11/)
```
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | zsh
$ source ~/.zshrc
$ nvm install node
$ node -v
$ npm -v
```
- Copy all the configurations
```
$ mkdir ~/Backup
$ mv ~/.config/nvim ~/Backup
$ git clone https://github.com/miscellaneous-mice/WSL_NVIM.git
$ cp -r nvim ~/.config/
```
- Some extra commands to get the neovim working. Inside Neovim
```
:Mason
```
