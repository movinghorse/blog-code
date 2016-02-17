---
layout: post
title: 博客搬家完成，换了主机，换到了WP，一切从头开始！
date: 2009-10-24
categories:
- think
tags:
- PJBlog WP 转换
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '2'
  _wp_old_slug: ! '%e5%8d%9a%e5%ae%a2%e6%90%ac%e5%ae%b6%e5%ae%8c%e6%88%90%ef%bc%8c%e6%8d%a2%e4%ba%86%e4%b8%bb%e6%9c%ba%ef%bc%8c%e6%8d%a2%e5%88%b0%e4%ba%86wp%ef%bc%8c%e4%b8%80%e5%88%87%e4%bb%8e%e5%a4%b4%e5%bc%80%e5%a7%8b'
  dsq_thread_id: '404520685'
---
<img class="alignnone size-full wp-image-97" title="创造" src="http://www.yeahxj.com/wp-content/uploads/20070424143801851240.jpg" alt="创造" width="500" height="685" />
用了两年的Win主机和PJBlog终于退场了，主机是用钱买的，没必要感谢。PJBlog是免费用的，感谢下腾讯的<a title="PuterJam" href="http://www.pjhome.net/" target="_blank">PuterJam</a>同学，此asp博客已经灰常不错了！

既然都换了，但是数据还是要啊，所以得把原来在PJBlog中的数据导入到WP中，这里介绍我使用的一种简单方法。

WP支持多种格式的导入，常见的有SQL等，我用的RSS标准的XML文件，这个及其方便。

<strong>使用RSS2.0 XML文件从PJBlog博客导入数据岛WP平台</strong>

1. 首先要修改feed.asp文件，找到SQL = "SELECT TOP 10 L.log_ID,L.log_Title,l.log_Author,L.log省略，这里TOP 10是你要修改的数值，要全部导出就删掉TOP 10好了，数字多少自己斟酌，因为WP默认只能导入2M以内的文件。

2. 然后在你浏览器里访问http://你的域名/feed.asp，然后保存源文件。

3. 我以为现在直接导入就OK了，在这里我告诉你，不行的。两者的定义是不一样的。主要有一个，WP的内容定义是&lt;content:encoded&gt;&lt;/content:encoded&gt;,然后你在编辑器里批量替换就行了。WP的定义很多，我没有一一核对，当然你要向知道，可去读文档（我不知道文档在哪儿），你也可以随便发片文章，然后在WP导出，看看他导出是什么样子的，对比下就清楚了！我就是这么搞的！

<strong>我没有把以前所有的文章都导进来，因为我之前很多的文章都是转的，现在我要开始原创。伟人说：当你不会的时候你要先学会模仿，当你会了，你要学会创造。</strong>

<strong>PS：最早之前的订阅的地址有变化，麻烦又订阅的重新订阅！
</strong>
