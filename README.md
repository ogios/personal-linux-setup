# personal-linux-setup

## 基础

### 7zip
```bash
yay -S 7-zip
```
命令：
```bash
7zz x <name>.zip -r -o<path>
7zz a <include>
```

### 时间
```bash
timedatectl set-local-rtc 1 --adjust-sy
```

### 字体
```bash
sudo pacman -S ttf-dejavu wqy-microhei wqy-microhei-lite noto-fonts noto-fonts-cjk noto-fonts-emoji noto-fonts-extra adobe-source-han-serif-cn-fonts adobe-source-han-sans-cn-fonts wqy-zenhei wqy-bitmapfont ttf-arphic-ukai

yay -S ttf-fira-code
```

[nerd-fonts](https://www.nerdfonts.com/font-downloads)


### debtap解包
```bash
yay -S debtap

sudo debtap -u
```

### 输入法
```bash
sudo pacman -S fcitx5-im 
sudo pacman -S fcitx5-chinese-addons fcitx5-pinyin-zhwiki 
```

```bash
vim /etc/environment

GTK_IM_MODULE=fcitx5
QT_IM_MODULE=fcitx5
XMODIFIERS=@im=fcitx5
SDL_IM_MODULE=fcitx5
```

```bash
vim ~/.bashrc

export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx 作者：st-_-st https://www.bilibili.com/read/cv24967541/ 出处：bilibili
```

### ssh-key
```bash
ssh-keygen -t ed25519 -C "email"
```

### 修改文件/文件夹所属

防止有的内容变成root导致原本用户无法使用和更改  
单改文件取消 `-R`  
```bash
sudo chown -R <用户名> <文件夹名>
sudo chgrp -R <用户名> <文件夹名>
```



## nvm (nodejs)
### archlinux:
```bash
yay -S nvm
```
然后把初始化文件倒入rc
```bash
echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.bashrc
```
然后安装node:
```bash
nvm install node
```

## go
[安装](https://go.dev/doc/install)
或者：
```bash
yay -S go
```



该文件是我在第一次安装完nvchad之后写的，里面包含了一个go插件，不知道是不是插件帮助我安装的还是啥，直接就有了，之前有没有没测试过

## lazygit
https://github.com/jesseduffield/lazygit
```bash
ln /home/ogios/app/lazygit /usr/bin/lazygit
```
host: 
```bash
140.82.113.3 github.com
```

## ripgrep

```bash
sudo pacman -S ripgrep
```




## lf
https://github.com/gokcehan/lf/wiki/Packages  
[配置](https://github.com/ogios/lf-personal-settings)
```bash
echo "source ~/.config/lf/lfcd.sh" >> ~/.bashrc
cho "alias lf=lfcd" >> ~/.bashrc
```

## fzf
```bash
yay -S fzf
```

## pistol-git
```bash
go install github.com/doronbehar/pistol/cmd/pistol@latest
```



## 聊天软件
https://yaocc.cc/archwine/
```bash
yay -S com.qq.tim.spark
yay -S deepin-wine-wechat
yay -S com.qq.weixin.work.deepin-x11
```

## 音乐
```bash
yay -S netease-cloud-music
```
