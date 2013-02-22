vim-use
===================
**note:** 这个是我平时使用vim的一份记录 我的邮箱 xiyoulaoyuanjia@gmail.com

*   [命令模式](#commad)
    * [在当前/后面插入一行](#command_1)
    * [光标跳转到第n行](#command_2)
    * [更改 删除 复制 选中 代码块](#command_3)
    * [跳转到与它匹配的括号处](#command_4)
    * [整体向右移动](#command_5)
    * [多行执行相同的操作例如注释](#command_6)
*   [插入模式](#insert)
     * [vim 的自动补全机制](#insert_1)
     * [](#insert_2)
     * [](#insert_3)
*   [末行模式](#lastCommand)
    * [显示行号](#lastCommand_1)
    * [去掉行号](#lastCommand_2)
    * [非root用户保存编辑](#lastCommand_3)
    * [外command命令与文档的交互](#lastCommand_4)
    * [删除所有行](#lastCommand_5)
    * [删除空格](#lastCommand_6)
    * [增加tags文件](#lastCommand_7)
    * [与tags文件有关的快捷键](#lastCommand_8)
    * [取消 vim 回车注释的问题](#lastCommand_9)
    * [整体向右移动](#lastCommand_10)


***
<h3 id="insert">插入模式</h3>
<h4 id="insert_1">vim 的自动补全机制</h4>
    在插入模式下 键入一个字符  然后 单击 CTRL-N 编辑器将用同文件中出现的第一个以相同字母开头的标识符自动完成它。再次按下CTRL-N 将给出第二个符号要求的标识符！



***
<h3 id="commad">命令模式</h3>
<h4 id="command_1">在当前/后面插入一行并且切换成插入模式</h4>
######注意完成后变成插入模式######
    O/o
<h4 id="command_2">光标跳转到第n行</h4>
>**note:** 转到第9行  
    
    9G
    
<h4 id="command_3">更改 删除 复制 选中 代码块</h4>
>**note:** 这里的代码块主要包括 {} () [] 
    
    ci( di(  yi( vi(

<h4 id="command_4">跳转到与它匹配的括号处</h4>
>**note:** 当前光标在([{ 中
    
    %

<h4 id="command_5">整体向右移动</h4>
>**note:** 另外table 默认是4个空格  当然可以修改了 方法为 set shiftwidth=3

     7gg4<< 
     
<h4 id="command_6">多行执行相同的操作</h4>
>**note:** 当然方法很多。这里采取列行模式

     1.ctrl+v  2.选择包括的行数 3.I(大写i) 4.插入执行动作例如 "//" 注释符号 5. ESC 键


***


<h3 id="lastCommand">末行模式</h3>
#####显示行号#####
    :set number 
#####去除行号#####
    :set nonumber
    
<h4 id="lastCommand_3">非root用户保存编辑 </h4>
当我们使用非root用户打开一个文档，并且编辑需要保存时需要
    
    :w !sudo tee %   
<h4 id="lastCommand_4">外command命令与文档的交互 </h4>
将command的输出插入到当前位置。
    
    :r!command
 
将command命令作用于全文 例如我们可以不用退出直接运行perl程序！
    
    :!perl %
    
<h4 id="lastCommand_5">删除所有行</h4>
>**note:** 先用G转到文件尾

    1,. d
<h4 id="lastCommand_6">删除空格</h4>
>**note:** 完成的目的是使多行变成一行显示(命令解释为将回车替换成空格)

    %s/\n/ /g

<h4 id="lastCommand_7">增加tags文件</h4>
>**note:** 这里值已经打开了vim 后希望自己tags文件 当然可以设置vim的tags文件的路径，这里给出了一个使用绝对路径导入的方法
    
    :set tags=/root/ossec-hids-2.6/src/tags

<h4 id="lastCommand_8">与tags文件有关的快捷键</h4>
>**note:** 当使用 ctrl+] 命令找到的不是需要的时候可以使用此命令。下面是一个查找NULL_Decoder的例子

    :ts NULL_Decoder
>**note:** 可以使用 ctrl+] 快速的查找当前光标的定义处
    
    ctrl+] 

>**note:** 可以使用 ctrl+T 返回 可以看做是 ctrl+] 的反动作
    
    ctrl+T

<h4 id="lastCommand_9">取消 vim 回车注释的问题</h4>
>**note:**在centos6 中 默认注释语句后面换行是会在前面加注释语句的，如何我们需要从外面粘贴语句进来，这一特性就十分讨厌。取消其方法如下
    
    set fo-=r
>**note:** 
help formatoptions  可得其解释 
更多选项 help fo-table
例如 此处r

>r     Automatically insert the current comment leader after hitting
        <Enter> in Insert mode.

<h4 id="lastCommand_10">整体向右移动 </h4>

    7,10<



