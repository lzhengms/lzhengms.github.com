---
layout: post
category : github_blog
title : 浮动，定位，行高，块级内联的理解
tags : [intro,beginner,jekyll,githubblog]
---
{% include JB/setup %}

做过一些css，js的事情，但是没有深入研究。特别是浮动，定位，display，line-height这几个一直没有理解清楚。这段时间有认真的去看了一下。下面是
个人的一些理解。不对的地方请多指教


### 要讲的几个知识点：

- **浮动float**   
	这块主要是清除浮动的几种方法  
- **定位position**  
        定位方法，relative，absolute，fixed，默认是static
- **display**    
        inline，block，inline-block几个属性以及在ie6下的表现，visibility和display的区别。
- **line-height**    
        行高居中和居中的方法
- **ie6下的haslayout**        
         ie6下的layout的触发 
              
### 几个知识点的主要地方: 

- **浮动float**   
	 浮动主要就是清除浮动的工作，因为浮动元素会被移出文档流，会导致外围div高度隐藏，会影响布局。
	 所以，一般在浮动之后就要立马执行清除浮动操作。布局的时候，如果有右浮动，通常先写右浮动，再写左浮动。
	 下面列出几种清除浮动的方法 
	 
	 (1)&lt;div style="clear:both"&gt;&lt;/div&gt;   
	    这种方法浏览器兼容性好，但是就是要添加额外的标签   
	 (2)&lt;br  style="clear：both"/&gt;  
	 (3)ie6下:   
	          
	          #outer{display:inline-block}  
	          *html #outer{height:1%}  
	          #outer {display:block}   
	 (4){overflown:hidden或者auto}  
	   在ie6下还需要价格zoom:1来触发layout，才会生效 。跟定位一起用会出问题 
	 (5)万能清楚浮动.clrfix:  
	             在父级元素上加上类名clrfix，在ie6下也是要加上zoom:1来触发layout的  
	             
	             .clrfix
	          {
	          content:".";
	          height:0;
	          visibility:hidden;
	          display:block;
	          clear:both;
	          }
- **定位position**   
        position默认的是static，fixed在ie6下是不支持的。absolute和fixed是脱离文档流的，relative还是有占据文档空间的。当使用absolute
        定位的时候，它会去找父级有用到position这属性的元素作为标准，进行偏移。如果没找到就相对于浏览器窗口。而relative是相对于本身元素
        所在的原来位置进行偏移的。设置了这个属性之后，z-index才会生效，一般position是配合着z-index使用的。z-index越大，在越上面一层  
- **display**  
         display常用的有inline,block,inline-block。inline可以将块级元素变成内联元素，block可以将内联元素变成块级元素。inline-block
         可以让一个元素有内联的性质同时有块的性质。display和visibility的区别是，`display`不占据文档位置，`visibility`有占据文档空间，
         ie6下的inline-block其实是没用的。但是可以触发ie6的layout，所以在ie6下要改变内联和块级元素，需要在两个css里面写才会生效。例如：

         div{display:inline-block}
         div{display:inline} 
- **line-height** 
         line-height和height的区别，其实这两个都是撑开一个高度的。一个元素如果没有设置高度，却有高度的原因就是因为存在line-height。
         ie6下，height是需要使用haslayout，height设置不是auto的任何值都是可以触发layout的。但是line-height不需要layout就有效的。  
            （1）我们常用的一个行高的地方就是单行文字居中的问题：    
                 设置line-height和height一样高就可以让内容居中了。  
            （2）附带讲一下居中的几种方法： 
                  `margin:0 atuo`用于对DIV框的居中定位，对IE不起作用。    
                  `text-align:center`用于DIV中的内容的定位，对IE起作用 
                  如下代码可以在所有浏览器中使DIV标签水平居中:  
                  
                  <body style="text-align:center">  
                  <div style="width:80px;margin:0 auto"></div>  
                  </body>   
	 (4)直接在body设置高度是没用的，因为高度是不继承的，要设置最小宽度，必须在里面再加一个div，设置里面这个div的宽度为960px  
- **ie6下的haslayout**  
          （1）ie6下触发layout的元素及元素的值：  
           
           position:absolute
           float:left/right
           display:inline-block
           width:any value other than auto
           height:any value other than auto
           zoom:1   
	 (2)ie7下触发layout的元素：  
	 
	   <pre><code>
	   overflow
	   overflow-x
	   overflow-y
	   min-width
	   max-width
	   min-height
	   max-height</code></pre>
	 
          
           
           
    
            
                         
                             
         

         
        

                     
         
         
          
        

       
	          
  
	         
	    
	   	 

      
      
    
