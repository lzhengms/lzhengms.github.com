---
layout: post
category : div_css
title : css的一些常用小技巧
---
{% include JB/setup %}

##1.增加一个小箭头,tip

		<i class="arrow arrow-out"></i>
		<i class="arrow arrow-in"></i>

	.appmsg-edit .arrow {
    position: absolute;
	}

	.appmsg-edit .arrow-out {
     border-top: 12px dashed transparent;
    border-right: 12px solid #F8F8F8;
    border-bottom: 12px dashed transparent;
    border-left: 0 dashed transparent;
    display: inline-block;
    height: 0;
    left: 0;
    top: 44px;
    width: 0;
	}

	.appmsg-edit .arrow-in {
    border-top: 12px dashed transparent;
    border-right: 12px solid #F8F8F8;
    border-bottom: 12px dashed transparent;
    border-left: 0 dashed transparent;
    display: inline-block;
    height: 0;
    left: 1px;
    top: 44px;
    width: 0;
	}
##2.两个div对齐，左边的div没有数据，有背景色,需要跟右边对齐

	父div:
	overflow:hidden

	左边和右边的div:
	margin-bottom: -3888px;
	padding-bottom: 3888px;
	
##3.万能清除浮动
	.clearfix:after {
    content: ".";
    display: block;
    clear: both;
    visibility: hidden;
    line-height: 0;
    height: 0;
	}

	.clearfix {
    zoom: 1;
	}
##4.处理父元素里面的空白
		white-space: nowrap;
##5.设置透明
	rgba(0,0,0,0)//完全透明---------ie下不识别
	transparent----------------都可以识别
	opacity-----------------------标准浏览器识别，ie下不识别，opacity是0-1
	filter:Alpha(opacity=0)-------ie下可以识别，opacity是0-100，step是10
	opacity是0是看不到的，1是看得到的
	
	
