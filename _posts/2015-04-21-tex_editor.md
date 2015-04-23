---
layout: post
title:  "Texstudio使用经验"
date:   2015-04-21 22:58:47  
categories: tools
tags: TeXmaker TeXstudio
---
本贴介绍我在写毕业论文的过程中使用TeXstudio的一些经验。

在一开始的时候我用的是[Texmaker]，由于包含中文以及多个文件的tex和pdf的跳转有问题，在写毕业论文的过程中我最终转向了[TeXstudio]。经过一段时间的体验，我觉得TeXstudio还是很棒的。TeXstudio是曾经从Texmaker独立出来之后发展起来的一个tex编辑器，很多界面命令都一样，从Texmaker到TeXstudio的迁移是容易的。整体上来说，Texmaker的设计更倾向于对用户友好，不易出错，有点像Apple公司的风格（不过windows下的UI真心一般），TeXstudio适合码农来用（普通使用也是棒棒哒），有各种高级设置，可编程的宏命令功能非常强大。下面对比下两款软件。

## TeXmaker和TeXstudio对比 ##

我先陈述下Texmaker相比于TeXstudio的优点：

1. 可以自动检测tex文件的编码，提示是否按照对应编码方式打开。这对一些初级用户使用非utf-8格式的编码提供了方便。
2. 在structure面板中无限自定义命令超赞，可以用`:XX+向右键`转换，有种用vim的感觉（这个功能也可以部分地由TeXstudio的宏实现）。

然后列表Texstudio的优点，其中Texmaker也有的功能做了标注。

1. 整体界面UI面积减小，把更多的空间留给编辑和pdf窗口，更容易focus。高级用户可以在高级选项更细致地调节，貌似这也是最初TexStuio跟TextMaker设计哲学不合的体现吧。刚安装TeXstudio的时候其实差点因为其太丑而卸掉，主要是默认字体在中文系统下太难看加上tex代码里一片错误命令的高亮提示。在使用经验中我会给出我目前使用的配置文件以及增加自定义命令的方式。
2. 更强大的structure预览，定义完主文档后会一直在。
3. 支持定义各种meta信息，包括编码信息（此功能Texmaker 4.4.1版本也有）、主文档信息等。
    ```
    % !TeX root = main.tex
    % !TEX encoding=GB18030
    ```
4. 支持自动恢复上次的会话。也就是能把上次打开的文档全部自动打开，对于编辑多文件的毕业论文非常实用。Texmaker可以保存会话也可以加载会话，不过笔者使用时最新的版本4.4.1没有自动恢复上次会话的功能。
5. 文档内高亮设置，错误命令高亮等如果设置好了非常易于写作。可以通过"选项-设置-补全"选项卡内的扩展命令集来去除一些不应该的错误高亮。[ThuThesis]相关的命令集选项中也有，但不是很全，后面会介绍怎么自己添加。
6. 公式行内预览对于大文档内局部公式编辑有很大帮助，实时预览和强大的纠错功能是亮点。
7. TeXstuio的快捷编译可以自动地检测bib文件的变化并自动编译多遍直至交叉引用成功，这一点也很实用。

## TeXstudio使用经验 ##

接下来我主要陈述下使用TeXstudio的一些经验，分为初级和高级两部分。其实如果你需要长时间使用一个软件，一个最好的学习方式就是把选项一个个看过去，把帮助文档也大致看一看。然而每个人使用软件的习惯终究不一样。突然想起我在《吉祥纹莲花楼》这部小说中看到的几句话。
![center]({{ site.url }}/downloads/images/belief.jpg)

### 初级使用 ###

在对比Texmaker和TeXstudio的过程中我们其实已经给出了一些，这里再重新整理下。

1. 在子文档中编译整个文档。毕业论文的模板包含多个文件，写作往往在子文件里，然而如果不加设置地直接编译子文件是会报错的。这时需要在“选项”中设置主文档或者在主文档第一行中加入meta信息`% !TeX root = main.tex`(假设主文档是main.tex的话)。这样在任何一个子文件都可以直接编译，等价于编译main.tex。
2. 常用快捷键。F1快捷编译（可以在选项里面改其用的编译命令，默认是pdflatex），F7查看tex对应的pdf，在pdf中按住ctrl单击可以跳转到对应的tex文件。Ctrl+E添加begin，end环境。Alt+P预览行内数学公式。Ctrl+Shift+M添加行内数学公式（因为经常使用，我添加了额外的快捷键Ctrl+`）。Alt+Shift+M添加显示数学公式。其他的默认快捷键参见帮助中的用户指南。快捷键的使用可以大大提高写作效率。
3. 标签的使用。在一个较长的文档中，经常需要前后滚动鼠标，有时回到正在书写的地方是费事的，因此可以点击这一行左侧界面的空白处，添加标签。按Ctrl+n (n为标签的编号，一个文档至多有3个标签)或者点整个界面右下角，或者从结构面板的标签选项卡里点击可以跳转到该书签。其他的跳转命令可以参见菜单中的“编辑-跳转到”，其中Ctrl+H跳转到上一次修改处也是很实用的。不过貌似点击一次总是会回到当前文档头部，需要再按一次才能到之前修改的地方。
4. 在pdf面板中点击显示可以选择时钟（clock），可以双击单独显示也可以调整大小。虽然功能很简单，不过可以作为督促自己专心写论文的小工具哦。
其他功能和使用技巧请参见[帮助文件](http://texstudio.sourceforge.net/manual/current/usermanual_en.html]和[官网][http://texstudio.sourceforge.net/)。

### 高级使用 ###

通过导入我的[配置文件]({{ site.url }}/downloads/files/qing_2015_04_21.txsprofile)可以拥有文中提及的一些功能。通过“选项-加载配置文件”来加载。

#### 自定义补全 ####

一些TeXstudio无法识别的命令会高亮显示出来，大面积的高亮非常丑。TeXstudio自己收集了一些常见package的命令，可以在"选项-设置-补全"选项卡内选择对应的扩展命令集来去除一些不应该的错误高亮。然而有些package或者自定义的命令很可能识别不全，这时需要手动添加。TeXstudio中自动补全的命令是有cwl文件来记录的。cwl文件路径为C:\Users\%UserName%\AppData\Roaming\texstudio，找出一个cwl文件添加自己需要的命令即可，我是在thuthesis.cwl和thutils.cwl里修改的。添加的格式可以参考[帮助文件](http://texstudio.sourceforge.net/manual/current/usermanual_en.html#CWLDESCRIPTION)。

#### 自定义宏 ####
有时会有一些特殊的需求而软件没有给出这个功能时，可以用宏来实现。TeXstudio的宏大致原理是用触发器（trigger）或者类似于latex命令（没用过这个功能）来触发宏，然后通过三种方式来跟编辑器等来交互实现用户自定义的功能。这三种方式分别为“正常”、“环境”和“脚本”，具体的文档参见[帮助文件](http://texstudio.sourceforge.net/manual/current/usermanual_en.html#SECTION33)。帮助文件中给了大量的例子，比如计算器。下面给出几个我使用过的例子。

+ 文本替换也就是正常替换。Texmaker 4.4.1可以自定义命令`:XX+向右键`，用自定义类似于vim的命令来实现简单命令到复杂文本（可以是命令）的替换。在TeXstudio中可以用宏来代替。之所以在对比中说是部分地实现该功能，是因为我目前还没有找到键盘映射如何触发宏。TeXstudio使用正则表达式来匹配trigger，虽然无法匹配某些按键，但是也更灵活。我自己的使用中用Tab键(\t)来作为一般的触发键。比如如果经常使用itemize，而且希望出来三个item的话，可以使用以下的宏。触发器为`:i\t`，宏内容是自己想替换的文本
{% highlight tex %}
\begin{itemize}
    \item %|
    \item %<%>
    \item %<%>
\end{itemize}
{% endhighlight %}
`%|`指鼠标的跳转，`%<%>`是占位符，跳转到下一个占位符的快捷键是Ctrl+向右键。

+ 环境模式适用于添加begin,end这样的环境。可以用%environment来触发

+ 脚本模式可以用来实现更复杂的命令，下面给出两个例子。这两个例子都是通过正则表达式获得匹配内容，然后在前后加上一些文本。

**例子一，给变量加行内数学模式。**如果经常要使用行内数学模式来标记一些变量，那么每次即使按快捷键添加`$ $`，然后再输入比如变量`p`也比较麻烦。可以实现一个宏，当输完`p`之后按下Tab键就可以自动地在`p`前后加上`$ $`。触发器为`([A-Za-z0-9, _=\^\(\)'\\]+)\t`，宏内容为
{% highlight javascript %}
%SCRIPT
var math =  triggerMatches[1]
editor.write("$ " + math + " $"); 
{% endhighlight %}
**例子二，引用时自动加上前后缀。**引用不同的类型，比如章、节、图、表、公式等需要前后加不同的描述，可以实现一个脚本自动根据标签的前几个字符来判断。假设用户给章的label都是`\label{cha:XXX}`，给节的都是`\label{sec:XXX}`之类的可以使用下面的宏。触发器为`\\ref\{([a-z]{2,10}):\w+\}\t`，宏为
{% highlight javascript %}
%SCRIPT
var type = triggerMatches[1];
var cmd = triggerMatches[0].trim();
if (type == "equ")
editor.write("式(" + cmd + ")")
else if (type == "fig")
editor.write("图" + cmd);
else if (type == "cha") {
editor.write("第" + cmd + "章");
} else if (type == "sec") {
editor.write(cmd + "节");
} else if (type == "thm") {
editor.write("定理" + cmd);
} else if (type == "def") {
editor.write("定义" + cmd);
} else if (type == "alg") {
editor.write("算法" +cmd);
} else {
editor.write(cmd);
}
{% endhighlight %}










[Texmaker]: http://www.xm1math.net/texmaker/
[TeXstudio]: http://texstudio.sourceforge.net/