#zsh

##安装

echo $SHELL查看当前shell，如果不是zsh则需要先安装

更改默认shell的方法
chsh -s /usr/bin/zsh

先安装zsh,然后安装oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

##更换主题

在~/.zshrc文件中将ZSH_THEME改为ys
source ~/.zshrc使变化生效

##安装插件

插件存放位置为 /home/leo/.oh-my-zsh/plugins/ 
下载插件，放在plugins/incr目录下
wget http://mimosa-pudica.net/src/incr-0.2.zsh  

在~/.zshrc最后添加
source ~/.oh-my-zsh/plugins/incr/incr*.zsh

##git使用

https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/git/
