---
layout: post
title: "Jekyll博客搭建指南"
date : 2015-11-27 21:47:21 +8000
categories: meta
---


我最早的博客在[blogger](http://pp2moonbird.blogspot.com)上，然后你懂的，在墙外很不方便。于是去年买了一个域名，然后在新浪云上搭了一个wordpress。但是新浪云有流量限制，还得做实名身份验证，最后那个博客也弃用了。最近github和markdown用的比较多，想起以前看到阮一峰老师介绍Jekyll和github-pages的[文章](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)，于是就实际操练了一把。总的来说这个solution发布文章很方便，页面速度很快，而且支持markdown，语法高亮，我还是很满意的。不过整个过程中坑还是比较多，这里记录一下。

Github-pages是github的一个服务，可以让用户把网页托管在github上。Jekyll是ruby的一个静态博客生成工具。

## Install Jekyll ##
我在Centos下进行Jekyll的安装，坑还是蛮多的。主要参考的是github-pages关于Jekyll的[文档](https://help.github.com/articles/using-jekyll-with-pages/)

首先得安装ruby, bundler

	yum install ruby
	gem install bundler

然后安装Jekyll，因为ruby官方的源速度很慢，首先得把gem的源改成[taobao的源](https://ruby.taobao.org/)

	gem sources --remove http://rubygems.org/  
	gem sources -a http://ruby.taobao.org/  
	gem sources -l  

我用的是bundle的方式安装，可以参考淘宝的文档，使用这种方式修改gem源

	bundle config mirror.https://rubygems.org https://ruby.taobao.org

然后在一个自定义的目录里创建一个Gemfile，内容就是安装`github-pages`

	gem 'github-pages'

在这个目录里运行bundle进行安装

	bundle install 

### 解决依赖的问题 ###
安装Jekyll出现了很多包缺失的问题，这里列出我所遇到的，各位可以按照实际的错误日志依次安装依赖的包

	yum install ruby-devel
	yum install gcc	
	yum install zlib-devel	
	yum install patch
	yum install libxml2-devel

## Use Jekyll ##
Jekyll安装完毕之后，使用起来就很方便了。主要可以参考Jekyll的[文档](http://jekyllrb.com/docs/quickstart/)
	
	jekyll new site_name

Jekyll会自动创建一个目录，然后进入这个目录

	jekyll serve

访问`localhost:4000`就可以看到博客了

### Write posts ###
要写一篇新的文章，需要到`/_posts`目录下面创建指定格式的markdown文件
格式必须是

	YEAR-MONTH-DAY-title.MARKUP

然后这个文件的开头也必须遵守[`Front Matter`](http://jekyllrb.com/docs/frontmatter/)的规定

	---
	layout: post
	title: Blogging Like a Hacker
	---

### Other Configuration ###
`_config.yml` 里面有很多配置项，也都可以参考文档进行配置

## Publish to github-pages ##
github提供了github-pages服务可以托管各种页面，用户需要首先申请一个特定的repo `username.github.io`, 然后把Jekyll生成的博客目录全部push上去就可以了

	yum install git
	git init
	git clone https://github.com/username/username.github.io
	// create jekyll site, write some posts
	git push https://github.com/username/username.github.io
	
本来以为每次写了文章之后还需要`jekyll build`, 结果好像github自动支持，文章push到repo上后，就会被自动build，非常方便

## Config DNS ##
如果你跟我一样是一个顶级域名的话，可以参考这个[文档](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/)

1. 域名商那边添加两个`A record`, 然后加上`CNAME`, 跳转到`username.github.io`
2. 在`username.github.io`中创建一个`CNAME`文件，里面写上自己的域名就好了

## Add Disqus ##
因为Jekyll是静态博客，所以无法做评论，后来发现现在的评论都有专门的平台服务了。国外比较流行的是[Disqus](http://disqus.com/)
注册一个账户，然后把Disqus的代码加入到`_layouts\post.html`里就可以了

## Conclusion ##
以上就是安装Jekyll，搭建静态博客的教程
