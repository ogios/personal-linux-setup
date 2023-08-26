<!--ts-->
* [personal-linux-setup](#personal-linux-setup)
   * [基础](#基础)
      * [7zip](#7zip)
      * [时间](#时间)
      * [字体](#字体)
      * [debtap解包](#debtap解包)
      * [输入法](#输入法)
      * [ssh-key](#ssh-key)
      * [修改文件/文件夹所属](#修改文件文件夹所属)
   * [clash-gui](#clash-gui)
   * [v2raya](#v2raya)
   * [音乐播放器](#音乐播放器)
   * [waybar](#waybar)
   * [zsh](#zsh)
   * [Grub启动](#grub启动)
   * [全局配置修改 (Login manager/grub...许多)](#全局配置修改-login-managergrub许多)
   * [nvm (nodejs)](#nvm-nodejs)
      * [archlinux:](#archlinux)
   * [go](#go)
   * [lazygit](#lazygit)
   * [ripgrep](#ripgrep)
   * [lf](#lf)
   * [fzf](#fzf)
   * [pistol-git](#pistol-git)
   * [聊天软件](#聊天软件)
   * [音乐](#音乐)
<!--te-->

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


## clash-gui
https://github.com/Fndroid/clash_for_windows_pkg/releases

配置service(其实也可以不配，毕竟人家自带自启按钮，或者使用hyprland的话在hyprland的配置文件里设置启动)
```service
[Unit]
Description=Clash Proxy
After=network.target

[Service]
Type=simple
ExecStart=/**/cfw

[Install]
WantedBy=multi-user.target
```
可以开启轻量模式，具体要求看这里：
https://docs.cfw.lbyczf.com/contents/lightweight.html#%E7%89%88%E6%9C%AC%E8%A6%81%E6%B1%82


## v2raya
```bash
# 可能需要换源到官方 aur.archlinux.org
yay -S v2raya
```
会自动注册服务，之需手动开启和设置自启就好  
完事之后访问本地2017端口，设置过滤为cn大陆白名单  
之后import地址再启动，如果遇到iptables的问题，先重启（可能是clash导致的，记得关闭它）

这可能会导致ssh连接github出现密钥交换问题，切换为带有ssl的443端口
```ssh_config
Host github.com
    Hostname ssh.github.com
    Port 443
    User git
```


## 音乐播放器
> 由于网易云音乐下架linux版，故使用[YesPlaymusic](https://github.com/qier222/YesPlayMusic)代替

依赖(AppImage):
```bash
sudo pacman -S fuse2
```
desktop启动项:
```desktop
[Desktop Entry]
Type=Application
Terminal=false
Categories=music
Name=R3pMusic
Exec=/home/ogios/app/R3PLAY-2.0.0-linux.AppImage
Comment=music player to substitute netease
```

## waybar
clock如果不起作用就在shell脚本中加入如下内容:
```bash
export LC_ALL=C
```

## zsh
```
yay -S zsh
bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```
在plugins文件夹里创建一个自定义文件夹，放进去自定义的zsh脚本就行

.zshrc
```zsh
zinit ice wait'' lucid 
zinit light zsh-users/zsh-autosuggestions
zinit ice wait'' lucid 
zinit light wting/autojump
zinit ice wait'' lucid 
zinit light zsh-users/zsh-syntax-highlighting
zinit ice wait'' lucid 
zinit light StackExchange/blackbox
zinit ice wait'' lucid 
zinit light b4b4r07/enhancd
zinit ice wait'' lucid 
zinit light fcambus/ansiweather
zinit ice wait'' lucid 
zinit light zsh-users/zsh-history-substring-search
zinit ice wait'' lucid 
zinit light supercrabtree/k
# zinit light chriskempson/base16-shell
zinit ice wait'' lucid 
zinit light wfxr/forgit
zinit ice wait'' lucid 
zinit light zdharma/fast-syntax-highlighting
zinit ice wait'' lucid 
zinit light larkery/zsh-histdb
zinit ice wait'' lucid 
zinit light MichaelAquilina/zsh-you-should-use
zinit ice wait'' lucid 
zinit light iam4x/zsh-iterm-touchbar
zinit ice wait'' lucid 
zinit light unixorn/git-extra-commands
zinit ice wait'' lucid 
zinit light marlonrichert/zsh-autocomplete
zinit ice wait'' lucid 
zinit light mfaerevaag/wd
zinit ice wait'' lucid 
zinit light agkozak/zsh-z
zinit ice wait'' lucid 
zinit light mafredri/zsh-async
zinit ice wait'' lucid 
zinit light Tarrasch/zsh-autoenv
zinit ice wait'' lucid 
zinit light zsh-users/zaw
zinit ice wait'' lucid 
zinit light djui/alias-tips
zinit ice wait'' lucid 
zinit light changyuheng/fz
zinit ice wait'' lucid 
zinit light b4b4r07/emoji-cli
zinit ice wait'' lucid 
zinit light Tarrasch/zsh-bd
zinit ice wait'' lucid 
zinit light zdharma/history-search-multi-word

# Load pure theme
# zinit ice pick"async.zsh" src"pure.zsh" # with zsh-async library that's bundled with it.
# zinit light sindresorhus/pure
# zinit ice defer
zinit ice wait'' lucid 
zinit load custom

```

## Grub启动
```bash
sudo pacman -S xorg-xhost
sudo pacman -S grub-customizer
```

## 全局配置修改 (Login manager/grub...许多)
```bash
yay -S archlinux-tweak-tool-git
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
