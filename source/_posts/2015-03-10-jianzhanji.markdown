---
layout: post
title: "博客诞生记"
date: 2015-03-10 15:11:02 +0800
description: "使用Octopress + GitHub Pages搭建博客"
keywords: octopress, github, eclipseflower, 博客
comments: true
categories: octopress
toc: true
tocstartlv: 2
---
之前看到许多小伙伴搭的博客，自己觉得挺好看的，但是由于自己感觉没有太大的需要，就没有产生过自己尝试搭博客的想法。（当然，其实一方面是因为自己比较懒）

这学期刚开始，又发现了一个小伙伴的博客，而且还在不断更新，逛了逛之后感觉挺励志（大雾）。实际上，上学期我在整理读书笔记的时候，一直被坑爹的Word排版困扰，无法满足得了我的需求。而且，每到放假的时候，我还需要把做的笔记记录等一些东西进行同步，着实不方便。这时候，我突然想到，如果把这些笔记什么的发布在网上，一来解决了我同步的琐碎问题，二来也可以方便自己随时查阅，三来还能和其他人进行交流。于是我就想自己搭一个博客了。

想到什么就要及时做什么。于是就有了这篇记录我这几天捣鼓的文章。本博客的建立过程中得到了[薇姐](http://6carol6.github.io/)和习大大、J神的大力帮助与支持，在此向他们表示感谢。（也不造他们能不能看到==）总之，ありがとうございます。
<!-- more -->
##环境配置
本博客是基于[Octopress](http://octopress.org/)和[GitHub Pages](https://pages.github.com/)搭建的。关于环境配置的教程，前面两个链接中均有较为详细的描述（不过是英文版==）。中文版的教程，主要参考了使用[github + Octopress 搭建免费博客](http://cn.soulmachine.me//blog/20130401/)和[在Github上搭建Octopress博客](http://blog.163.com/fuhaocn@126/blog/static/366650802012115103842500/)两篇博文。但是这里还是要把自己搭建环境的步骤记录，做一个备忘录。（万一哪天我又重装系统了呢）
###1.在GitHub上创建New Repository
该步骤参见[GitHub Pages](https://pages.github.com/)官网。
###2.安装配置msysgit
我安装的git版本为Git-1.8.1.2-preview20130201。配置过程前面博文均有叙述。
###3.安装Octopress
####安装ruby
我安装的ruby版本为rubyinstaller-1.9.3-p429。
####安装DevKit
我安装的DevKit版本为DevKit-tdm-32-4.5.2-20111229-1559-sfx。
####安装python
该步骤是可选的，但是如果不安装python就无法使用Octopress自带的代码高亮功能。（亲测）

我安装的python版本为ActivePython-2.7.8.10-win64-x64。别忘记安装完之后要在cmd中执行：

	easy_install pygments
####安装Octopress
参见[Octopress](http://octopress.org/)官网和前面博文。
###4.博客基本设置
修改Octopress根目录下的主配置文件_config.yml。
###5.部署到GitHub
依旧参见。这里有个小问题，就是我直接在cmd中执行

	rake setup_github_pages
时，会遇到repository地址无法识别的问题。但是换在Git Bash下执行相同的命令却解决了。所以最好还是在Git Bash下执行所有操作。

另外，不要忘记备份源文件：

	git add .
	git commit -m "your message"
	git push origin source
至此，本地环境的配置基本结束。然后差不多就可以写文章啦。markdown的语法参考见[这里](http://wowubuntu.com/markdown/)和[那里](http://www.jianshu.com/p/q81RER/)。Octoprees自带语法高亮的文档在[这里](http://octopress.org/docs/plugins/backtick-codeblock/)。
##常用命令
###rake install命令
该命令在不加任何参数情况下，安装默认的Octopress主题。所加的参数即为各种已下载的其他[第三方的主题](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes)。
###rake generate命令
该命令用于生成静态页面（即对source文件夹进行处理）。如果需要对安装好的主题进行修改，直接对source文件夹的文件进行修改，然后再运行一次本命令即可。
###rake preview命令
该命令用来本地浏览，这样可以不用每次都要上传才能看到本次修改的效果。另外，该命令是动态更新的，即如果命令不终止，每次修改都会即时生效，然后直接即可本地预览，而不用每次都要重新generate然后再preview，是非常好用的命令。
###rake deploy命令
该命令用于将本地修改自动发布到GitHub上的master分支，然后可以就可以访问看到效果了。
##自定义设置
1、默认首页显示摘要

在markdown文件中合适的地方插入下面的代码

	 <!-- more -->
就会生成一个Read on。

2、添加多说评论框

该设置主要参考[Ocotpress集成多说评论](http://droidyue.com/blog/2014/07/29/integrate-duoshuo-in-octopress/)。

3、主题

本博客使用的主题为[fabric](https://github.com/panks/fabric#tapirgo-search)，并在此基础上进行修改。

4、目录插件

Octopress的markdown解释器不带目录，我又懒得换，所以找了插件来用。教程见[Octopress易筋经，目录表ToC](http://khaos.github.io/blog/2012/12/05/generating-toc-in-octopress/#jquerytoc)。

##问题整理
###1.执行rake generate命令时出现的"invalid bad byte sequences in UTF-8"错误
该问题出现得十分诡异，在我使用百度和Google搜索均得不到想要的答案。准确来说，网上出现这种错误的情况比较少。在进行多番排查后，怀疑是自己系统的用户名含有非英文字符所致。于是，果断就重装系统了。重装系统后使用了全英文作为用户名，再次尝试安装，一切顺利，问题解决。这就告诉我们：
>no zuo no die

###2、执行rake deploy命令时出现无法git的错误
	! [rejected]        master -> master (non-fast-forward)
	error: failed to push some refs to 'https://github.com/eclipseflower/eclipseflower.github.com.git'
	hint: Updates were rejected because the tip of your current branch is behind
	hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
	hint: before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.
这个问题出现时我也比较紧张。好在Google一下解决方案到处都是。（不得不吐槽百度的英文搜索能力）有以下两种解决方式，亲测都可用：

1、手动进入_deploy目录手动强制push一次。参见[利用octopress部署博客到github](http://www.itzhoulin.com/deploy-a-blog-using-octopress-hosted-in-github/#deploy2github)。

2、（建议）在_deploy目录下执行以下命令。参见[Failed to deploy to Github Pages using octopress](http://stackoverflow.com/questions/21356212/failed-to-deploy-to-github-pages-using-octopress)。

	git config branch.master.remote origin
	git config branch.master.merge refs/heads/master
	git pull
###3、备份source时出现无法git的错误
报错提示与上一错误类似。我自己找到一个比较残暴的解决方案：即先删除远程分支，然后再重新提交本地分支。参考[git 常用命令(含删除文件)](http://www.cnblogs.com/springbarley/archive/2012/11/03/2752984.html)。命令如下：

	git push origin :heads/source
然后就可以像以前一样正常提交了。

