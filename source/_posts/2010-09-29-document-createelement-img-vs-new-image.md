---
layout: post
title: document.createElement("img") vs new Image()
date: 2010-09-29
categories:
- nono
tags: []
status: draft
type: post
published: false
meta:
  _edit_last: '1'
---
<img width="640" height="384" src="http://farm5.static.flickr.com/4154/5035892610_dfaef24382_z.jpg">

document.createElement("img") vs new Image() 这两个东西有一些纠结的东西。
从功能上讲，这两个应该是实现一样的东西，从专业上讲这两个东西是不是都能叫生成一个img标签，这就不得而知了。更多的区别在于一些对应的功能点和各个浏览器的区别。先把自己能够想到的区别列出，有些可能证明的不是很完全。
<strong>1. 性能</strong>
(function() {
    var imageUrl = '/image.ipg';
    var start = new Date();
    for (var i = 10000; i--;) {
      var cacheImage = document.createElement('img');
      cacheImage.src = TestImage;
     //var cacheImage = new Image();
      //cacheImage.src = TestImage;
    }
    var end = new Date();
    alert(end - start);
})()
结论：Firefox 3.5, Safari, 和Webkit浏览器基本没有明显的差异。IE6和IE7使用new Image()更快，而IE8却使用document.createElement('img')更快，IE9不知道。这个真难选择。

<strong>2. onload</strong>
document.createElement('img')在触发各个浏览器下触发onload事件有不一样，而这个方法是非常常用的，很多需要只知道图片地址，但需要调整图片高宽的地方都需要。而使用new Image()的方法在各个浏览器下触发onload都保持一致。
所以在有这样的需求的时候，请使用new Image()，不知道有没有牛人能够封装document.createElement('img')使其也能够onload，因为我没有仔细去考虑onreadystatechange。

<strong>3.垮页面问题</strong>
我们知道，如果有跨页面的情况，我们需要将创建元素这个事情放在其要append的页面。
