---
layout: post
title: 百度空间倒闭后
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - evi1m0</p>


百度公告称，4月21日起，百度空间将停止编撰更新博文，博文内容迁移后只对自己可见，百度空间内容将于2015年5月7日正式迁移到百度云，博文内容（包括字体格式、原文、图片以及视频链接）不变；博文评论、标签、私信、浏览转载及原粉丝数擦除。

随着百度空间宣布关闭后，当天下午微博上骂声一片，运营八年的百度空间内容将于5月7日正式迁移到百度云，简单的说就是百度空间倒闭了。
    
我在 13 年初的时候也有过使用百度空间作为博客内容的经历，在使用的过程中已经逐渐感受到各种令我不爽的地方，例如发表的文章经常会莫名其妙的被关闭仅自己可见，原因好像是因为文章中出现的黑客、入侵、漏洞等敏感关键字，但黑哥的文章却未被“查封”，可能错别字大法发挥了作用。

虽然越做越烂，但倒闭这个消息仍令我和几个朋友比较郁闷，其中一大原因是由于国内安全圈写文章的很多托管在百度空间，tombkeeper 在当天也发表了八卦缘由：“我比较早开始使用百度空间。在我的忽悠下，国内安全界很多人都在百度空间开设了自己的 Blog。同时，我也是改版后比较早停止使用的人。后来听说主持改版的 PM 弄完这事儿后就离开了。我写了首诗：轻轻的他走了，正如他轻轻的来。他轻轻的开会， 搞烂本来挺好的产品。给接任者，留下，一个，烂摊子。”

关于写作与博客我经历了这样几个阶段，开始刚写文章时觉得很有趣，新鲜感十足，抱着憧憬选择免费博客提供商（已经被墙），轻松的开始了“写作”之旅。但在使用的过程中发现免费博客（例如新浪、网易等）限制太多，不能任性的修改 CSS ，添加 JS 等，于是便转身购买了主机域名搭配 WordPress 做起了个人博主。这个时间周期比较长，几年后又觉得 WP 太臃肿，单纯的写作似乎不需要如此花哨的配合，便在能保留控制权限的前提下，让别人托管，自己只负责写文章。这就是我现在所使用的 Github pages + Jekyll 模式，详情搭建过程可以参考我的博文《[Github pages + Jekyll build a blog](http://linux.im/2014/12/04/blogging_with_jekyll.html)》。

百度空间倒闭了，又会有不少人踏上新的征途，但我并不希望从此那么多优秀的文章在互联网上消失，我能够体会到历经几年撰写的文章只因为提供商跑路就无法与他人分享，分享是值得尊敬的。每篇文章背后都是作者坐在荧光屏前深思熟虑敲打出来的，所以我经常会对优秀的文章进行“打赏”，至少够人家买个鸡蛋核桃补补脑。面对文章消失的问题，我在下午茶时间裸写了百度空间爬虫从而对我比较敬重的几个博客内容进行存档。

简单提一下实现过程：

1. 爬取存档页面：http://hi.baidu.com/{author}/archive ；
2. 获取所有发表过文章的年月份；
3. 爬取发表过文章月份中的博文链接；
4. 多线程进行 Wget 操作，下载到本地；

因为是轻量级爬虫，所以没有使用 BS 等多余的第三方库，效果如下：

![http://ww1.sinaimg.cn/large/c334041bgw1er0kt723qgj20qo0igwio.jpg](http://ww1.sinaimg.cn/large/c334041bgw1er0kt723qgj20qo0igwio.jpg)

脚本开源在 Github : [https://gist.github.com/Evi1m0/a3cc41690c69bce02ed3](https://gist.github.com/Evi1m0/a3cc41690c69bce02ed3)

最后无论怎样，至少我们还能留下那些年的印迹和那点儿依稀的回忆。
