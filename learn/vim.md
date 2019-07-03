# nvim

# 一、安装nvim

[官网安装教程](https://www.vim.org/git.php)

```shell
git clone https://github.com/vim/vim.git
cd vim
./configure --with-features=huge \
        --enable-multibyte \
        --enable-python3interp=yes \
        --with-python-config-dir=/usr/local/python3/lib/python3.7/config-3.7m-x86_64-linux-gnu \        --enable-gui=gtk2 \
        --enable-cscope \
#make distclean  # if you build Vim before
make -j8
sudo make install
cp src/vim /usr/bin
```

## 二、插件安装

```shell
# Vundle安装
# 地址： https://github.com/VundleVim/Vundle.vim
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

# 安装NERDTree插件
# 在.vmrc中添加
Plugin 'scrooloose/nerdtree'

# 安装YouCompleteMe
https://blog.csdn.net/wanormi/article/details/82998541

```

