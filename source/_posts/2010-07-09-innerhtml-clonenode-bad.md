---
layout: post
title: innerHTML和cloneNode表现的很不好
date: 2010-07-09
categories:
- dev
tags:
- 前端
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  dsq_thread_id: '404521157'
---
有时候需要把表单里的元素复制出来，这里有两个方法，一是先去innerHTML，然后在innerHTML到其他的地方；二是cloneNode(true)出来到其他地方，但是这个两个方法在各个浏览器仅仅是对普通的表单的元素都是支持不完善的，甚至IE自己的系列都有变化。

以下是支持列表，yes表示会把值复制出来，no表示不会。其实还有包括表单元素的自定义属性，事件等也是各有千秋，我实在是懒得列举。
<table cellspacing="0" cellpadding="0" border="1">
  <tr>
    <td width="138">innerHTML</td>
    <td width="72">IE6</td>
    <td width="72">IE7</td>
    <td width="72">IE8</td>
    <td width="72">FF</td>
    <td width="88">Chrome</td>
  </tr>
  <tr>
    <td>input[text]</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <td>input[checkbox]</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <td>input[radio]</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <td>select</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <td>textarea</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
  </tr>
</table>
<p></p>
<p></p>
<table cellspacing="0" cellpadding="0" border="1">
  <tr>
    <td width="138">cloneNode</td>
    <td width="72">IE6</td>
    <td width="72">IE7</td>
    <td width="72">IE8</td>
    <td width="72">FF</td>
    <td width="88">Chrome</td>
  </tr>
  <tr>
    <td>input[text]</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>input[checkbox]</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
    <td>yes</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>input[radio]</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
    <td>yes</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>select</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <td>textarea</td>
    <td>yes</td>
    <td>yes</td>
    <td>yes</td>
    <td>no</td>
    <td>no</td>
  </tr>
</table>


解决上面的最保险的方法是对每一个元素类似这样:
<pre lang="javascript">
var aClone = dClone.getElementsByTagName('SELECT');
var aSelect	 = dSelect.getElementsByTagName('SELECT');

if( aClone.length > 0 && aClone.length == aSelect.length ){
	for( var i = 0, len = aClone.length; i < len; i++ ){
		aClone[i].selectedIndex = aSelect[i].selectedIndex;
	};
}</pre>
随即，附送美图一张：
<a href="http://www.yeahxj.com/wp-content/uploads/2010-outing.jpg"><img class="alignnone size-medium wp-image-301" title="2010-outing" src="http://www.yeahxj.com/wp-content/uploads/2010-outing-300x63.jpg" alt="" width="300" height="63" /></a>
点击小图看大图，这次outing最欢畅的就是住五星，很豪华很奢侈！
