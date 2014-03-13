---
layout: post
category : seajs_debug
title : seajs_debug
tags : [seajs  debug  map]
---
{% include JB/setup %}

###线上调试seajs debug

##步骤

（1）在url上添加?seajs-debug
    

（2）把下面这写代码存在可访问的地址map.js


define(function(require, exports, module) {
    var loc = this.location;

    var local = 'http://ndweb.91.com/';
    var remote = 'http://v0ts.weibo.com/';

    seajs.on('fetch', function(data) {
        if (data.uri) {
            data.requestUri = data.uri.replace(remote, local);
        }
    });
});

 （3）在底下的框里面填入地址http://ndweb.91.com/static/map.js
 
 填入上面保存好的map.js的访问地址，点保存就可以了
   