---
layout: post
title: "Linux派"
tags: linux, vim
issueID: 1
---

* 目录
{:toc}

## A. 派别
---
linux中实现目标有很多种方法和选择,  请理性看待它们的不同


### A1. 发行版
不同的包管理机制和软件选择哲学
* RHEL  centos    Fedora
* SuSe
* Debian     ubuntu


### A2. 界面
* CLI(tilling-wm)
* GUI


### A3. 看与思
* WYSIWYG
* WYTIWYG


### A4. 编辑器
* vim(编辑器之神)
* emacs(神的编辑器)
* others


### A5. 终端
* urxvt
* tmux
* others(gnome-terminal, putty, SecureCRT)


### A6. shell
* bash
* zsh
* others


### A7. 浏览器
* firefox(vimperator)
* others


### A8.1 鼠标, 键盘, 快捷键
![正常使用键盘鼠标](/img/normal-keyboard-mouse.gif)


### A8.2 鼠标, 键盘, 快捷键
#### 鼠标:
* thinkpad的trackpoint(小红点)
* apple的MultiTouchTrackPad(多点触控板)
* 轨迹球
* others

#### *键盘*:
* hhkb+
* ergodox (kinesis, maltron)
* others {微软4000, 机械键盘 (GH60)}

#### 快捷键:
* Ctrl-, Alt-, Meta-//Super-
* Esc, Tab, Space, Enter, F1-F12
* others


### A9. 键盘的布局
* qwerty
* dvorak, colemak


### A10. 中文输入法
* 全拼
* 双拼, 五笔





## B. 文本
---
最基本的记录信息的格式
 


### B1. 文本查找
* 正则表达式
* 逻辑或与非


### B2. 文本处理
* sed
* awk(替代excel)
* vim(vimdiff)
* perl
* python


### B3. 内容展示
* vim(sytax on)
* markdown
* wiki
* html
* LaTeX




## C. 命令行
---
command   [option]   &lt; argument &gt;


### C1. 显示器
##### 接多屏(扩展模式)

```
xrandr --output VGA1 --right-of LVDS1
```

##### 竖屏显示

```
xrandr --output VGA1 --rotate right
```

##### 显示器分辨率不自动识别

```
cvt 1920 1080 60
xrandr --newmode "1920x1080_60" 173.00 1920 2048 2576 1080 1083 1088 1120 -hsync +vsyn
xrandr --addmode VGA1 "1920x1080_60"
xrandr --output VGA1 --mode 1920x1080_60 --right-of LVDS1
```


### C2. 锁屏与待机
#### 锁屏

```
xtrlock
```

#### 待机

```
pm-suspend (S2R)
```


### C3. 防止误操作
* alias
* rm='rm -i --'
* cp='cp -i'
* mv='mv -i'
* chattr
* lsattr


### C4. 显示优化
* grep='grep --color=always'
* ls='ls --color=auto'
* tree
* pstree




### C5.1 释放磁盘空间

```
sync
umount /xxx; du -sh /xxx    **看看mount挂载的盘盖住了,下面实际保持在其它盘上的大量文件**
du -sh 二分法查找大文件

lsof|egrep '/tmp|/var'   查找关键字
lsof|grep deleted
lsof|grep '\.TMP'
echo ' ' >/tmp/xxx [**不中断服务**]
```


### C5.2 挂载磁盘空间
* fat, ntfs 必须用`-o uid=1000, gid=1000, umask=0133, fmask=0133, dmask=0022`挂载

            > 否则无法指定权限。因为权限是无法记录在磁盘空间上的，所以必须在mount时指定

* ext3, ext4  直接mount挂载

            > 用chown, chmod修改存储空间中的权限，是写在磁盘上的，重启后有效





## D. 查找
---
资料管理有序, 还需要能快捷的被找到
 


### D1. 找命令参数
* xxx --help
* man xxx


### D2. 找文件路径
* find
* locate
* which


### D3. 找其它
* dpkg -S \`which man\`
* apt-cache search xxx
* history




## E. uinx哲学
---
* 一切皆文件（特别是文本text）
* 只做一件事, 做到极致
* 互相连接
* 分层处理 (上帝的归上帝，程序的归程序)



## F. 推荐
---
* 清华申请退学博士作品(王垠)：完全用Linux工作
* http://www.solidot.org
