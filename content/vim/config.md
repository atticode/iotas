+++
title = "Vim Config"
date = 2020-11-05T00:10:32+08:00
tags = ["vim"]
+++


```vimscript

set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
"" Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
"" Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
"" Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
"" Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
"" Plugin 'ascenator/L9', {'name': 'newL9'}

" language

" [go](https://github.com/fatih/vim-go)
Plugin 'fatih/vim-go'
" [rust](https://github.com/rust-lang/rust.vim)
Plugin 'rust-lang/rust.vim'
" [dart](https://github.com/dart-lang/dart-vim-plugin)
Plugin 'dart-lang/dart-vim-plugin'
" [javascript](https://github.com/pangloss/vim-javascript)
Plugin 'pangloss/vim-javascript' 
" [typescript](https://github.com/leafgarland/typescript-vim)
Plugin 'leafgarland/typescript-vim'
" [emmet](https://github.com/mattn/emmet-vim)
Plugin 'mattn/emmet-vim'
" https://github.com/maksimr/vim-jsbeautify
" Plugin 'maksimr/vim-jsbeautify'

" [ruby](https://github.com/vim-ruby/vim-ruby)
Plugin 'vim-ruby/vim-ruby'
" [rails](https://github.com/tpope/vim-rails)
Plugin 'tpope/vim-rails'

" https://github.com/wavded/vim-stylus
Plugin 'wavded/vim-stylus'
" https://github.com/posva/vim-vue
Plugin 'posva/vim-vue'




" text plain

" https://github.com/godlygeek/tabular
Plugin 'godlygeek/tabular'
" https://github.com/plasticboy/vim-markdown
Plugin 'plasticboy/vim-markdown'


" tools

" https://github.com/scrooloose/nerdtree
Plugin 'scrooloose/nerdtree'
" https://github.com/lifepillar/vim-mucomplete
Plugin 'lifepillar/vim-mucomplete'
" https://github.com/majutsushi/tagbar
Plugin 'majutsushi/tagbar'

" themes
" https://github.com/dracula/vim
Plugin 'dracula/vim'
" https://github.com/altercation/vim-colors-solarized
Plugin 'altercation/vim-colors-solarized'
" https://github.com/vim-airline/vim-airline
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'


" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line

set laststatus=2

" vim-javascript
let g:javascript_plugin_jsdoc = 1
let g:javascript_plugin_ngdoc = 1

" vim-airline
let g:airline#extensions#tabline#enabled = 0
let g:airline#extensions#tabline#left_sep = ' '
let g:airline#extensions#tabline#left_alt_sep = '|'
let g:airline#extensions#tabline#formatter = 'default'

" mucomplete
set completeopt+=menuone
set completeopt+=noselect
" or
" set completeopt+=noinsert
" set shortmess+=c   " Shut off completion messages
" set belloff+=ctrlg " If Vim beeps during completion
let g:mucomplete#enable_auto_at_startup = 1
" let g:mucomplete#completion_delay = 1



set number

" set tab
set tabstop=4
set softtabstop=4
set shiftwidth=4
set noexpandtab
" set expandtab
set autoindent
set cindent

" no backup
set nobackup

"set encoding=utf-8
set fileencodings=utf-8,gbk,gb2312 
set fileencoding=utf-8
set termencoding=utf-8

" remove menu bar
set guioptions-=m
" remove toolbar
set guioptions-=T

" set fonts
set guifont=Inconsolata:h14
" set guifont=SourceCodePro:h12

syntax on

set background=light

" colorscheme solarized
colorscheme dracula

filetype on

set nocompatible

set backspace=indent,eol,start

set foldmethod=indent
set nofoldenable

:cd D:/





```
