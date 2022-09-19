# Installation Scripts

## Github Repos

### VimWiki

#### Notes

1. Vim must run `:call mkdp#util#install()` for markdown to work.
2. Vim must be removed using `sudo apt-get remove vim` and then compiled from source using 
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

