---
layout: post
title: 五种开源协议(GPL,LGPL,BSD,MIT,Apache)
date: 2010-04-02
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  _wp_old_slug: pen-source
  edg_digg_count: '0'
  dsq_thread_id: '404521061'
---
<a href="/wp-content/uploads/opensourceubuntu.jpg"><img class="alignnone size-full wp-image-252" title="open-source-ubuntu" src="/wp-content/uploads/opensourceubuntu.jpg" alt="" width="500" height="333" /></a>
<h3>什么是许可协议？</h3>
什么是许可，当你为你的产品签发许可，你是在出让自己的权利，不过，你仍然拥有版权和专利（如果申请了的话），许可的目的是，向使用你产品的人提供一定的权限。

不管产品是免费向公众分发，还是出售，制定一份许可协议非常有用，否则，对于前者，你相当于放弃了自己所有的权利，任何人都没有义务表明你的原始作者身份，对于后者，你将不得不花费比开发更多的精力用来逐个处理用户的授权问题。

而<a href="http://en.wikipedia.org/wiki/Open-source_license" target="_blank">开源许可协议</a>使这些事情变得简单，开发者很容易向一个项目贡献自己的代码，它还可以保护你原始作者的身份，使你至少获得认可，开源许可协议还可以阻止其它人将某个产品据为己有。以下是开源界的 5 大许可协议。
<h3>GNU GPL</h3>
<a href="http://www.opensource.org/licenses/gpl-2.0.php" target="_blank">GNU General Public Licence</a> (GPL) 有可能是开源界最常用的许可模式。GPL 保证了所有开发者的权利，同时为使用者提供了足够的复制，分发，修改的权利：
<ul>
	<li><strong>可自由复制</strong>
你可以将软件复制到你的电脑，你客户的电脑，或者任何地方。复制份数没有任何限制。</li>
	<li><strong>可自由分发</strong>
在你的网站提供下载，拷贝到U盘送人，或者将源代码打印出来从窗户扔出去（环保起见，请别这样做）。</li>
	<li><strong>可以用来盈利</strong>
你可以在分发软件的时候收费，但你必须在收费前向你的客户提供该软件的 GNU GPL 许可协议，以便让他们知道，他们可以从别的渠道免费得到这份软件，以及你收费的理由。</li>
	<li><strong>可自由修改</strong>
如果你想添加或删除某个功能，没问题，如果你想在别的项目中使用部分代码，也没问题，唯一的要求是，使用了这段代码的项目也必须使用 GPL 协议。</li>
</ul>
需要注意的是，分发的时候，需要明确提供源代码和二进制文件，另外，用于某些程序的某些协议有一些问题和限制，你可以看一下 <a href="http://www.twitter.com/PierreJoye" target="_blank">@PierreJoye</a> 写的 <a href="http://www.softwarefreedom.org/resources/2008/compliance-guide.html" target="_blank">Practical Guide to GPL Compliance</a> 一文。使用 GPL 协议，你必须在源代码代码中包含相应信息，以及协议本身。
<h4>GNU LGPL</h4>
GNU 还有另外一种协议，叫做 LGPL （<a href="http://www.opensource.org/licenses/lgpl-2.1.php" target="_blank">Lesser General Public Licence</a>），它对产品所保留的权利比 GPL 少，总的来说，LGPL 适合那些用于非 GPL 或非开源产品的开源类库或框架。因为 GPL 要求，使用了 GPL 代码的产品必须也使用 GPL 协议，开发者不允许将 GPL 代码用于商业产品。LGPL 绕过了这一限制。
<h3>BSD</h3>
BSD 在软件分发方面的限制比别的开源协议（如 GNU GPL）要少。该协议有多种版本，最主要的版本有两个，新 BSD 协议与简单 BSD 协议，这两种协议经过修正，都和 GPL 兼容，并为开源组织所认可。

新 BSD 协议（3条款协议）在软件分发方面，除需要包含一份版权提示和免责声明之外，没有任何限制。另外，该协议还禁止拿开发者的名义为衍生产品背书，但简单 BSD 协议删除了这一条款。
<h3>MIT</h3>
<a href="http://www.opensource.org/licenses/mit-license.php" target="_blank">MIT 协议</a>可能是几大开源协议中最宽松的一个，核心条款是：

该软件及其相关文档对所有人免费，可以任意处置，包括使用，复制，修改，合并，发表，分发，再授权，或者销售。唯一的限制是，软件中必须包含上述版权和许可提示。

这意味着：
<ul>
	<li>你可以自由使用，复制，修改，可以用于自己的项目。</li>
	<li>可以免费分发或用来盈利。</li>
	<li>唯一的限制是必须包含许可声明。</li>
</ul>
MIT 协议是所有开源许可中最宽松的一个，除了必须包含许可声明外，再无任何限制。
<h3>Apache</h3>
Apache 协议 2.0 和别的开源协议相比，除了为用户提供版权许可之外，还有专利许可，对于那些涉及专利内容的开发者而言，该协议最适合（<a href="http://www.howstuffworks.com/question492.htm" target="_blank">这里有一篇文章阐述这个问题</a>）。

Apache 协议还有以下需要说明的地方:
<ul>
	<li><strong>永久权利</strong>
一旦被授权，永久拥有。</li>
	<li><strong>全球范围的权利</strong>
在一个国家获得授权，适用于所有国家。假如你在美国，许可是从印度授权的，也没有问题。</li>
	<li><strong>授权免费，且无版税</strong>
前期，后期均无任何费用。</li>
	<li><strong>授权无排他性</strong>
任何人都可以获得授权</li>
	<li><strong>授权不可撤消</strong>
一旦获得授权，没有任何人可以取消。比如，你基于该产品代码开发了衍生产品，你不用担心会在某一天被禁止使用该代码。</li>
</ul>
分发代码方面包含一些要求，主要是，要在声明中对参与开发的人给予认可并包含一份许可协议原文。
<h3>Creative Commons</h3>
Creative Commons (CC) 并非严格意义上的开源许可，它主要用于设计。Creative Commons 有多种协议，每种都提供了相应授权模式，CC 协议主要包含 4 种基本形式：
<ul>
	<li><strong>署名权</strong>
必须为原始作者署名，然后才可以修改，分发，复制。</li>
	<li><strong>保持一致</strong>
作品同样可以在 CC 协议基础上修改，分发，复制。</li>
	<li><strong>非商业</strong>
作品可以被修改，分发，复制，但不能用于商业用途。但商业的定义有些模糊，比如，有的人认为非商业用途指的是不能销售，有的认为是甚至不能放在有广告的网站，也有人认为非商业的意思是非盈利。</li>
	<li><strong>不能衍生新作品</strong>
你可以复制，分发，但不能修改，也不能以此为基础创作自己的作品。</li>
</ul>
这些许可形式可以结合起来用，其中最严厉的组合是“署名，非商用，不能衍生新作品”，意味着，你可以分享作品，但不能改动或以此盈利，而且必须为原作者署名。在这种许可模式下，原始作者对作品还拥有完全的控制权，而最宽松的组合是“署名”，意味着，只要为原始作者署名了，就可以自由处置。

-----------------
<strong>因为在此之前，我用了国内的一些开源程序，但是呢这些程序都是需要商业授权的，不知道能不能免费的自己搭建起来给企业用。比如说shopex，康盛的产品， PHPCMS等等。。。。
如果真用了，他们会找上门来问你要版权么？ </strong>
