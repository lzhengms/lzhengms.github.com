---
layout: post
category : learning
title : 知识分享
---
{% include JB/setup %}


###1.gazira修改的几个地方：

####（1）修复了拖动元素的父元素的position为fixed时候的bug

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

###2.项目中遇到的一些兼容性问题：

####（1）IE下在input内回车的问题

       在ie中，在input敲回车的时候，ie会自动寻找第一个button标签并且触发。也就是被第一个button标签劫持。

       [这样设置没有效果，回车仍然会触发button1]
       <p><button style="display:none;visibility:hidden">禁止input回车触发的button</button></p>

       [这样才有用，回车不会触发button1了]
       <div style="display:block; width:0; height:0; overflow:hidden;">
           <button>禁止input回车触发的button</button>
       </div>

       <p><button onclick="console.log('from button click1');">button1</button></p>
       <p><button onclick="console.log('from button click2');">button2</button></p>
       <p><input type="text" value="在这里回车就触发提交按钮" style="width:300px;" /></p>


        *尽量不要使用button标签，会引发很多意外情况。设计按钮可以使用a标签或者input[type=button]*

####（2）IE7，firefox下表格边框问题

        table{border-collapse:collapse;border:1px solid #000;}
        table td,table th{border:1px solide #000}

        IE下，表格的下边框会被截断
        firefox下的表格的左边框会多出一个像素

        最终解决方案：

        *在table上定义下边框和左边框；
        *在td上定义上边框和右边框；

        table{
        border-collapse:collapse;
        border:1px solid #000;
        border-top:none;
        border-right:none;
        }

        table td,table th{
        border:1px solid #000;
        border-bottom:none;
        border-left:none;
        }

####（3）margin-left,margin-right,width
          #####1.0个auto的情况是，marign-right会被强制为auto
          #####2.1个auto的情况是，计算之后得到值
          #####3.2个auto的情况是：

          **如果margin-left，margin-right设为auto的话，会被设置成左右相等，就会把该元素居中，这个居中是指元素本身，text-align只是应用于块级元素
          中的内容

          **如果是margin-left|margin-right,width设为auto的话，margin-left|margin-right都会被设置成0，width尽可能的宽

          #####4.3个auto的情况是，margin-left和margin-right都会被设置成0，width尽可能宽
          ####5.正常流中的一个块级元素的margin-top和margin-bottom为auto的话，都会被计算成0，所以高度设为auto是不会居中的

####（4）auto高度

          var s=$('<div style="height:auto;"><p style="margin:20px 0;background-color:red">ddddddd</p></div>');
          父div高度只有“dddd”文字的高度，父div有margin值，值就是p的margin值

          var s1=$('<div style="height:auto;border:1px solid #000；padding：1px"><p style="margin:20px 0;background-color:red">ddddddd</p></div>');
          加了边框或者内边距的话，父div的高度包含了“dddd”文字的高度和p的margin，父div没有margin值

###3.几个关键字的应用和区分:

####（1）typeof
**undefined,string,number,object,function,boolean**

         var arr=[1,2,3];

         (1)typeof arr======>'object';

         (2)toString=Object.prototype.toString;
            toString.call(arr)=====>'[object Array]'

####（2）instanceof
**判断某个对象是否是某个构造函数的实例**

*1. A instancof B,只要函数B在A的原型链中能找到，就返回true。*

  *2. 每个函数都默认有个prototype属性*

  *3. 通过new构造函数生成的对象都有一个属性__proto__属性，这个属性保存了创建它的构造函数的prototype属性的引用*

  *4. 构造函数都是函数的实例，函数，原型是对象*

         1.
         function Student(){

         }
         var s=new Student();
         s.__proto__=Student.prototype;
         Student.prototype.__proto__=Function.prototype;
         Function.prototype.__proto__=Object.protoytpe;
         Object.protoytype.__proto__=null;


         2.  Object instancof Function
           Object.__proto__=Function.prototype;
           Function.prototype.__proto__=Object.prototype;
           Object.prototype.__proto__=null;


         3. Function instanceof Object

            Function.__proto__=Object.prototype;
            Object.prototype__proto__=null;



####（3）constructor
**实例的constructor指向的是构造函数的prototye的constructor，构造函数的prototype的constructor默认指向构造函数本身**

         function Student(){

         }

         var s=new Student();
         (1) s.contructor==Student=====>true;

         (2) Student.prototype={};
             s.constructor==Student=====>false;
             s.constructor==Object=====>true;

         (3)Student.protoype={
                             constructor:Student;
                             };
             s.constructor==Student=====>true;

          *在做继承的时候，一定要保证【构造函数的prototype的constructor属性指向正确】*

####（4）hasOwnProperty
**检查属性是否是实例本身的，不是在原型上的**

         function Obj(name){
           this.name=name;
         }
         Obj.prototype.say='hello';
         var s=new Obj('张三');
         s.hasOwnProperty('name')=====>true;
         s.hasOwnProperty('say')======>false;











































