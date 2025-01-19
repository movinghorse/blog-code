---
layout: post
title: 回车符 \r\n 在各个浏览器中无耻的表现
date: 2011-11-07 
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
---
先认识下回车符：


<a href="http://www.yeahxj.com/wp-content/uploads/ASR-33_21.jpg"><img src="http://www.yeahxj.com/wp-content/uploads/ASR-33_21.jpg" alt="" title="ASR-33_2" width="500" height="375" class="alignnone size-full wp-image-391" /></a>


在计算机还没有出现之前，有一种叫做电传打字机（Teletype Model 33）的玩意，每秒钟可以打10个字符。但是它有一个问题，就是打完一行换行的时候，要用去0.2秒，正好可以打两个字符。要是在这0.2秒里面，又有新的字符传过来，那么这个字符将丢失。

于是，研制人员想了个办法解决这个问题，就是在每行后面加两个表示结束的字符。一个叫做“回车”，告诉打字机把打印头定位在左边界；另一个叫做“换行”，告诉打字机把纸向下移一行。

这就是“换行”和“回车”的来历，从它们的英语名字上也可以看出一二。

后来，计算机发明了，这两个概念也就被般到了计算机上。那时，存储器很贵，一些科学家认为在每行结尾加两个字符太浪费了，加一个就可以。于是，就出现了分歧。

Unix系统里，每行结尾只有“<换行>”，即“\n”；Windows系统里面，每行结尾是“<换行><回车>”，即“\r\n”；Mac系统里，每行结尾是“<回车>”。一个直接后果是，Unix/Mac系统下的文件在Windows里打开的话，所有文字会变成一行；而Windows里的文件在Unix/Mac下打开的话，在每行的结尾可能会多出一个^M符号。
<strong>【来自f2e.aliued】</strong>


就是因为有这样分歧，回车在各个浏览器中的表现也不一致，这个很无耻。
```html
<pre lang="html4strict">
<!DOCTYPE html>
<html>
	<head>
		<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
		<title>test</title>
	</head>
	<body>
<input id="aa" type="hidden" value="" />
<textarea id="bb"></textarea>
<input id="cc" type="hidden" value="" />
<script>
	var test = document.getElementById('bb');
	test.value = 'a\r\nb';	// test.value = 'a\nb';
	alert(encodeURIComponent(test.value));
</script>
	</body>
</html>
</pre>
```
首先，在IE6,7,8中，还是比较坚持的，所有的回车都是\r\n。用encodeURIComponent出来都是%0D%0A
在IE9中，就完全改了，但还是比较坚持的，所有回车都是\n。用encodeURIComponent出来都是%0A
但是在FF或者Chrome中，对input type="hidden" 的处理是不一样的，其如果value='\r\n',用encodeURIComponent出来是%0D%0A.其他全部都是%0A

这些问题在一些带回车的内容会处理处理起来比较头疼，特别是涉及到字符限制的。回车会计算成一个字符或者两个字符，处理起来需注意。
