---
layout: post
title: 网页缓存机制分析
date: 2009-07-20
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  edg_digg_count: '0'
  _edit_last: '1'
  _wp_old_slug: ! '%e7%bd%91%e9%a1%b5%e7%bc%93%e5%ad%98%e6%9c%ba%e5%88%b6%e5%88%86%e6%9e%90'
  dsq_thread_id: '438218190'
---
<p>最近在做一个项目，是关于页面提速的。页面提速的方法有很多，建议看看<a href="http://developer.yahoo.com/performance/rules.html" target="_blank"><font color="#006091">Yahoo!网站性能最佳体验的34条黄金守则</font></a>，当然提速最明显的就是使用缓存，所以我们先关注缓存！</p>
<div>&nbsp;&nbsp;&nbsp; 五种常用于控制客户端缓存的头标<br />
&nbsp;&nbsp;&nbsp; <strong>Last-Modified (最后修改时间)&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;ETag (实体标签)&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;Expires (有效指示) <br />
&nbsp;&nbsp;&nbsp; Pragma (编译指示)&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;Cache-Control (缓存控制) </strong></div>
<div><strong>&nbsp;&nbsp;&nbsp; Expires、Cache-Control、Last-Modified、ETag</strong>是RFC 2616（HTTP/1.1）协议中和网页缓存相关的几个字段。前两个用来控制缓存的失效日期，后两个用来验证网页的有效性。<strong>Pragma</strong>是HTTP/1.0中一个较弱的控制协议。</div>
<div>&nbsp;&nbsp;&nbsp; <strong>Expires</strong>字段声明了一个网页或URL地址不再被浏览器缓存的时间，一旦超过了这个时间，浏览器都应该联系原始服务器。RFC告诉我们：&ldquo;由于推断的失效时间也许会降低语义透明度，应该被谨慎使用，同时我们鼓励原始服务器尽可能提供确切的失效时间。&rdquo;
<div>&nbsp;&nbsp;&nbsp; 对于一般的纯静态页面，如html、gif、jpg、css、js，默认安装的Apache服务器，不会在响应头添加这个字段。Firefox浏览器接受到相应后，如果发现没有Expires字段，浏览器根据文件的类型和&ldquo;Last-Modified&rdquo;字段来推断出一个合适的失效时间，并存储在客户端。推测出的时间一般是接受到响应时间后的三天左右。</div>
<div>
<div>&nbsp;&nbsp;&nbsp; 对于动态页面，如果在页面内部没有通过函数强制加上Expires，例如header(&rdquo;Expires: &rdquo; . gmdate(&rdquo;D, d M Y H:i:s&rdquo;) . &rdquo; GMT&rdquo;)，Apache服务器会把Wed, 11 Jan 1984 05:00:00 GMT作为Expires字段内容，返回给浏览器。即认为动态页面总是失效的。而浏览器仍然会保存已经失效的动态页面。</div>
<div>&nbsp;&nbsp;&nbsp; 可以发现Firefox浏览器总是缓存所有页面，不管失效、不失效还是没有声明失效时间。即使缓存中声明了一个网页的实效日期是1970-01- 01 08:00:00，浏览器仍然会发送该文件在缓存中的Last-Modified和ETag字段。如果在服务器端验证通过，返回304状态，浏览器就还会使用此缓存。</div>
<div>&nbsp;&nbsp;&nbsp; <strong>Last-Modified</strong>这个头标是一个响应头标，表示客户端(通常指浏览器)所请求资源在服务器端的最后修改时间，通常情况下客户端在接受这个头标后，在以后对这个资源的请求会附带一个'If-Modified-Since'请求头标，而这个头标是想告诉服务器上次客户端所请求资源的最后修改时间，对于一些图像,css,js等静态文件资源，配置好了的apache服务器会理解这些If-Modified-Since请求头标，将头标里的时间和文件的最后修改时间进行比较并作出响应，如果二者相等则发送一个304 Not Modfied来告诉客户端所请求资源并未修改让客户端放心使用缓存中的资源，否则的话会重新发送一个新的资源和新的Last-Modified的头标。但是对于一个动态的PHP脚本，我们即使在脚本加入了header('Last Modified: '.$time)来发送一个Last Modified响应头标，当客户端附带'If-Modified-Since'在次请求时apache服务器不会进行处理，这需要我们自己用$_SERVER['HTTP_IF_MODIFIED_SINCE']来获取'If-Modified-Since'的值自己来进行判断处理。</div>
<div>&nbsp;&nbsp;&nbsp;&nbsp; <strong>Cache-Control</strong>字段中可以声明多些元素，例如no-cache, must-revalidate, max-age=0等。这些元素用来指明页面被缓存最大时限，如何被缓存的，如何被转换到另一个不同的媒介，以及如何被存放在持久媒介中的。但是任何一个 Cache-Control指令都不能保证隐私性或者数据的安全性。&ldquo;private&rdquo;和&ldquo;no-store&rdquo;指令可以为隐私性和安全性方面提供一些帮助，但是他们并不能用于替代身份验证和加密。
<div>&nbsp;&nbsp;&nbsp;&nbsp; Apache的mod_cern_meta模块允许文件级Http响应头部的控制，同时它也可以配置Cache-Control头（或任何其他头）。响应头文件是放在原始目录的子目录中，根据原始文件名所命名的一个文件。具体用法请参阅Apache的官方网站。其中Cache-Control : max-age表示失效日期。如果没有启动mod_cern_meta模块，Apache服务器会把Expires字段中的日期换算成以秒为单位的一个 delta值，赋值给max-age。如果启动mod_cern_meta模块，并且配置了max-age值，Apache会将这个覆盖Expires字段。同时，max-age隐含了Canche-Control: public。这样浏览器接受到的Cache-Control : max-age和Expires值就是一致的。</div>
<div>&nbsp;&nbsp;&nbsp; 如果失效日期Cache-Control : max-ag=0或者是负值，浏览器会在对应的缓存中把Expires设置为1970-01-01 08:00:00。</div>
<div>&nbsp;&nbsp;&nbsp; <strong>ETag</strong>(Entity Tag)和Last-Modified类似，也是WEB服务器和客户端用于确认缓存组件的有效性的一种机制，apache 1.3和2.0的ETag格式是inode-size-timestamp，因此当资源被修改，其ETag也发生改变，ETag相对Last-Modified更精确，Last-Modified只能精确的s级别，但是ETag在多服务器可能造成混乱，所以用还是不用还得看实际情况，其相对应的后续请求头标为If-None-Match。</div>
</div>
</div>
</div>
