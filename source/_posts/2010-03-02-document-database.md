---
layout: post
title: 文档数据库
date: 2010-03-02
categories:
- think
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '1'
  dsq_thread_id: '404520971'
---
<a href="http://www.yeahxj.com/wp-content/uploads/sketch.png"><img class="size-full wp-image-238" title="CouchDB" src="http://www.yeahxj.com/wp-content/uploads/sketch.png" alt="CouchDB" width="292" height="340" /></a>

事情的来源是：

1. 想了一个问题，很多表单里都有国家数据，世界上又有两百多个国家，加上如国家简写等信息，国家信息量其实挺多了，要是能够缓存在浏览器中挺好...

2. 好吧，以静态文件的形式存在，可以缓存了，这些都是资源文件，本就不应该每次都由Java程序生成...

3. 这样的资源文件都是文档，架构和我说有个叫CouchDB的针对 Web 应用程序的面向文档数据库...CouchDB 是一个开源的面向文档的数据库管理系统，可以通过 RESTful JavaScript Object Notation (JSON) API 访问...

4. 自己本是前端，通过JSON访问，那好的。本地装完，请求 curl http://127.0.0.1:5984/ 返回以下响应：{"couchdb":"Welcome","version":"0.8.1-incubating"}。

5. 文档数据库有什么好的？文件服务器很花钱...

6. TaoBao已经完全由自己开发的文件系统，而我们可能还只是用ext3，而且要花很多的钱买别人的存储解决方案

7. 我们和TaoBao已经在技术层面已经相处甚远，牛人说：<strong>小公司起来往往是销售凶猛了，大公司倒闭往往是技术落后了...</strong>
