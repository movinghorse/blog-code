---
layout: post
title: 争论：为什么Firefox的Javascript速度无法超越其它浏览器
date: 2010-03-05
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '3'
  dsq_thread_id: '404521041'
---
<a href="/wp-content/uploads/firefox-chrome-ie.png"><img class="size-full wp-image-248" title="firefox-chrome-ie" src="/wp-content/uploads/firefox-chrome-ie.png" alt="firefox-chrome-ie" width="225" height="207" /></a>

有道 "Firefox在速度上暂时落后于chrome safari和opera。原因并不是Mozilla技术差，而是因为其他浏览器支持的javascript，只是Firefox的一个子集，有很多东西，被其他浏览器忽略了。
<strong> 1)只有Firefox支持E4X：</strong>
E4X是一个javascript的附加标准，用于在javascript里简便快速的操作XML。有多方便？
<strong> 2) 只有Firefox在逐步实现ECMAScript5:</strong>
ECMAScript5是下一代javascript标准，目前的Firefox已经包含了很多ECMAScript5的特性，而其他浏览器似乎并没有公布相关的计划。ECMAScript5是一个已经发布了的标准，和遥遥无期的HTML5比起来，实现ECMAScript5要务实得多。
<strong> 3) Firefox在javascript和html的交互上更加优化：</strong>
HTML中部分属性，只有Firefox才能通过js去调用，其他浏览器只能写成静态html标签,目前浏览器脚本速度测试用的都是1999年的标准。10年前的标准不可能永远用下去。先实现标准，再进行速度优化，这才是正道。相信脚踏实地的Firefox可以走得更远。"

有说法：

1.HTML5不是遥遥无期，只是未到主流开发者使用。
话说DIV+CSS都不知道流行多少年了，但是好多网站还是用Table。也不怪得浏览器中IE使用率其高，因为Javascript 还不是用户浏览一般网站的核心障碍，开得舒心就行了，所以你们开发者就想着怎么给IE6 hack。是不是DIV+CSS？是不是XHTML Strict？是不是HTML5？关用户什么事。
应用比技术更重要一点。有了Gmail、Google Wave才用得着高速的Js解释功能，没有网银的话还是IE、Windows的世界。

2.<strong>为什么IE总是慢于其他浏览器：</strong>美国有多少人要求浏览器默认关闭javascript，再看看中国人，他妈连javascript是什么都不知道。

3.美国有多少人要求浏览器默认关闭javascript，再看看中国人，他妈连javascript是什么都不知道。
