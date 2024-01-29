# WSL_NVIM
Using NVIM on WSL-Debian

![WSL_Rice_2](https://github.com/miscellaneous-mice/WSL_NVIM/assets/79500624/1aca77dc-9e0d-46c0-8bfa-228d701e9a31)


## Installtion of WSL
- Follow these steps on powershell/command prompt
```
# wsl --install -d Debian
```
- Download this [distro](https://apps.microsoft.com/detail/9MSVKQC78PK6?hl=en-US&gl=US)

## Installation of basic-utils
```
$ sudo apt update && sudo apt upgrade -y
$ sudo apt-get dist-upgrade
$ sudo apt-get install xz-utils unzip thunar
$ sudo apt-get install ninja-build build-essential cmake g++ gcc
$ sudo apt-get install wget curl git
$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
$ sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Using ZSH
- Install zsh and dependencies
```
$ sudo apt-get install zsh
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

## Ricing the terminal
- Install the Mononoki nerd font
  - Download using this [link](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/Mononoki.zip). Then unzip this fonts folder
  - In Windows settings -> Personalization -> Fonts -> Browse and Install Fonts -> Select all the fonts in the unzipped folder
- Change the color of windows terminal -> Settings -> Defaults -> Appearance -> Colorscheme -> One Half Dark
- Change the font of windows terminal -> Settings -> Defaults -> Appearance -> Font Face -> Select Mononoki Nerd font (Select the "Font weight" : Bold)
- Install TMUX inside WSL
```
$ sudo apt-get install tmux
```
- You can find the shortcuts of TMUX [here](https://www.redhat.com/sysadmin/introduction-tmux-linux)
- Optional programs if you wanna show off the hacker terminal.
  - To use Colorscripts follow this [guide](https://gitlab.com/dwt1/shell-color-scripts)
  - To use Pipes.sh follow this [guide](https://github.com/pipeseroni/pipes.sh#contents)
  - To use unimatrix follow this [guide](https://github.com/will8211/unimatrix)

## Installtion of neovim and turning into a ide
- This installation guide is for C++ & python. If you want others you can follow this [tutorials for beginners](https://www.youtube.com/playlist?list=PLsz00TDipIffreIaUNk64KxTIkQaGguqn)
- First git clone the repo. Installtion guide is give [here](https://github.com/neovim/neovim/blob/master/INSTALL.md#install-from-source)
```
$ sudo apt-get install gettext libtool libtool-bin autoconf automake pkg-config doxygen
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
:TSUpdate
:Mason
```
- Install all these LSP's, Linter's & Formatters inside neovim using ```:MasonInstall package_name```
  - stylua
  - clangd
  - clang-format
  - cpplint
  - lua-language-server
  - mypy
  - pyright
  - black
- Credits : https://github.com/cpow/neovim-for-newbs/tree/main
