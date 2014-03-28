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
	
##6.ie6/7下设置select的的高度和边框

<pre><code>
.select-box{
    *padding: 10px 10px 10px 0px;
    *width: 180px;
    *border: 1px solid #ccc;
    *background: #fff;
    display: inline-block;
    *display: inline;
    zoom:1;
}
.select-wrap{
 *width: 190px;
    *height: 19px;
    *line-height: 16px;
    *overflow: hidden;
    display: inline-block;
    *display: inline;
    overflow:hidden;
    position: relative;
    zoom:1;
}
.select-wrap select{
    *margin: -1px;
    *width: 192px;
    *height: 21px;
    *font-size:12px;
    *overflow: hidden;
    *display: block;
    zoom:1;
    position: relative;
}

  <div class="select-box">
                        <div class="select-wrap">
                    <select class="rounder">
                    <option value="1">品牌营销</option>
                    <option value="2">产品测试</option>
                    <option value="3">消费者分析</option>
                    <option value="4">满意度调查</option>
                    <option value="5">人力资源</option>
                    <option value="6">学术教育</option>
                    <option value="7">社会民意</option>
                    <option value="8">其它</option>
                </select>
				        </div>
  </div>
</code></pre>
	
	
