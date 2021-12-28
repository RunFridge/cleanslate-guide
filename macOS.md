<p align="center">
	<img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1588562735/noticon/rmbkeyap75d6u6v0kjdj.png" width="100" />
</p>

# Developer Setup Guide

[![](https://img.shields.io/badge/Github-hwhang0917-brightgreen?logo=github)](https://github.com/hwhang0917)

> 이 문서는 개발자 세팅 환경 가이드입니다.

## Terminal Basic

- [iTerm2](https://iterm2.com/index.html) 설치

- [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) 설치

  | Method    | Command                                                                                           |
  | --------- | ------------------------------------------------------------------------------------------------- |
  | **curl**  | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
  | **wget**  | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`   |
  | **fetch** | `sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |

- [Powerlevel10k](https://github.com/romkatv/powerlevel10k) 테마 설치

  ```sh
  $ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
  $ echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
  ```

  - 폰트 설치

    - [MesloLGS NF](https://github.com/romkatv/powerlevel10k/blob/master/font.md)

  - 터미널에서 아래 커맨드로 테마 설정

    ```sh
    $ p10k configure
    ```

  - `~/.p10k.zsh` 에서 설정 아래와 같이 변경
    (_터미널에서 마지막 디렉토리만 표시하도록 설정_)

    - ` typeset -g POWERLEVEL9K_SHORTEN_STRATEGY=truncate_to_last`

- [Homebrew](https://brew.sh/) 설치

  ```sh
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```

- [Tmux](https://formulae.brew.sh/formula/tmux) 설치

  ```sh
  $ brew install tmux
  ```

  - [.tmux](https://github.com/gpakosz/.tmux) 커스텀 설정 설치

    ```sh
    $ git clone https://github.com/gpakosz/.tmux.git /path/to/oh-my-tmux
    $ ln -s -f /path/to/oh-my-tmux/.tmux.conf ~/.tmux.conf
    $ cp /path/to/oh-my-tmux/.tmux.conf.local ~/.tmux.conf.local
    ```

### Other CLI Apps

> brew 로 설치 가능

- [exa](https://github.com/ogham/exa) - `ls` 커맨드 개선
- [bat](https://github.com/sharkdp/bat) - `cat` 커맨드 개선
- [autojump](https://github.com/wting/autojump) - `j` 로 디렉토리 이동 개선
- [tig](https://formulae.brew.sh/formula/tig) - `git` 텍스트 인터페이스
- [nvm](https://github.com/nvm-sh/nvm) - `node` 버전 관리
- [cheat](https://formulae.brew.sh/formula/cheat) - 유닉스 커맨드 참고 예제

### Zsh Plugins

- [zsh-syntax-highlighting](https://formulae.brew.sh/formula/zsh-syntax-highlighting)
- [zsh-autosuggestions](https://formulae.brew.sh/formula/zsh-autosuggestions)
- [fzf](https://formulae.brew.sh/formula/fzf)

```sh
$ brew install zsh-syntax-highlighting
$ brew install zsh-autosuggestions
$ brew install fzf
```

- `~/.zshrc` 파일에 플러그인 추가

```sh
plugins=(
	zsh-syntax-highlighting
	zsh-autosuggestions
	fzf
)
```

### Zsh Alias

```sh
# tmux 단축키
alias ta = "tmux attach -t"
# cat 을 bat으로 대체
alias cat = "bat"
# ls 를 exa로 대체
alias ls = "exa --icons"
alias ll = "exa -l --icons --git"
alias la = "exa -la --icons --git"
# 열려있는 포트 조회
alias ls-ports = "netstat -anvp tcp | awk 'NR<3 || /LISTEN/'"
# 외부 아이피 조회
alias whatextip = "dig +short myip.opendns.com @resolver1.opendns.com"
# 오타 방지
alias sl = "ls"
# Hombrew 업데이트 및 정리
alias brewup = "brew update; brew upgrade; brew cleanup; brew doctor"
# 날씨 조회
alias weather = "curl wttr.in"
```

## Vim

- [Vim-Plug](https://github.com/junegunn/vim-plug) - vim 플러그인 매니저 설치

  ```sh
  curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
      https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  ```

- `~/.vimrc` 설정

  ```sh
  " Vim-Plugins
  call plug#begin('~/.vim/plugged')
  	" Formatter
  	Plug 'prettier/vim-prettier'
  	" Utility Plugins
  	Plug 'tpope/vim-surround'
  	Plug 'kien/ctrlp.vim'
    Plug 'preservim/nerdtree'
  	Plug 'wakatime/vim-wakatime'
  	" Visual Plugin
  	Plug 'ryanoasis/vim-devicons'
  	" Syntax Highlight Plugins
  	Plug 'scrooloose/syntastic'
  	Plug 'mxw/vim-jsx'
  	Plug 'jparise/vim-graphql'
  	Plug 'pangloss/vim-javascript'
  	Plug 'leafgarland/typescript-vim'
  	Plug 'tomlion/vim-solidity'
  call plug#end()

  " Key Mapping
  " NerdTree Open
  nmap nerd :NERDTreeToggle<CR>
  " Switch between buffers
  nmap <C-j> :bnext<CR>
  nmap <C-k> :bprev<CR>
  " Split Window
  nmap <C-w>- :split<CR>
  nmap <C-w>_ :vsplit<CR>
  " Blackhole Register
  noremap ' "_

  " Vim settings
  if has('syntax')
      syntax on
  endif
  set noimd
  set showmatch
  set ts=4
  set shiftwidth=4
  set nu
  set ruler
  set relativenumber
  set encoding=UTF-8
  set fileencodings=utf8,euc-kr

  " Colorscheme
  if has("termguicolors")
  	set termguicolors
  endif

  " Vim Prettier
  let g:prettier#autoformat = 0
  autocmd BufWritePre *.js,*.jsx,*.mjs,*.ts,*.tsx,*.css,*.less,*.scss,*.json,*.graphql,*.md,*.vue PrettierAsync

  " Syntastic Settings
  set statusline+=%#warningmsg#
  set statusline+=%{SyntasticStatuslineFlag()}
  set statusline+=%*

  let g:syntastic_always_populate_loc_list=1
  let g:syntastic_auto_loc_list=1
  let g:syntastic_check_on_open=1
  let g:syntastic_check_on_wq=0

  " NERDTREE Devicon
  let g:webdevicons_conceal_nerdtree_brackets=1

  " Vim-Javascript Settings
  let g:javascript_plugin_jsdoc=1
  let g:javascript_plugin_flow=1

  " Vim-Jsx Settings
  let g:jsx_ext_required=1
  ```

- 아래 커맨드를 실행하여 Vim 플러그인 설치

  ```sh
  $ vim +PlugInstall
  ```

- 다음 디렉토리에서 `vim-prettier`에 필요한 패키지 설치 (`~/.vim/plugged/vim-prettier`)

  - `yarn` 또는 `npm instsall`

## Other Apps

> 그 외 유용한 MacOS Application

- [Hammerspoon](https://www.hammerspoon.org/) - 커스텀 단축키 매핑

  - `~/.hammerspoon/init.lua` 파일에서 단축키 설정 가능

  설정 예제:

  ```lua
  -- cmd + control + T 조합으로 iTerm을 여는 단축키 설정
  hs.hotkey.bind({'cmd', 'control'}, 'T', hs.application.launchOrFocus('iTerm'))
  ```

- [Typora](https://typora.io/) - 마크다운 에디터 (💰 유료)

## Visual Stuido Code 설정

- Extensions
  - Apollo GraphQL (apollographql.vscode-apollo)
    - GrpahQL 개발 도구
  - Choose A License (ultram4rine.vscode-choosealicense)
    - 신규 프로젝트 `LICENSE` 파일 추가 템플릿
  - Codesnap (adpyke.codesnap)
    - 코드 스크린샷
  - DotENV (mikestead.dotenv)
    - `.env` 파일 syntax highlight
  - ES7 React/Redux/GraphQL/React-Native snippets (dsznajder.es7-react-js-snippets)
    - 자바스크립트 ES7 snippets
  - ESLint (dbaeumer.vscode-eslint)
    - VSC 자바스크립트 ESLint
  - Excel Viewer (grapecity.gc-excelviewer)
    - VSC 엑셀 뷰어
  - gitignore (codezombiech.gitignore)
    - `.gitignore` 파일 생성 템플릿
  - Gitlens (eamodio.gitlens)
    - 에디터 내부에서 `git` 조회
  - GraphQL (graphql.vscode-graphql)
    - GraphQL 개발 도구
  - indent-raindow (oderwat.indent-rainbow)
    - 가독성을 위한 indentation highlighting
  - Jira and Bitbucket (atlassian.atlascode)
    - VSC에서 Jira issue 조회
  - Material Icon Theme (pkief.material-icon-theme)
    - 파일 및 폴더 아이콘 테마
  - Peacock (johnpapa.vscode-peacock)
    - VSC 창별로 구분 가능한 색 지정
  - Prettier - Code formatter (esbenp.prettier-vscode)
    - 코드 포맷
  - Shares of Purple (ahmadawais.shades-of-purple)
    - 보라색 테마
  - vscode-styled-components (jpoissonnier.vscode-styled-components)
    - `jsx` 또는 `tsx` 파일 내부의 styled-components CSS highlighting
  - Vim (vscodevim.vim)
    - VSC vim 에뮬레이터
- `settings.json`

> command + shift + p 로 `> preferences: Open Settings (JSON)` 실행

```json
{
  // Workbench
  "workbench.iconTheme": "material-icon-theme",
  "workbench.colorTheme": "Shades of Purple",
  "workbench.fontAliasing": "auto",
  "workbench.startupEditor": "none",
  // Security
  "security.workspace.trust.untrustedFiles": "open",
  // Terminal
  "terminal.external.osxExec": "iTerm.app",
  "terminal.integrated.fontFamily": "MesloLGS NF",
  // Editor
  "editor.fontFamily": "D2Coding",
  "editor.fontSize": 18,s
  "editor.lineHeight": 24.65,
  "editor.letterSpacing": 0.5,
  "editor.fontWeight": "400",
  "editor.fontLigatures": true,
  "editor.cursorBlinking": "phase",
  "editor.cursorStyle": "line",
  "editor.cursorWidth": 5,
  "editor.smoothScrolling": true,
  "editor.renderWhitespace": "all",
  "editor.glyphMargin": true,
  "editor.semanticHighlighting.enabled": true,
  // Editor -- Format
  "editor.formatOnSave": true,
  "editor.formatOnPaste": false,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  // Editor -- Suggestions
  "editor.inlineSuggest.enabled": true,
  "editor.quickSuggestions": {
    "other": true,
    "comments": false,
    "strings": true
  },
  // Editor - Minimap
  "editor.minimap.enabled": true,
  "editor.minimap.renderCharacters": false,
  "editor.minimap.maxColumn": 200,
  "editor.minimap.showSlider": "always",
  "editor.scrollbar.vertical": "hidden",
  // Editor - Bracket
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": true,
  // Edidotr - LineNumbers
  "editor.lineNumbers": "relative",
  // Files
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "files.eol": "\n",
  // CSS
  "css.validate": false,
  // JavaScript
  "javascript.updateImportsOnFileMove.enabled": "always",
  // Emmet
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  //Python
  "python.formatting.provider": "black",
  "python.defaultInterpreterPath": "/usr/bin/python3",
  // Golang
  "[go]": {
    "editor.defaultFormatter": "golang.go"
  },
  // GraphQL
  "[graphql]": {
    "editor.defaultFormatter": "apollographql.vscode-apollo"
  },
  // Typescript
  "typescript.updateImportsOnFileMove.enabled": "always",
  // Material Theme
  "material-icon-theme.activeIconPack": "nest",
  // Gitlens
  "gitlens.hovers.currentLine.over": "line",
  // VIM
  "vim.vimrc.path": "~/.vimrc",
  "vim.vimrc.enable": true,
  "vim.autoSwitchInputMethod.defaultIM": "true",
  // Peacock Colors
  "peacock.favoriteColors": [
    {
      "name": "Typescript Blue",
      "value": "#3178c6"
    },
    {
      "name": "GraphQL Pink",
      "value": "#e535ab"
    },
    {
      "name": "Gopher Blue",
      "value": "#00add8"
    },
    {
      "name": "Next.js White",
      "value": "#ffffff"
    },
    {
      "name": "MongoDB Green",
      "value": "#4db33d"
    },
    {
      "name": "Gitlab Orange",
      "value": "#f76230"
    },
    {
      "name": "NestJS Red",
      "value": "#ce3951"
    },
    {
      "name": "Altair Gray",
      "value": "#34363b"
    }
  ],
  // Material Icon Theme
  "material-icon-theme.showWelcomeMessage": false,
  // Explorer
  "explorer.confirmDelete": false,
  "explorer.autoReveal": false,
  "explorer.confirmDragAndDrop": false,
}

```
