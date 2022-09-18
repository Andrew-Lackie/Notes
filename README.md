# Notes using vimwiki

## Prerequisites

``` 
set nocompatible
filetype plugin on
syntax on
```
## Installation for vimwiki

### Vim-Plugin

```
Plug 'vimwiki/vimwiki'
```

### Pathogen

```
cd ~/.vim
mkdir bundle
cd bundle
git clone https://github.com/vimwiki/vimwiki.git
```

### Vundle

```
Plugin 'vimwiki/vimwiki'
```

## Markdown

```
Plugin 'iamcco/markdown-preview.nvim'
Plugin 'preservim/vim-markdown'
Plugin 'vim-pandoc/vim-pandoc'
Plugin 'vim-pandoc/vim-pandoc-syntax'
```

## usage

* To reach the main wiki, open vim and hit `\ww`.
* Navigate through the wiki by using enter and backspace.
* Run the command `:MarkdownPreview` to open the markdown file in your search engine.

## Topics:

1.) Finance - Algorithmic day trading, technical analysis, and fundamental analysis notes from various books.

2.) Programming - C/C++, Python, and working on notes for other languages.

3.) Penetration Testing - Comprehensive notes on TryHackMe's Junior Pentesting learning path, and box write ups.

4.) In the process of developing further notes in a number of fields: Quantum Mechanics, Differential Geometry, String Theory, Computer Science, Pentesting Tools, etc.
