# personal-linux-setup

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
该文件是我在第一次安装完nvchad之后写的，里面包含了一个go插件，不知道是不是插件帮助我安装的还是啥，直接就有了，之前有没有没测试过

## lazygit
https://github.com/jesseduffield/lazygit
```bash
ln /home/ogios/app/lazygit /usr/bin/lazygit
```

## lf
https://github.com/gokcehan/lf/wiki/Packages  
[配置](https://github.com/ogios/lf-personal-settings)
