---
layout: post
title: 安装subversion-[学习笔记]
date: 2010-10-08
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  dsq_thread_id: '409042148'
---
subversion(简称svn)是近年来崛起的版本管理软件，是cvs的接班人。目前，绝大多数开源软件都使用svn作为代码版本管理软件。
subversion的官方网站是 http://subversion.tigris.org/
Linux真TM的，完全不能以学习Windows的方式进行了，做过一遍下次很有可能要忘记了，额的神啊，请让我做些笔记吧，虽然这些对于高手来说非常简单。

安装的方法应该有四种：
<strong>1. 下载源码，自己编译，安装。</strong>这种方法适合熟悉的用户，这里会遇到很多依赖没有安装的情况，要一个一个搞定，很是麻烦，而且需要很多的时间。当然也还是介绍下方法：
$wget http://subversion.tigris.org/downloads/subversion-deps-1.6.12.tar.gz
$wget http://subversion.tigris.org/downloads/subversion-1.6.12.tar.gz
$$ tar xvzf subversion-1.6.12.tar.gz;tar xvzf subversion-deps-1.6.12.tar.gz;
$ cd ~/subversion-1.6.12/
$./configure
$make clean
$make
$make install
这只是大致步骤，中间出现的任何问题，自己想办法处理。

<strong>2. 直接使用yum安装，这个应该是最方便的方法了。直接yum -y install subversion就OK了。</strong>
这里我遇到的问题，使用这个方法老是提示我老的版本已经是最新了，没法升级。而我看到的是使用的是http://mirrors.163.com/的。不知道是不是163的svn只有1.4的版本，望高手解答，如何修改不使用163的。

<strong>3. 使用rpm包安装，这个相对也方便，但是也要处理依赖。</strong>rpm一种用于互联网下载包的打包及安装工具，它包含在某些Linux分发版中。它生成具有.RPM扩展名的文件。
这里可以下载svn的rpm包：http://the.earth.li/pub/subversion/summersoft.fay.ar.us/pub/subversion/latest/1.6.13/rhel5/i386/
按照我的经验，下载neon，sqlite，subversion，就可以了。然后如rpm subversion-1.6.13-1.i386.rpm等等。遇到要升级什么的，使用参数rpm -ivh sqlite-3.5.9-2.i386.rpm --replacefiles

rpm举几个例子：
安装：# rpm -ivh subversion-1.6.13-1.i386.rpm
卸载：# rpm -e subversion；强力卸载：# rpm -e subversion --nodeps
升级：# rpm -Uvh subversion-1.6.13-1.i386.rpm

或许还可以直接拷贝目录吧，然后配置一下，这不就是Linux嘛，我没有试过。希望有高手可以指点。


期间还遇到一个非常复杂的问题，就是安装的时候subversion-1.6是依赖sqlite-3.4以上的，但是我的linux使用的是sqlite-3.3，所以需要升级sqlite。
但是sqlite却删除不掉，因为很多东西依赖与他。

rpm -e sqlite-3.3.6-2
error: Failed dependencies:
        libsqlite3.so.0()(64bit) is needed by (installed) rpm-4.4.2-47.el5.x86_64
        libsqlite3.so.0()(64bit) is needed by (installed) rpm-libs-4.4.2-47.el5.x86_64
        libsqlite3.so.0()(64bit) is needed by (installed) yum-metadata-parser-1.0-8.fc6.x86_64
        libsqlite3.so.0()(64bit) is needed by (installed) python-sqlite-1.1.7-1.2.1.x86_64
        libsqlite3.so.0()(64bit) is needed by (installed) apr-util-1.2.7-6.x86_64

结果我一火，将这个文件删掉了
rpm -e sqlite-3.3.6-2 --nodeps

这下完蛋了，出现了以下的错误：
error while loading shared libraries: libsqlite3.so.0: cannot open shared object file: No such file or directory
要安装sqlite，就需要rpm，而rpm又需要sqlite，死循环了。

解决办法是：
在windows中下载了sqlite-3.3.6-2.rpm ，解压出libsqlite3.so.0.8.6放在linux系统中
然后建一个链接：
ln -s /usr/lib/libsqlite3.so.0.8.6 /usr/lib/libsqlite3.so.0

这样再次安装sqlite就可以了。
