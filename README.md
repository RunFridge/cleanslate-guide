# 🧼 Cleanslate Guide

![](https://img.shields.io/github/license/RunFridge/cleanslate-guide)

> This guide instructs users to set a new "celan-slate" operating system when starting a new PC.

## Instructions

Not all installations are required, just install what suits yourself.

#### Prerequisite

- System
  - Windows 10 Version 2004 (Install the latest Windows 10 Update)

#### Recommanded Softwares

- General Tools

  - [Chocolatey](https://chocolatey.org/install): CLI tool for application management
  - _Choco Packages_

    - [Git](https://chocolatey.org/packages/git) - Git version control

      ```sh
      choco install git
      ```

    - [Mingiw](https://chocolatey.org/packages/mingw) - Minimalist GNU Compiler

      ```sh
      choco install mingw
      ```

    - [NVM](https://chocolatey.org/packages/nvm) - Node Version Manager (Check this link for [nvm-windows](https://github.com/coreybutler/nvm-windows))

      ```sh
      choco install nvm
      ```

      Then, install Node.js LTS or other versions

    - [Yarn](https://chocolatey.org/packages/yarn) - Yarn Package Manager

      ```sh
      choco install yarn
      ```

    - [Python](https://chocolatey.org/packages/python/) - Install any preferred version ([Check here for stable version](https://www.python.org/downloads/))

    - [Windows Terminal](https://chocolatey.org/packages/microsoft-windows-terminal)
      ```sh
      choco install microsoft-windows-terminal
      ```

- [Install Ubuntu from Microsoft Store](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)

- [WSL 2 Installation & Settings](https://docs.microsoft.com/en-us/windows/wsl/install-win10#update-to-wsl-2)

- Windows Terminal Setting

  1. Download and install [MesloLGS NF](https://github.com/romkatv/dotfiles-public/tree/master/.local/share/fonts/NerdFonts) Fonts
  2. Add the following schema in `settings.json` under `"schemes": []` by pressing `CTRL + ,`
     ```json
     {
        "name": "VS Code",
        "background": "#232323",
        "black": "#000000",
        "blue": "#579BD5",
        "brightBlack": "#797979",
        "brightBlue": "#9BDBFE",
        "brightCyan": "#2BC4E2",
        "brightGreen": "#1AD69C",
        "brightPurple": "#DF89DD",
        "brightRed": "#F6645D",
        "brightWhite": "#EAEAEA",
        "brightYellow": "#F6F353",
        "cyan": "#00B6D6",
        "foreground": "#D3D3D3",
        "green": "#3FC48A",
        "purple": "#CA5BC8",
        "red": "#D8473F",
        "white": "#EAEAEA",
        "yellow": "#D7BA7D"
     },
     ```
  3. Set default profile as following:
     ```json
     "defaults": {
        "colorScheme": "VS Code",
        "fontFace": "MesloLGS NF"
     }
     ```
  4. Set `Azure Cloud Shell` and `Command Prompt` as hidden

- Browsers

  - [Brave Browser](https://brave.com/): Browser for general web browsing
  - [Chrome](https://www.google.com/chrome/): Broswer for general dev tools
  - _Chrome Extensions_
    - [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en): Prettify JSON
    - [Page Ruler](https://chrome.google.com/webstore/detail/page-ruler-redux/giejhjebcalaheckengmchjekofhhmal?hl=en): Pixel ruler
    - [ColorZilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp?hl=en): Color pallet
  - [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/): Browser for CSS dev tools

- Editors

  - [Visual Studio Code](https://code.visualstudio.com/): Code Editor
  - _VSC Extensions_
    - Prettier
    - ESLint
    - Remote - WSL
    - WakaTime
    - Material Theme
  - [Typora](https://typora.io/): Markdown Editing

- Archive Management

  - [Bandizip](https://kr.bandisoft.com/bandizip/): Minimal archive program

- Multimedia

  - [Kakao Pot Player](https://tv.kakao.com/guide/potplayer): Video player with basic codec support
  - [VLC](https://www.videolan.org/vlc/index.html): Lightweight Audio / Video player
  - [Audacity](https://www.audacityteam.org/download/): Audio editor
  - [Honeyview](https://kr.bandisoft.com/honeyview/): Image viewer
  - [Paint.NET](https://www.getpaint.net/): Minimal photo editor

- Task Management

  - [Notion](https://www.notion.so/): Task / Schedule management\

- Web Development

  - [WAMP](https://bitnami.com/stack/wamp/installer): WAMP Bitnami Server

- Miscellaneous
  - [Postman](https://www.postman.com/): API Dev tool
  - [Zeplin](https://zeplin.io/): Designer collaboration tool
  - [DarkNamver](https://software.naver.com/software/summary.nhn?softwareId=GWS_000169): File name editor
  - [Hoax Eliminator](https://teus.me/690): Eliminates Korean security hoax tools
  - [모두의 프린터](https://modu-print.tistory.com/): Virtual Printer for creating PDF

#### VSC Settings

```json
{
  "workbench.colorTheme": "Material Theme Darker High Contrast",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.startupEditor": "newUntitledFile",
  "terminal.integrated.fontFamily": "MesloLGS NF",
  "terminal.integrated.shell.windows": "C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
  "editor.formatOnSave": true,
  "editor.fontSize": 18,
  "workbench.colorCustomizations": {},
  "prettier.packageManager": "yarn",
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "javascript.updateImportsOnFileMove.enabled": "always",
  "go.formatTool": "goimports",
  "FSharp.useSdkScripts": true,
  "explorer.confirmDelete": false,
  "editor.fontFamily": "D2Coding",
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "editor.suggestSelection": "first",
  "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
  "java.semanticHighlighting.enabled": true,
  "explorer.confirmDragAndDrop": false,
  "todo-tree.tree.showScanModeButton": false,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "python.languageServer": "Microsoft",
  "C_Cpp.updateChannel": "Insiders"
}
```
