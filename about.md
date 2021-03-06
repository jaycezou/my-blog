---
layout: page
title: 关于
permalink: about.html
image: /public/images/redflag.jpg
order: 5
---

{% if site.author.photo %}
![{{ site.author.name }}]({{ site.author.photo | prepend: site.cdnurl }}){:.me}
{% endif %}

`Jayce` 是我打算一直用下去的英文名，后边购买了 `jaycezou.com` 的域名，如果可以，会一直用下去的。
从 2019 年开始，没有问题的话，至少每月发一篇博文。

目前还没什么其他可说的，如果想看我的代码可以去我的 [Github](https://github.com/jaycezou){:target="_blank"}。

## 编程理念

仰慕「优雅编码的艺术」，追崇实践 + 理论得真知。

## 版权说明

我坚信着开放、自由和乐于分享是推动计算机技术发展的动力之一。所以本站所有内容均采用[署名 4.0 国际（CC BY
4.0）](http://creativecommons.org/licenses/by/4.0/deed.zh)创作共享协议。通俗地讲，只要在使用时署名，那么使用者可以对本站所有内容进行转载、节选、二次创作，并且允许商业性使用。

## 其他

我的博客使用 Jekyll 搭建，源码托管在 [Github](https://github.com/jaycezou/my-blog){:target="_blank"}。如果你有什么想对我说的请发送邮件至 `jayce.zou@foxmail.com`，注意逻辑清晰，表明来意，否则不回复。

{% if site.comments.disqus %}
{% include disqus.html %}
{% endif %}