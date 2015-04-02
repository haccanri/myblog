---
layout: post
title:  "Markdown, Pandoc and Jekyll"
date:   2015-03-31 13:50:52
categories: learning
tags: markdown pandoc jekyll
---
# Markdown参考资料
1. GFM(GitHub Flavored Markdown)
    + <https://help.github.com/articles/github-flavored-markdown/>
    + <https://help.github.com/articles/markdown-basics/>
2. Standard markdown
    + <http://daringfireball.net/projects/markdown/syntax>
3. Tips
    + End a line with two spaces to add a `<br/>` linebreak:

# Pandoc参考资料
1. 可以从[这里](https://github.com/jgm/pandoc/releases/)安装Pandoc，直接下载msi文件安装就行
2. 虽然是2012年的博客，不过其中的东西都还好用，比如编译pdf的命令。<http://www.yangzhiping.com/tech/pandoc.html>
3. 这里面详细解释了pandoc编译中文pdf的各种坑。<http://blog.sina.com.cn/s/blog_5ee56d450101dah2.html>
  + 使用`fc-list > C:\fonts.txt`的方式输出系统中的字体名字非常好用，只是列表非常大，可能需要搜索一些关键字来查看，比如_黑_，_宋_之类的
  + 目前使用微软雅黑字体（Microsoft YaHei，大小写是敏感的）不会出现文字超过边界，而使用宋体（SimSun）和黑体（SimHei）会出现超出边界的问题，使用模板应该可以，没有亲自测试。相关命令如下
 
    {% highlight bash %}
pandoc test.md -o test.pdf --latex-engine=xelatex -V mainfont="Microsoft YaHei"
pandoc test.md -o test.docx --css=https://raw.githubusercontent.com/nicolashery/markdownpad-github/master/markdownpad-github.css (不加`--css`选项貌似效果一样)
{% endhighlight %}
4. pandoc的更多用法参见http://johnmacfarlane.net/pandoc/demos.html
    - 用--toc选项可以在html中生成目录。
    - 用beamer做slides也超赞
    - HTML slide shows也超赞
5. 用pandoc可以把带latex公式的markdown文件转化成docx的公式以及包含公式的pdf，这个超赞！


# Jekyll参考资料
1. 安装
  + <http://jekyllrb.com/docs/windows/#installation>
      + 如果遇到报错“Liquid Exception: Incompatible character encoding”，需要更改console的code page
      
          ```      
            chcp 65001
          ```
  + <http://jekyll-windows.juthilo.com/>。在安装jekyll gem包的时候会遇到ssl报错的情况，可以参见<https://gist.github.com/luislavena/f064211759ee0f806c88>

