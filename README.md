# Notes using vimwiki

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

## Topics

1.) Finance - Algorithmic day trading, technical analysis, and fundamental analysis notes from various books.

2.) Programming - C/C++, Python, and working on notes for other languages.

3.) Penetration Testing - Comprehensive notes on TryHackMe's Junior Pentesting learning path, and box write ups.

4.) In the process of developing further notes in a number of fields: Quantum Mechanics, Differential Geometry, String Theory, Computer Science, Pentesting Tools, etc.
