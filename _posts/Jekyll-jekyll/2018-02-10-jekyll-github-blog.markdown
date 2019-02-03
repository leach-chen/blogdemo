---
layout: post
title: Github+Jekyll 搭建个人网站详细教程
date:  2018-02-10 12:54:00 +0900
description: Hello World！
img: post-2.jpg # Add image post (optional)
tags: [Jekyll,GitHub]
author: # Add name author (optional)
jekyll: true
---

{{site.label1}} <a href="https://github.com/leach-chen/blogdemo" target="\_blank">Leach Chen</a> {{site.label2}}

GitHub搭建个人网站，大家在网上一搜能搜到一大把的教程，但是大部分都讲的差不多，并不能满足自己想搭建的网站详细需求。我之前在搭建本站的时候也是查了较多资料，学习了下jekyll语法，参考了几个主题模板，才把符合我需求网站搭建出来。那么今天我将详细介绍下本站从**github代码托管，jekyll安装，jekyll主题选择，jekyll目录结构，jekyll基本语法，jekyll主题修改，网站留言，访问量统计等子功能整入**的详细过程。顺便当作自己记录下吧，防止以后忘记了。<br>也欢迎大家<a href="https://github.com/leach-chen/leach-chen.github.io/" style="text-decoration: none;" target="\_blank" title="点击前往">star本站源码</a>改造成属于你自己喜欢的个人网站。

这里推荐下Git代码管理工具用<a href="https://desktop.github.com/" style="text-decoration: none;" target="\_blank" title="点击前往">Desktop</a>，文档编辑工具用<a href="https://atom.io/" style="text-decoration: none;" target="\_blank" title="点击前往">ATOM</a>，atom它是Github的一款文件编辑器，可关联git仓库，可预览Markdown文件，可以导入文件夹结构，很好用，界面看着也舒服

GitHub搭建个人网站可基于jekyll或者hexo或者其它的，我看官方提供的主题jekyll更多，样式也更好看，而且能直接链接到源码主页，所以我选择的基于jekyll搭建的，若不明白jekyll是什么东西，别急，后面会解释到，下面开始讲解本站的搭建过程。

## **第一步 网站托管**<br> ##
我们知道，一个网站要能够在任何地方都能够被访问，那么需要部署到服务器上。其实github就提供了这样的功能，只要按照github格式要求，新建一个仓库，把你的网站代码上传到里面，那么就可以在任何时候任何地方都能够访问了，那么如何搭建这个代码托管仓库呢？<br>
可参考<a href="https://pages.github.com/" style="text-decoration: none;" target="\_blank" title="代码托管">官方链接</a>，我这也把步骤写出来。<br><br>
**1.**首先你要到<a href="https://github.com/" style="text-decoration: none;" target="_blank" title="点击前往">GitHub</a>上注册一个账号,例如我注册的用户名为：leach-chen（用户名可以在设置里改）<br><br>
**2.**点击New repository-->输入仓库名称格式为：用户名.github.io(如：leach-chen.github.io)->点击Create repository<br>
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/1.png" width = "300px" height = "300px" style="float:left"/>

"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/2.png" width = "300px" height = "300px"/><br>
**3.**浏览器里访问<a href="https://leach-chen.github.io/" style="text-decoration: none;" target="_blank"  title="点击前往">https://leach-chen.github.io/</a>,可以发现这个url可以被访问了，你可以把改仓库拉取到本地，然后在里面新建一个index.html的文件,在里面输入任意内容，然后再把代码推送到git上，然后再访问改链接，可以发现index.html里面的内容被访问到了。<br><br>
到这里，一个免费且无限流量的github代码托管仓库就创建完成了。
## **第二步 Jekyll安装**<br> ##
首先解释下什么是jekyll，jekyll相当于一个编译工具，安装好jekyll后，你可以通过jekyll创建一个网站模板，创建好之后，我们就可以通过http://127.0.0.1:4000/访问刚刚创建的网站了（具体jekyll用法后面再介绍），我们可以实时修改刚刚创建的模板里面的内容，并可以实时通过本地url预览改动后的效果。我们把这个博客推送到上一步创建的代码仓库里，再通过<a href="https://leach-chen.github.io/" style="text-decoration: none;" target="_blank"  title="点击前往">https://leach-chen.github.io/</a>就可以访问到博客里面的内容了。有了Jekyll，我们不用每次改动一点点就把代码推送到仓库中进行预览，而是本地就可以预览。GitHub支持jekyll，hexo等语法解析。

那么如何安装jekyll呢？我这边暂只讲解windows下的安装步骤。

1. 首先点击下载安装<a href="https://rubyinstaller.org/" style="text-decoration: none;" target="_blank"  title="点击前往">Ruby installer</a>;
2. 点击下载<a href="https://rubygems.org/pages/download" style="text-decoration: none;" target="_blank"  title="点击前往">RubyGems</a>,下载完成后解压至你想放的位置，例如我放到E:\Software\Install\StudySoftware\rubygems-2.7.4。
打开命令行执行：<br>
>cd E:\Software\Install\StudySoftware\rubygems-2.7.4 //进入到解压包的位置<br>
>E:<br>
>ruby setup.rb
3. 在命令行执行gem install jekyll；
4. 安装完成，我们可以用jekyll命令创建一个博客模板,打开命令行执行：<br>
>cd d:<br>
>d:<br>
>jekyll new testblog<br>
>cd testblog<br>
>jekyll server<br>
在浏览器输入http://127.0.0.1:4000/即可浏览刚刚创建的blog

到此jekyll 就安装完成了。

## **第三步 Jekyll 主题选择**<br> ##
1. 上一步我们完成了jekyll的安装，默认创建的博客模板一般比较简单，jekyll官网提供了大量博客模板，我们可以去挑选一个自己喜欢的博客模板，然后在这个博客基础上修改到满足自己需求的博客
2. 点击前往<a href="http://jekyllthemes.org/" style="text-decoration: none;" target="_blank"  title="点击前往">jekyll 主题官网</a>
3. 我选择的<a href="http://jekyllthemes.org/themes/adam-blog/" style="text-decoration: none;" target="_blank"  title="点击前往">adam-blog</a>这篇主题<br>
点击Homepage可以链接到该blog Github页面，点击download可以下载该博客源码，点击demo可以预览该博客效果
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/blog_demo.png" height = "300px"/><br>
4. 我们点击download，将该源码下载下来，命令行进入该目录执行jekyll server，执行成功可以在控制台看到运行路径：
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/demo_start.png" height = "300px"/>
若下载的主题jekyll server执行失败，则用步骤二中创建的testblog目录下的Gemfile，Gemfile.lock文件替换下载的主题里面的该文件，若还不成功，则根据控制台提示的错误，可以百度到解决方案。
到此，我们已经选定了一个博客主题模板，接下来我们讲解下jekyll主题的目录结构

## **第四步 Jekyll 目录结构**<br> ##

jekyll目录结构主要包含如下目录：<br>
>_posts  博客内容<br>
>_pages  其他需要生成的网页，如About页<br>
>_layouts 网页排版模板<br>
>_includes 被模板包含的HTML片段，可在_config.yml中修改位置<br>
>assets 辅助资源 css布局 js脚本 图片等<br>
>_data 动态数据<br>
>_sites  最终生成的静态网页<br>
>_config.yml 网站的一些配置信息<br>
>index.html 网站的入口

那么这些目录是如何运作的呢？
1. 我们打开根目录下的index.html可以看到：
>---<br>
>layout: home-page<br>
>---<br>
>**html代码段**
2. 上面的home-page我们到_layouts目录下可以找到：
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/struct_home.png" height = "200px"/><br>
实际上根目录下index.html运行后是home-page里面的代码内容，1中**html代码段**会填充的上图中的**content**位置
3. 上图的default布局也可以再_layouts目录下找到：
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/struct_default.png" height = "200px"/><br>
实际上根目录下index.html运行后,home-page.html里面的代码内容会填充到上图中的**content**位置<br>
jekyll是将分散在各个目录下的html文件拼接起来运行。<br>
4. **<a href="http://jmcglone.com/guides/github-pages/" style="text-decoration: none;" target="_blank"  title="点击前往">文章链接</a>这里有篇讲的比较好的，跟着该文章里的操作，能让你更熟悉**<br>

## **第五步 Jekyll 语法**<br> ##

上一步大概讲解了下Jekyll的目录结构，现在我们讲解下部分jekyll的语法，也可去官方网站学习更详细**<a href="http://jekyllcn.com/docs/home/" style="text-decoration: none;" target="_blank"  title="点击前往">官方链接</a>**

1. **{**% for post in paginator.posts %**} {**% endfor %**}**表示一个for循环,百分号之间的语句为要执行的语句，该段代码表示分页输出文章，分页数量在_config.yml中配置，**注意：分页只在根目录下的index.html中有效**


1. **{** site.自定义字段名称 **}** 表示获取_config.yml里面的自定义字段名称的值


1. **{**% for post in site.posts limit:2  %**} {**% endfor %**}**循环输出 2 篇文章

1. **{**%  for post in site.posts offset:0 limit:2 %**}**循环输出最新2篇文章


1. **{**% for tag in post.tags  %**} {**% endfor %**}**输出该篇文章里的tag


1. **{**% if link.type == site.blog_1  %**} {**% endfor %**}**字符串比较


1. **{**% assign count = 0 %**}****{**% assign count = count | plus: 1 %**}**定义assign变量加1


1. **\{\{**post.content \| strip_html \| strip_newlines \| truncate: 100 **\}\}**获取文章摘要，取前100个字符


1. 2018-02-10-你要添加的描述.markdown，文章命名格式，否则识别不了


1. **\{\{** page.date \| date: '%Y, %b %d' **\}\}**输出文章日期


1. **\{\{**page.title**\}\}**输出文章标题


1. **{**% if post.jekyll %**}** 判断文章里的jekyll字段是否为true


1. **{**% if paginator.previous_page %**}**是否有上一页


1. **{**% if paginator.next_page %**}**是否有下一页


1. **\{\{** paginator.previous_page_path **\}\}**上一页url


1. **\{\{** paginator.next_page_path **\}\}**下一页url


1. **\{\{** post.url | prepend: site.baseurl **\}\}**要访问的文章的url


## **第六步 修改博客模板**<br> ##

第四步中下载的博客模板发现并不完全符合自己的需求，于是做了如下修改

**1. 添加文章分类功能：**<br>
**a.** 在_config.yml中添加如下分类
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/class_part.png" height = "200px"/><br>
**b.** 在_includes目录下的header.html里面添加如下代码，该代码是循环输出分类及该分类下的文章数量
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/class_part1.png" height = "200px"/><br>
**c.**在根目录下创建博客文件夹，在里面创建对应目录，目录名称和a步骤中的url路径对应
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/class_part2.png" height = "200px"/><br>
**d.**在每个目录下创建index.html,并按如下图方式添加代码，这样就可以按分类输出文章
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/class_part3.png" height = "200px"/><br>
**2. 添加文章评论功能：**<br>
模板本身有评论功能，但是用的是国外的Disqus，Disqus在国内被屏蔽的。
主流的评论系统有Disqus, Facebook comment, IntenseDebate, Livefyre等。我这里选择的是IntenseDebate，其它的访问速度貌似较慢。<br>
去<a href="https://intensedebate.com/" style="text-decoration: none;" target="_blank"  title="点击前往">IntenseDebate</a>注册账号，并获取到key，并定义在_config.yml中，如：<br>
intensedebate_identifier: 1ce8d80a5f6d373a46f4ceaf3dff8859，intensedebate_identifier取你自己想定义的名称，值为你注册后获取到的key
在_includes目录下创建disqus.html，并添加如下代码，这样文章就有了评论功能。
"<img src="{{site.imagepath}}/assets/img/blog/jekyll/jekyll_github/class_part4.png" height = "200px"/><br>
**3. 添加文章统计功能：**<br>
我这里添加百度统计，添加谷歌统计因为被墙了，会影响文章的访问速度，添加也需要先去百度统计网站注册账户，申请key，申请到key后类似上一步定义在_config.yml中，同时会得到一段代码，把它添加到_includes目录下的head.html中,这样统计功能就添加完成

	<!--百度统计-->
    <script>
    	var _hmt = _hmt || [];
    	(function() {
    	  var hm = document.createElement("script");
    	  hm.src = "https://hm.baidu.com/hm.js?{{ site.baidu-analysis }}";
    	  var s = document.getElementsByTagName("script")[0];
    	  s.parentNode.insertBefore(hm, s);
    	})();
    </script>

**4. 添加文章访问量功能：**<br>
在_includes目录下的head.html中添加

    <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>

在_includes目录下的footer.html中添加如下代码，这样文章底部有了统计访问量功能

    <span id="busuanzi_container_site_pv">本站总访问量：<span id="busuanzi_value_site_pv"></span>次</span>

在_layouts目录下的post.html中添加如下代码，这样每篇文章有了统计访问量功能

    <span id="busuanzi_container_page_pv"> | 访问量：<span id="busuanzi_value_page_pv"></span> 次</span>

**5. 博客其它样式修改：**<br>
博客其它样式修改主要参考以下几篇博客：<br>
<a href="http://jekyllthemes.org/themes/Liberxue-Theme/" style="text-decoration: none;" target="_blank"  title="点击前往">博客模板1</a><br>
<a href="http://jekyllthemes.org/themes/bef/" style="text-decoration: none;" target="_blank"  title="点击前往">博客模板2</a><br>
<a href="http://jekyllthemes.org/themes/leopard/" style="text-decoration: none;" target="_blank"  title="点击前往">博客模板3</a><br>

到此，一个满足自己需求的个人博客网站就搭建完成。
