---
layout: post
title: Vundle——带有github特点的vim插件管理器
date: 2014-02-01 02:41:00
tags: vundle vim插件管理器
categories: 玩意儿
---

###什么是[Vundle]

[vundle]是一款vim插件管理器，它用.vimrc管理vim插件，为所有管理下的插件设置单独的存放位置，最大的特点是可以直接从github上下载插件。


###安装Vundle

1. 下载

```
git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/Vundle.vim
```

2. 配置

在.vimrc顶部添加以下内容：

```
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" let Vundle manage Vundle, required
Plugin 'gmarik/Vundle.vim'
" 根据自己的需要增删插件
Plugin 'tpope/vim-fugitive'
Plugin 'L9'
Plugin 'git://git.wincent.com/command-t.git'
Plugin 'file:///home/gmarik/path/to/plugin'
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
Plugin 'user/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
```

###用Vundle安装插件

1. 在.vimrc中填写要安装的插件名字，比如要安装“neocomplete”的话，需要添加如下内容：

```
Plugin 'Shougo/neocomplete.vim'
```

2. 运行vim，输入

```
:PluginInstall
```

vim会提示目前被[vundle]管理的插件，并提示正在安装neocomple，稍等片刻插件就安装完毕了。


###用Vundle卸载插件

1. 删除或屏蔽.vimrc中安装过的插件信息

2. vim中输入

```
:PluginClean
```

提示要被删除的插件名称，确认之后，插件就被删除。

[vundle]:https://github.com/gmarik/vundle
[Vundle]:https://github.com/gmarik/vundle
