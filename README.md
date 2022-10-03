# Notes using vimwiki

## Topics

1.) **Penetration Testing** - Comprehensive notes on TryHackMe's Junior Pentesting learning path, and comprehensive CTF box write ups. I try to post a writeup at least every other day.

2.) **Programming** - C/C++, Python, HTML, and others coming.

3.) **Finance** - Algorithmic day trading, technical analysis, and fundamental analysis notes from various books.

4.) In the process of developing further notes in a number of fields: Physics, Mathematics, Philosophy, Computer Science, Quantum Computing, and more.

## Prerequisites

``` 
set nocompatible
filetype plugin on
syntax on
```
## Installation

### VimWiki

#### Vim-Plugin:

```
Plug 'vimwiki/vimwiki'
```

### Markdown

```
Plug 'iamcco/markdown-preview.nvim', { 'do': { -> mkdp#util#install() }, 'for': ['markdown', 'vim-plug']}
Plug 'preservim/vim-markdown'
Plug 'vim-pandoc/vim-pandoc'
Plug 'vim-pandoc/vim-pandoc-syntax'
```

## Additional Configurations

### Kali

1. Vim must be removed using sudo apt-get remove vim and then compiled from source using

```sh
sudo apt-get install -y python3-distutils python3-dev
git clone https://github.com/vim/vim.git
cd vim
./configure --prefix=/usr/local \	     
--enable-python3interp \
--with-python3-config-dir=/usr/lib/python3.6/config-*
make
sudo make install
```

for python support.

## Usage

* To reach the main wiki, open vim and hit `\ww`.
* Navigate through the wiki by using enter and backspace.
* Run the command `:MarkdownPreview` to open the markdown file in your search engine.
