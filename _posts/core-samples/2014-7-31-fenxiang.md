---
layout: post
category : learning
title : 知识分享
---
{% include JB/setup %}

###1.gazira修改的几个地方:

####（1）修复了拖动元素的父元素的position为fixed时候的bug问题

        js/util/dom/dnd.js

        js/util/dom/sortable.js

        例子：demo/lib/util/dom/sortale

        增加了一个proxyParent属性
		
####（2）增加了几个常用的正则表达式

        js/lib/util/regexp.js
		
####（3）swfupload中增加了检测浏览器没有安装flash和其他错误的接口

        js/lib/util/dom/upload/upload-swfupload.js

        例子：demo/lib/util/dom/upload/swfupload.js

         new Upload().on('flashUnsupport',function(){
               //处理浏览器没有安装flash或者安装的flash版本不支持swfupload
         }).on('flashLoadFailed',function(){
               //其他程序错误
         });









































