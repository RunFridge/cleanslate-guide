<p align="center">
	<img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1574221064/noticon/xjal9z4a8h46soi6ktgo.png" width="100"/>
</p>


# 🧼 Cleanslate Guide

[![Author](https://img.shields.io/badge/author-RunFridge-green?style=flat)](https://github.com/hwhang0917) ![License](https://img.shields.io/github/license/RunFridge/cleanslate-guide) 

> This guide instructs users to setup new windows 10 when starting a new PC, hence "clean-slate".

## Table of Contents

[TOC]

## Goal

Originally, this repository was set up so I can quickly setup formatted PC for my developing environment. It is to help user set up native windows environment with versatile version management, readability, and style. However many of the software here are merely recommendation by personal taste, so you can install what suits you. If there are suggestions or error in this document feel free to leave an issue or make a pull request.

## Before Installing

- System Requirements
  - Windows 10 Version 2004 (*check the [latest Windows 10 update](ms-settings:windowsupdate?activationSource=SMC-IA-4027667)*)
- Browser Requirements
  - Chromium based browser (*preferably [Brave browser](https://brave.com/)*)
- Installation marked with <img src="https://chocolatey.org/content/images/global-shared/logo-square.svg" width="50"/> can be installed with [chocolatey package manager](https://chocolatey.org/)
- **Always check the original software site's reference/manual before installing**

## Initial Setup

These are some required software before starting other setups.

| Software Name    | Description                                                  | Installation                                                 | Reference                                                    | Required |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| Chocolatey       | Windows Package Manager                                      | [![](https://img.shields.io/badge/Install-blue)](https://chocolatey.org/install) | [![](https://img.shields.io/badge/Reference-green)](https://docs.chocolatey.org/en-us/choco/setup) | ✅        |
| Windows Terminal | Terminal supporting UTF-8, GPU acceleration, styling, and more | [![](https://img.shields.io/badge/Install-blue)](https://github.com/microsoft/terminal#installing-and-running-windows-terminal) or <img src="https://chocolatey.org/content/images/global-shared/logo-square.svg" width="50"/> | [![](https://img.shields.io/badge/Reference-green)](https://github.com/microsoft/terminal) | ✅        |
| MesloLGS font    | Nerdy font for terminal, editor, and more                    | [![](https://img.shields.io/badge/Install-blue)](https://github.com/romkatv/dotfiles-public/tree/master/.local/share/fonts/NerdFonts) |                                                              |          |

## [Node.JS](https://nodejs.org/en/)

1. Install [NVM-windows](https://github.com/coreybutler/nvm-windows/wiki#installation) [![](https://img.shields.io/badge/Reference-green)](https://github.com/coreybutler/nvm-windows)

   nvm-windows is a windows version of Node Version Manager; to change between different Node.JS version

2. Using nvm install the preferred Node.JS version `nvm install <version>`

   check [this page](https://nodejs.org/en/about/releases/) or type `nvm list available` in terminal to check available Node versions.

3. Type `nvm use <version>` to use the installed version.

4. Check if the correct Node.JS version is installed via `node --version` command (also `npm --version` if possible)

## [Python](https://www.python.org/)

1. Install [pyenv-win](https://github.com/pyenv-win/pyenv-win#installation) [![](https://img.shields.io/badge/Git%20reference-green)](https://github.com/pyenv-win/pyenv-win)

   pyenv-win is a windows version of Python version manager (pyenv); to change between different Python version
   
   possible with chocolatey command [![](https://img.shields.io/badge/Reference-green)](https://chocolatey.org/packages/pyenv-win) <img src="https://chocolatey.org/content/images/global-shared/logo-square.svg" width="50"/>
   
   ```sh
   choco install pyenv-win
   ```
   
2. In windows settings [Apps & Features](ms-settings:appsfeatures), then go to App execution aliases or in window search type `Manage app execution aliases`

   then disable `python` and `python3` command from opening Microsoft Store App

3. Using pyenv-win install the preferred python version `pyenv install <version>`

   check [this page](https://www.python.org/downloads/) or type `pyenv install -l` in terminal to check available Python versions.

4. Type `pyenv global <version>` to set python version to be used globally

   Use `pyenv local <version>` to set python version for a specific directory

5. Check if the correct python version is installed via `python --version` command

## [Git](https://git-scm.com/)

1. Install [Git](https://git-scm.com/downloads)

    possible with chocolatey command [![](https://img.shields.io/badge/Reference-green)](https://chocolatey.org/packages/git) <img src="https://chocolatey.org/content/images/global-shared/logo-square.svg" width="50"/>

   ```sh
   choco install git
   ```

2. Install [Github-cli](https://github.com/cli/cli) [![](https://img.shields.io/badge/Reference-green)](https://cli.github.com/manual/)

3. Install [Gitmoji-cli](https://github.com/carloscuesta/gitmoji-cli) using NPM ![](https://img.shields.io/badge/NPM%20required-red)

   ```sh
   npm i -g gitmoji-cli
   ```

   Gitmoji-cli allow commit messages to have coherent emoji for readability

   ![](https://cloud.githubusercontent.com/assets/7629661/20454643/11eb9e40-ae47-11e6-90db-a1ad8a87b495.gif)

   > gitmoji-cli in action

4. Configure git

   Add `.gitconfig` file in `%HOME%` directory as following (*Add preferred aliases*: [![](https://img.shields.io/badge/Git%20reference-green)](https://git-scm.com/docs))

   ```toml
   [user]
   	email = YOUR_EMAIL
   	name = YOUR_NAME
   [core]
       autocrlf = true
   [alias]
       co = checkout
       c = commit
       cm = commit -m
       st = status
       br = branch
       hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short 
       type = cat-file -t
       dump = cat-file -p
       pom = push origin master
   
   ```

## Terminal

1. Install [Windows Terminal](https://github.com/microsoft/terminal#installing-and-running-windows-terminal)

2. Install [oh-my-posh](https://ohmyposh.dev/docs/installation) theme

   ![](https://ohmyposh.dev/assets/images/agnoster-2554ec80c8f34ce54a7dac6c1a2f111a.png)

   > Oh-my-posh's Agnoster theme sample Image

## Editor

I've installed all of the following editors and use them for difference purposes. But you can pick the one you prefer.

| Editor Name        | Description                                                  | Installation                                                 | Reference                                                    |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Visual Studio Code | [Electron](https://www.electronjs.org/) based editor recommended for all types of coding: has excellent extensions. I use it when working on large scale project. | [![](https://img.shields.io/badge/Install-blue)](https://code.visualstudio.com/) | [![](https://img.shields.io/badge/Reference-green)](https://code.visualstudio.com/docs) |
| Sublime Text       | Lightweight editor, I use it to view single code file. Has an option to add `Open with Sublime Text` to the context menu for quick access. Also can access via CLI if added to windows environment variables with `subl filename.cpp` command. | [![](https://img.shields.io/badge/Install-blue)](https://www.sublimetext.com/) |                                                              |
| Vim                | Terminal based editor, can be used for quick edit / view within the terminal. Can be really agile if used to short keys. | <img src="https://chocolatey.org/content/images/global-shared/logo-square.svg" width="50"/> |                                                              |

### Visual Studio Code

