生成网站:
> https://bashrcgenerator.com/
> https://www.kirsle.net/wizards/ps1.html

使用效果:
![[Pasted image 20220628010604.png]]
```shell
# Custom bash prompt via kirsle.net/wizards/ps1.html
export PS1="\[$(tput bold)\]\[$(tput setaf 6)\]\t \[$(tput setaf 2)\][\[$(tput setaf 5)\]\h\[$(tput setaf 4)\]#\[$(tput setaf 3)\]\u\[$(tput setaf 1)\]@\[$(tput setaf 3)\]\h \[$(tput setaf 6)\]\w\[$(tput setaf 2)\]]\[$(tput setaf 4)\]\\$ \[$(tput sgr0)\]"
```

修改主机名（方便显示）

```shell
hostnamectl set-hostname centos
```

查看主机名
```shell
hostnamectl status
```