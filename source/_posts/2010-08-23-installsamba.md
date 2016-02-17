---
layout: post
title: 安装samba-[学习笔记]
date: 2010-08-23
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  dsq_thread_id: '404521239'
---
samba是Linux下的一个文件共享服务软件，属于必装软件。Linux命令这种东西真的需要记录，不想Windows，装过一遍，有点印象，下次一般都能搞定，真TMD的Linux。这些操作对懂的人来说应该是很简单的，权当学习笔记。
以下是RedHat和CentOS等的系统操作。
<strong>1、# yum -y install samba</strong>
使用yum命令安装samba，加入-y参数，如遇询问自动选择y，全自动下载并安装samba，此过程需要一点时间。如果是Ubuntu的话用apt-get。

<strong>2、# rpm -qa | grep samba</strong>
检查samba服务包的安装情况，会显示类似如下两个包：
samba-common-3.0.33-3.7.el5_3.1    //服务器和客户端均需要的文件
samba-3.0.33-3.7.el5_3.1                 //服务器端文件

<strong>3、# whereis samba</strong>
由于是yum安装，可以用此命令查看samba安装位置，得到类似如下内容：
samba: /etc/samba /usr/lib/samba /usr/share/samba /usr/share/man/man7/samba.7.gz

<strong>4、# vi /etc/samba/smb.conf</strong>
根据步骤3得知smb.conf的位置，配置samba：
（1）[global]        找到全局设置标签，在下面进行配置
workgroup = MYGROUP       找到此行，改为workgroup = WORKGROUP，这里以 Windows XP 默认的“WORKGROUP”为例
（2）配置最简单访问目录几个基本属性：
[share]       windows客户端查看时看到的文件夹名
path = /var/samba/share       共享目录位置，要系统中存在的目录，也可以配置完再创建
read only = no
public   = yes
我在操作的时候觉得这些都没必要的。

5、给配置的共享目录设置权限：
# mkdir /var/samba/share       如刚才配置的共享目录不存在则创建
# chown -R nobody. /var/samba/share       设置共享目录归属为 nobody
# chmod 777 /var/samba/share       将共享目录属性设置为 777

<strong>6、# smbpasswd -a username</strong>
将linux系统已存在用户 username（例）加入到 Samba 用户数据库，windows访问samba共享目录时需要输入此用户名和密码。
这步才是关键，加入这个用户之后好像会默认将这个用户的用户路径添加为共享目录。
New SMB password:       在此输入密码
Retype new SMB password:       重复密码

<strong>7、# service smb start</strong>
由于是yum安装可用此命令启动samba。

8、打开你的Windows，使用\\IP就可以访问Linux的文件了。

恭喜！

无奈最近刚刚换了电脑，重装了系统，无图不能发。
