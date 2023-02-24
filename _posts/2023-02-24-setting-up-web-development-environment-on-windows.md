---
layout: post
title: Setting up Web Development Environment on Windows
date: 2023-02-24 17:55 +0800
img_path: /assets/img/
categories: [technology]
tags: [web development, node, windows, linux, wsl]
---

I've been developing on a mac ever since I started working professionally, however resigning from my last job forced me to use my gaming pc instead after I surrendered my macbook to my company. Switching from macos web development environment to windows maybe pain in the ass, but luckily, windows 11 already introduced WSL which you can install and allow you to run linux environment without having a separate virtual machine. 

You might opt to go to a tradional route, or just use docker. But here how I set up my PC running on windows11 for web development.

# Installing WSL 2

First open the command prompt and type

```
wsl --install
```

This will install WSL with ubuntu distribution by default.  If you want other distribution you may follow the official docs [here](https://learn.microsoft.com/en-us/windows/wsl/install#change-the-default-Linux-distribution-installed)

Upon successful installation, a restart will be required for the changes to take effect. 

Once you're done with the restart, a terminal will open asking you to input your username and password. If the terminal didn't open at the startup, you may search it in the start menu instead.

# Updating Linux

The next step you need to do is to make sure that your linux packages are updated and upgraded. Do this by running this command on the linux terminal

```
sudo apt update && sudo apt upgrade
```

### Optional: Mapping Your Ubuntu Drive as a Network Drive

For easy access on files inside your ubuntu drive, you may want to map it as a network drive

1. First, open you file explorer and locate the linux folder

![screenshot](/Pasted_image_20230224161459.png)

2. Right click, and select map to network drive (if you don't see the option, just click see more options)

![screenshot](/Pasted_image_20230224161621.png)

3. You should see the ubuntu as a network drive in "This PC"
![screenshot](/Pasted_image_20230224161704.png)

# Setting up Linux for Web Development

The tools listed here may or may not be essential for web development. But listed here are the tools and personal configuration for my web development environment.

I'm using the preinstalled `terminal` application as my console choice. This is already installed in windows11 machines, but if it's not installed in your machine, you can always get it on microsoft store.

Because we'll be primarily working on Ubuntu profile, i will set the default profile and default terminal application to `Ubuntu` and `windows terminal`

![screenshot](/Pasted_image_20230224162401.png)

# Install Brew

I use brew as my package manager of choice. Install brew by running this command

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, you need to update your PATH and add brew

```
  (echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/<user>/.profile
  eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

And also it is recommended to install build-essentials

```
sudo apt-get install build-essential
```

# Install ZSH

ZSH or Z Shell is my scripting language of choice, it adds more functionalities on shell and allows plugins.

```
sudo apt install zsh
```

# Install Oh My ZSH

OhMyZSH is my favorite plugin of zsh, installing omz includes several bundled themes and helpers already. Install omz by running this command

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

> This command needs curl, if curl is not preinstalled in your linux you may install it via `sudo apt install curl`

After installing OMZ, my preferred theme is `agnostic`. To change theme edit the zshrc file. You can use nano or vim to do this

```
vim .zshrc
```

Look for the theme line and change to `agnoster`

```
ZSH_THEME="agnoster"
```

This theme will require powerlines font or else you're just going to see `?` instead of symbols.

To install powerline in windows you may follow this [instruction](https://gist.github.com/stramel/658d702f3af8a86a6fe8b588720e0e23).

After installing the font, go to profile settings and set the following.

Color scheme: Solarized Dark
Font Face: `Meslo LG S DZ for Powerline`
Font Size: 10

![screenshot](/Pasted_image_20230224171225.png)

After restarting the terminal, your terminal should look like this

![screenshot](/Pasted_image_20230224171329.png)

The other two plugins that I'd like to install is zsh autosuggestions and zsh syntax highlighting

To install zsh autosuggestions

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

To install zsh syntax highlighting

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Add the plugins in `.zshrc` via nano or vim

```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

# Install Git

To install git, run this following command

```
brew install git
```

After completing the installation, configure your git

Git Name

```
git config --global user.name "name"
```

Git Email

```
git config --global user.email "email"
```

Git Username

```
git config --global user.username "username"
```

# Install Node

To install node, I'd like to use node version manager so that I can switch out versions also. To do that, run the following command

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

After installation, you will need to restart your terminal. Check if NVM is successfuly installed

```
command -v nvm
```

Using `nvm` install node,I always like to install the LTS, but nvm will allow me to install different and switch out to version of node if needed.

```
nvm install --lts
```

Verify node is installed, it also comes with the default package manager, npm

```
node --version
npm --version
```

