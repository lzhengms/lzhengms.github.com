---
layout: post
category : question
title: 几个值得思考的题目
tags : [intro,beginner,jekyll,githubblog]
---
{% include JB/setup %}

这几个题目是教授出的，个人觉得很有意思。思考思考这些东西不错。可惜教授要离职了，不然每周一试不错

1.第一个


    function closure() {
        var v1 = 'v1';
        this.v2 = 'v2';
        var add1 = function() {
            v1 += '-add1';
            v2 += '-add1';
            console.log(v1);
            console.log(v2);
        }
        this.add2 = function() {
            v1 += '-add2';
            v2 += '-add2';
            console.log(v1);
            console.log(v2);
        }
        add1();
        add2();
    
    };
    
    closure ();
    console.log('---');
    new closure();

2.第二个：


    （1）
	var P = function(a, b) {
        this.a = a;
        this.b = b;
    };
    P.prototype.get = function(name) {
        alert(this[name]);
    };

    var S = function(a, b, c) {
        P.apply(this, arguments);
        this.c = c;
    };
    var F = function() {};
    F.prototype = P.prototype;
    S.prototype = new F();
    S.prototype.constructor = S;

    var s = new S(1, 2, 3);
    s.get('b'); // 2
--------------------------------------------------------	
	（2）
	var S = function(a, b, c) {
        var F = function() {};
        F.prototype = P.prototype;
        P.apply(this, arguments);
        this.c = c;
        S.prototype = new F();
        S.prototype.constructor = S;
    };
    var s1 = new S(1, 2, 3);
    s1.get('b'); // 报错---------考虑下为什么这样就会报错了

    var s1 = new S(1, 2, 3);
    s1.get('b'); // 2
	
3.第三个

    var arr = [];
    var fn = function(n) {
    if(n < 0) {
        return;
    }
    fn(n-=2);
    fn(n+=1);
    arr.push(n);
    };
    fn(3);
    console.log(arr);



	

    
