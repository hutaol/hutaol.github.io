# Mac Vim配置及插件

## 1 macOS（Linux）包管理器 `Homebrew`

安装命令

```brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)
```

## 2 安装vim

```brew
brew install wget
```

## 3 建立并编辑配置文件

```brew
cd ~
touch .vimrc
vim .vimrc
```

编辑配置文件为：

```vim
" 输入:make编译并运行
set makeprg=clear;gcc\ %\ &&\ ./a.out

" 当前行高亮
au WinLeave * set nocursorline nocursorcolumn
au WinEnter * set cursorline
set cursorline

colorscheme default       " 颜色主题
syntax enable             " 启用语法分析着色
set tabstop=4             " 设定Tab表示的空格数
set softtabstop=4         " 设定输入Tab表示的空格数
set expandtab             " 将Tab视为若干空格
set backspace=2           " 设置退格键可用
set number                " 显示行号
set showcmd               " 右下角显示待补全命令
set hlsearch              " 搜索字符串时高亮所有结果,:nohlsearch取消高亮
```

`:wq` 保存退出

## 4 安装Vundle（Vim 插件管理器）

```git
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

// 编辑文件
vim .vimrc
```

在配置文件开头添加如下配置：

```vim
"---START OF VUNDLE---
set nocompatible
filetype off

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'
" Plugins start

" Plugins end
call vundle#end()
filetype plugin indent on
" ---END OF VUNDLE---
```

## 5 Vundle安装插件

在配置文件 "Plugins start 和 end 注释之间加入：

```vim
Plugin '[插件名]'

:wq
vim .vimrc
:PluginInstall
```

## 6 代码自动补全YouCompleteMe安装

```brew
brew install cmake
```

方法一 使用Vundle安装

然后在 `/.vimrc`文件中加入

```vim
Plugin 'Valloric/YouCompleteMe',{'do':'python3 install.py'}

// Go support
Plugin 'Valloric/YouCompleteMe',{'do':'python3 install.py --go-completer'}
// 全部安装
Plugin 'Valloric/YouCompleteMe',{'do':'python3 install.py --all'}
```

然后执行`:PluginInstall`，自动安装

**注**： `https://www.jianshu.com/p/edc4bbed92ca`

方法二
下载ycm源码包

```git
git clone https://github.com/Valloric/YouCompleteMe.git

// YouCompleteMe/目录下执行命令
cd YouCompleteMe
python install.py
```

