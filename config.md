# 添加源

> [参考文档](https://www.jianshu.com/p/57a91bc0c594)

## 什么是软件源?
源,在Ubuntu下,它相当于软件库,需要什么软件,只要记得正确的软件名就可以用命令安装：
'sudo apt-get install [软件名]'

## 软件源的分类
在 Ubuntu 中软件源其实还细分为下面两种：

1. Ubuntu 官方软件源
2. PPA 软件源
	PPA 源，就是指 “Personal Package Archives” ，也就是个人软件包集。这其实是一个网站，即－launchpad.net。Launchpad 是 Ubuntu 母公司 Canonical 有限公司所架设的网站，是一个提供维护、支援或联络 Ubuntu 开发者的平台。由于不是所有的软件都能进入 Ubuntu 的官方的软件库，launchpad.net 提供了 PPA，允许开发者建立自己的软件仓库，自由的上传软件。供用户安装和查看更新。


## 为什么要替换系统默认的官方软件源？
因为 Ubuntu 的官方软件源的服务器是在国外，而从我们中国访问国外的网站都必须先经过一堵“墙”来验证这个网站是否可以访问，另外一个原因就是服务器在国外，距离远了，访问的速度当然没有直接访问国内的网站快。正是由于这种的访问检查和网络传输距离问题，导致我们通常访问 Ubuntu 官方软件源的速度很慢。因此需要替换官方源。


## 修改官方源
Ubuntu 官方软件源中包含了 Ubuntu 系统中所用到的绝大部分的软件，它对应的源列表是 `/etc/apt/sources.list`。只需要修改这个文件，就能添加我们想要的源。修改操作：

```shell
sudo vi /etc/apt/sources.list
sudo apt-get update
```

要记得刷新一下

> 国内开源镜像站点汇总：https://segmentfault.com/a/1190000000375848

# 切换为zsh-shell

>    https://github.com/Shadowmaple/something_for_ubuntu/blob/master/zsh.md


# terminator

## 简介
Ubuntu自带的终端是gnome-terminal，虽然可以用但是看多个界面的代码的话会不太方便，termaintor是
是一款非常好用的终端命令程序。

Terminator 可以在同一个窗口上分割多个子窗口，每个小窗口运行独立的命令程序。

## 安装

```shell
sudo apt-get install terminator
```

## 快捷键
| 操作 | 效果 |
| :---: | :---: |
| Shift+Ctrl+o |上下拆分屏幕|
| Shift+Ctrl+e |左右拆分屏幕|
| F11 |全屏切换|
| Ctrl + Page Down/ Page Up |切换标签页|
| ctrl+shift+right/left/up/down |  在分割的终端中将分割条向右/左/上/下移动 |
| ctrl+ shift+s |  隐藏/显示滚动条|

更多詳見終端偏好設置


## 设置默认Terminal为Terminator

    gsettings set org.gnome.desktop.default-applications.terminal exec /usr/bin/terminator
    gsettings set org.gnome.desktop.default-applications.terminal exec-arg "-x"

## 字体颜色
尽管字体颜色设为白色，但实际上显示的还是灰色，要改成全局的白色，只能在配置->色彩->前景与背景->内置方案中选择黑底白字。

## 参考资料
[terminator配置](https://www.jianshu.com/p/cee2de32ca28)


# 更改pip源
## 为什么要更改源？
下载安装python各种模块及插件的速度过慢，延迟过长。此时除了网速以外，最大的问题还在于软件源。为此需要更换国内的软件源。
几个常用的国内源：

>阿里云
http://mirrors.aliyun.com/pypi/simple/

>中国科技大学
https://pypi.mirrors.ustc.edu.cn/simple/

>豆瓣
http://pypi.douban.com/simple/

>清华大学
https://pypi.tuna.tsinghua.edu.cn/simple/

>中国科学技术大学
http://pypi.mirrors.ustc.edu.cn/simple/

## 临时换源
命令格式：sudo pip3 install 包名 -i 镜像源url

```shell
sudo pip3 install [package] -i http://mirrors.aliyun.com/pypi/simple/
```

## 设为默认
没有`.pip`文件夹，就新建一个，然后再新建 `pip.conf` 文件，编辑：

```shell
mkdir .pip
cd .pip
vi pip.conf
```

写入以下内容：

    [global]
    trusted-host = mirrors.aliyun.com
    index-url = http://mirrors.aliyun.com/pypi/simple/

现在速度就可以起飞了2333

## 安装搜狗输入法
1. 安装fcitx
```shell
sudo apt-get install fcitx
```
2. 设置，Language Support -> Keyboard input method system -> fcitx
3. 重启
4. 官网上下载安装linux版搜狗输入法
5. 重启fcitx (restart)
6. 右上角Keyboard -> Configure 添加 Sougou (有个"+"号)

ps: 搜狗输入法不要在英文键盘输入的上方，不然默认都是中文优先

# 更改终端默认编辑器

输入命令：

```shell
$ sudo update-alternatives --config editor
```

选择有 vim.basic 这项的数字就可以了