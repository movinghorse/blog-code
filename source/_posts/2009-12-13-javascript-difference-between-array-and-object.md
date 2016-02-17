---
layout: post
title: javascript区别对象和数组
date: 2009-12-13
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '2'
  dsq_thread_id: '438006222'
---
<a href="http://www.yeahxj.com/wp-content/uploads/javascript-the-good-parts.jpg"><img class="size-full wp-image-133" title="javascript-the-good-parts" src="http://www.yeahxj.com/wp-content/uploads/javascript-the-good-parts.jpg" alt="Javascript 语言精粹" width="300" height="400" /></a>

<strong>看《Javascript语言精粹》上看到的，挺有意思的，权当记录。</strong>

首先知道，我们的JavaScript中的数据很简洁的。只有 undefined, null, boolean, number,string,object。

Javascript中认为数组是一个对象，所以直接通过typeof是无法检测出是否是Array还是Object的，所以判断两者可以这样做：
<pre lang="javascript" line="1">
var isArray = function(value){
return value && typeof value === 'object' && value.constuctor = Array;
}</pre>
但是在检测从不同的敞口（window）或 （frame）里构造的数组会有问题，douglas crockford给出了如下的解决方案：
<pre lang="javascript" line="1">
var isArray = function(value){
return value && typeof value === 'object' && typeof value.length === 'number' && typeof value === 'function' && !(value.propertyIsEnumerable('length'));
}
</pre>
<strong>所有的建议是如果你想要深入学习一门语言的时候，一定要看权威的著作！</strong>
