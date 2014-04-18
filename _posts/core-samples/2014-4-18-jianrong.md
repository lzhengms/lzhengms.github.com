---
layout: post
category : css
title: 兼容多浏览器，关于表格的一些bug的处理
tags : [intro,beginner,jekyll,githubblog]
---
{% include JB/setup %}

这些是
关于强制不换行、强制换行的话题在网上已经被讨论了无数次，但我发现都不够全面，没有充分考虑各种浏览器、各种标签等情况，以致不兼容，所以我再来说说。由于 div 和 p 在本文的讨论中，效果相同，所以省略 p。

文中“没有指定宽度的 td”是指：为 table 指定了宽度，但没有给 td 指定宽度。

##强制不换行


div,
td
{
    white-space:nowrap;
}

这点在 Firefox 的 div 和 td 中，以及 IE 的 div 中，均没有问题。在 IE 的 td 中却很复杂：

如果没有为 td 指定宽度，则上述代码仍然有效。
如果为 td 指定了宽度，并且文字中无标点、无空格，上述代码不再有效。可以加 word-break:keep-all; 解决，这是 CSS3 的内容，不过是 IE 最先提出的，所以 IE6 中也支持。
如果为 td 指定了宽度，并且文字中有标点或空格。可以在文字与 td 之间套一层 div 加以解决。
综合起来，为了简单，使用：


div
{
    white-space:nowrap;
}
只是为了兼容 IE 的 td 的不同情况，在文字与 td 之间套一层 div。

##强制换行

强制换行是为了遇到一些超长的连续字符串（比如 aaaaaaaaaaaaa）时不撑大布局。


div,
td
{
    word-break:break-all;
}
word-wrap:break-word; 兼容性不够广，所以我们使用的是 word-break:break-all;。上述代码兼容于 IE、Chrome 的 div、指定宽度的 td、没有指定宽度的 td，非常不错，遗憾的是 Firefox 中不支持这个属性，所以无效果，为了不让其挤乱表格，可以加 overflow:hidden 来凑合着解决。

知其然知其所以然

上面介绍了三种属性：


white-space : normal | nowrap
word-wrap : normal | break-word
word-break : normal | break-all | keep-all
white-space


空白的处理方式，不止两个属性值，但在 IE6 中只支持这两个，所以不介绍其他的。


normal 多个连续英文空格压缩为一个英文空格显示，在空白处可换行。
nowrap 强制在同一行内显示所有文本，直到文本结束或者遭遇 br 对象。
word-wrap

内容超过容器边界时是否断开转行。


normal 允许（只是允许，不是必须）内容顶开指定的容器边界。
break-word 内容将在边界内换行。
word-break

换行的方式。


normal 英文在标点和空白处换行，中文在任何地方换行。
break-all 英文和中文都在任何地方换行，比如从一个英文单词的中间拆开换行。
keep-all 英文和中文都在标点和空白处换行。


##表格出现纵向滚动条时在IE6和IE7下截断最后一个td内容的解决方案

1.在ie6、ie7 下使用可解决当div内表格出现纵向滚动条时截断最后一个td内容的bug

<pre><code>
table-layout:fixed;*width:auto
</code></pre>

##border-collapse:collapse在firefox，IE6，IE7下的小bug

1.下面的方法可以解决ie6，ie7，firefox的表格边框被截断和边框左边像素多1px的bug

<pre><code>
table{border-top: none;border-right:none;border-bottom: 1px solid #FFFFFF;border-left: 1px solid #FFFFFF;}
table td,table th{border-top:1px solid #FFFFFF;border-right: 1px solid #FFFFFF;border-bottom:none;border-left: 0;}
</code></pre>














	

    
