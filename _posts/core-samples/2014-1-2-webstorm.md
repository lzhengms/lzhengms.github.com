---
layout: post
category : webstorm
title : webstorm的快捷键配置
---
{% include JB/setup %}

##配置tpl

(1)file----setttings----External Tools---增加一个tpl


####设置name：tpl
####设置Description:html编辑成js的tpl.js
####设置Options: 横排的两个打钩
####设置show  in：都打钩
####设置Tool settings:
 
          (1) Program:
                     C:\Users\Administrator\AppData\Roaming\npm\tpl.cmd
          (2) Parameters:
                     $FileDir$\$FileNameWithoutExtension$.html  $FileDir$\$FileNameWithoutExtension$.js
          (3) Woking directory:
                     $FileDir$


##.配置npm

(1)file----setttings----External Tools---增加一个npm


####设置name：npm
####设置Description:npm
####设置Options: 横排的两个打钩
####设置show  in：都打钩
####设置Tool settings:
 
          (1)Program:
                     D:\Program Files\nodejs\npm.cmd
          (2)Parameters:
                     $Prompt$
          (3)Woking directory:
                     $ProjectFileDir$

##.配置grunt

(1)file----setttings----External Tools---增加一个grunt


####设置name：grunt
####设置Description:grunt
####设置Options: 横排的两个打钩
####设置show  in：都打钩
####设置Tool settings:
 
           (1)Program:
                    C:\Users\Administrator\AppData\Roaming\npm\grunt.cmd
           (2)Parameters:
                     $Prompt$
           (3)Woking directory:
                     $ProjectFileDir$


##都配置完了之后，配置对应的快捷键

Keymap----------External Tools----------找到对应的名称设置，不同的快捷键