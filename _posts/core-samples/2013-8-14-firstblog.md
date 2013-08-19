---
layout: post
category : github_blog
tags : [intro,beginner,jekyll,githubblog]
---
{% include JB/setup %}

这两天在研究github博客怎么弄，怎么在github上写博客，写的是大家通俗易懂的博客，而不是一大堆代码.
网上有很多这样的博客，我是通过参考网上的一些文章结合自己的实际从不会到会的一步步实现成功的，自己一个人
摸索期间，遇到很多问题，都解决了。下面给大家分享下我这两天研究成果和学习的一些心得，逐步建立github博客的步骤。
还有就是网上的一些其他文章里面存在一些问题。这里介绍的是window系统的


### 要用到的一些工具和知识：

- **github.com**   
	    首先在<https://github.com/>这个站点上注册个账号，对这个应该都不陌生吧。这个是前提
- **git**  
        git是本地和github上的库之间的传输工具。要先安装这个git工具，后期上传下载github.com上的库的内容都要用git命令
        下载地址:<https://help.github.com/articles/set-up-git>,可以在这个网址上去下载window上的git工具
- **jekyll**    
        jekyll是一种静态网站生成器，这是在github上建立博客的前提。有关jekyll的教程：官网-<http://jekyllrb.com/>；
        中文教程：<http://higrid.net/c-art-blog_jekyll.htm#baseurl>
- **DevKit**    
        DevKit是windows平台下编译和使用本地C/C++扩展包的工具。它就是用来模拟Linux平台下的make,gcc,sh来进行编译。
        但是这个方法目前仅支持通过RubyInstaller安装的Ruby.这个是jekyll本地搭建环境必需的。RubyInstaller的下载地址：
        <http://rubyforge.org/frs/?group_id=167>;DevKit的下载地址：<https://github.com/oneclick/rubyinstaller/downloads/>
- **markdown** 
        markdown可以理解为一种语法。博文可以去遵循这种语法，然后会有jekyll这样的环境去编译这种语法 ,markdown语法说明<http://wowubuntu.com/markdown/> 
                    
### 网上其他博客遇到的一些问题：

- **第一篇博客one**  
        <http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html>这是我研究怎样写github博客看的第一篇文章。也照做了，
        但是遇到了一些问题，在执行“$ git checkout --orphan gh-pages”这步的时候，遇到了“You are on a branch yet to be born”；
        后面我就现在github.com上先建立了这个库jekyll_demo，就顺利通过了。解决了这个问题，跟着步骤，分支gh-pages都生成了，所有的页面
        也上传上去了，但是访问的时候，就是报404错误。这篇博客最终还是没试验成               
- **第二篇博客two**  
        因为第一篇博客没成功，后来问了下同事，推荐了一个博客，确实不错，<http://www.mceiba.com/develop/jekyll-introduction.html>;
        这篇博客下面的3分钟搭建Jekyll Blog，在git bash上对着敲那些命令，就可以了。但是这个过程中我遇到了一个问题，就是在执行
        $ git push origin master这个命令的时候，会报permission denied就是没有权限的意思了。这个是ssh key的问题。可以参考官方的
        <https://help.github.com/articles/generating-ssh-keys>进行解决，解决好后，重新用git bash工具进入要提交的目录，敲下这些命令
        ，访问username.github.com就可以顺利看到我们熟悉的`Hello   World`了 

### github上写博客的步骤：

*  **在本地搭建jekyll环境**  
        可以参考下<http://www.cnblogs.com/purediy/archive/2013/03/07/2948892.html>              
*  **在_post文件夹里面写自己的文章**    
        怎么写文章可以参考下，<https://github.com/plusjade/jekyll-bootstrap.git>这个clone下来后的代码 ,参考[markdown标签](http://wowubuntu.com/markdown/)  
*  **本地测试jekyll**  
    在安装好的ruby控制台上面,进入到项目的目录下，执行这个命令jekyll serve。声明下：我看到网上这些命令$ jekyll --server，是不成功的，
    我是直接输入jekyll serve这个命令后就可以执行了。这个命令输完之后，在浏览器上输入http://localhost:4000，就可以访问了。_site目录
    是最终的静态网页.在访问的时候可能出现乱码问题，修改下_includes/themes/default.html的编码就可以了，改成gb2312。还有遇到一些中文标题，列表无效，一个标题里面要
	含有英文才可以正常有列表的样式。或者不用改编码，把文件保存成utf8无bom格式的，再直接改下convertible.rb这个文件的31行<pre><code>self.content=File.read(File.join(base,name),:encoding=>"utf-8")</code></pre>这是解决jekyll中文
	文章的问题，解决jekyll模板中文问题，在tags/include.rb的23行<pre><code>source=File.read(@file,:encode=>"utf-8")</code></pre>
*  **git提交**  
        最后使用git工具提交到github.com上       
        从github.com下载文件的git命令如下:   
		<pre><code>git clone https://github.com/zms91/---.git  git clone git@github.com:username/username.github.com.git</code></pre>
        从本地上传文件到github.com的git命令:
		
		
        git init
        git add .
        git commit -m 
        git push
    
