---
layout: post
title: "利用Github Pages搭建博客（2021年版）"
date : 2021-08-29 17:00:00 +8000
categories: 工具
---

本文主要介绍如何使用Github的服务搭建一个博客，这个方案对优缺点是什么，以及对博客这一类媒介的再度思考。

[Github Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)是Github公司提供的一种网页托管服务，用户可以上传符合约定格式的文档到指定的代码库中，Github会自动编译成静态页面，并发布到互联网上。这个服务已经发布了很久，很多人用他来发布博客，或者产品介绍页面等。

# 安装本地环境

为了能够充分的使用Github Pages提供的强大功能，建议还是在本地先搭建一个开发环境。接下来会以Ubuntu 2020LTS操作系统作为样例进行说明。

在系统层面，主要安装ruby这个语言和相关依赖，因为我们使用的Jekyll方案是基于ruby开发的。另外还需要安装一些系统编译工具如build- essentials等。这里面的坑不少，建议大家参考这位微软MVP的[博文](https://seankilleen.com/2020/07/building-my-jekyll-blog-with-ubuntu-on-wsl2/)，把所有的依赖都安装上。

```
sudo apt-get install ruby-full # 安装ruby
sudo apt-get install make gcc gpp build-essential zlib1g zlib1g-dev # 安装各类编译依赖
gem install bundler # 安装ruby的包管理软件bundler
gem install jekyll # 安装静态站点生成工具Jekyll
```

在软件层面，我们需要安装ruby的静态网站生成软件Jekyll。安装完成后，即可使用`jekyll new site-name`命令生成一个新的站点。Jekyll会自动创建符合规范的文件夹结构和一些配置文件。其中比较重要的是Gemfile，这个文件约定了ruby会安装哪些依赖的包，有点像使用python pip加载requirements.txt来安装python包。根据Github的要求，需要注释掉Gemfile中的jekyll包，并加上github-pages包。

在构建站点的层面，我们可以修改同一目录下的_config.yml文件，对站点进行全局配置，比如站点的名称，说明，联系方式等，也可以根据安装的不同主题，进行主题相关的配置。

最后，新增博客文章需要在_posts文件夹中增加一个符合Jekyll规范的md文件。后面Jekyll会根据约定将这些文件编译为html文件。

md文件名需要是：`YEAR-MONTH-DAY-title.md`

内容需要以以下格式开头

```
---
layout: post
title: Awesome first post
---
```

以上所有准备步骤完成后，可以使用`jekyll serve`命令进行初次编译以及在本地查看。如果显示需要root权限的话，使用`bundle exec jekyll serve`即可。

预览没有问题后，我们就可以通过git将当前的代码推送到Github的远程仓库上，如果对git操作不是很熟练，可以使用客户端工具，比如VSCode。GitHub会自动编译并将结果发布到互联网上，当中的延迟可能有一分钟左右。

# 定制化

如果有兴趣，可以对站点的一些定制化工作。我对自己的站点主要做了3个优化：

1. 在[关于我]({{ site.github.url }}/about/)页面使用Jekyll的模板语法增加按分类展示文章的列表
2. 修改博客文章中的图片存放位置
3. 美化代码显示效果

1的样例代码如下

```html
{% raw %}
{% for category in site.categories %}
<h4>
  <div id="{{ category | first}}"> {{category | first}}</div>
</h4>
  <ul>
  {% for posts in category %}
    {% for post in posts %}
      {% if post.url %}
      <li>
        <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </li>
      {% endif %}
    {% endfor %}
  {% endfor %}
  </ul>
{% endfor %}
{% endraw %}
```

在Jekyll中增加图片，需要做两件事

1. 将图片放置于`/images/`
2. 在博客文章中应用自己站点的图片时需要使用`![]({{ site.github.url }}/images/.../some.jpg)`语法
3. 如果使用自己的域名，在`_config.yml`中配置自己的站点的域名即可

最后是样式修改。我使用的是默认的minima主题，觉得已经满足我的审美要求，但是文章中的代码块没有使用好看的等宽字体，看了一下minima的样例站点，它使用的css是styles.css，而默认生成的站点是main.css。

参考这篇给Jekyll增加自定义样式的[文章](https://lzone.de/blog/How-to-use-custom-CSS-with-Jekyll-Minima-theme)及Jekyll[官方文档](https://jekyllrb.com/docs/step-by-step/07-assets/)，我发现需要在Jekyll的基础上，增加定制化的css。我的做法比较简单暴力，把minima样例站点的各种_include文件复制到本地开发环境。重新构建后，站点使用了定制化的css，并且给pre code标签加上了期望的等宽字体样式。
