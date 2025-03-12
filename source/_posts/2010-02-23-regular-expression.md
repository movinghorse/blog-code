---
layout: post
title: 正则性能
date: 2010-02-23
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '1'
  dsq_thread_id: '404520875'
---
<a href="/wp-content/uploads/c728354.jpg"><img src="/wp-content/uploads/c728354.jpg" alt="正则表达式" title="正则表达式" width="500" height="307" class="size-full wp-image-219" /></a>
<pre lang="javascript" line="1">
var r = /^\w+?([\.]?[a-zA-Z0-9\-]+)*?@[a-zA-Z0-9]+([-.][a-zA-Z0-9]+)*\.[a-zA-Z]+$/;
var s = r.test('asdfasdfasdfasdfasdfasdfasdfasdfasdsdffgggasdfa');
alert(s);
</pre>
这个正则表达式导致浏览器死掉，包括chrome。
先记录在这，回头看看正则的实现，感觉好像是和编译原理有关的东西，可惜大学时的这堂课没有学好啊！
