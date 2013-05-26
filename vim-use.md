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
    * [关于vim编辑器增加自定义结构体 补全功能](#command_7)
    * [关于VISUAL模式](#command_8)
   
*   [插入模式](#insert)
     * [vim 的自动补全机制](#insert_1)
     * [关于vim 的 可视模式](#insert_2)
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
    * [设置tab键的空格多少几个空格](#lastCommand_11)
    * [向前与向后查找搜索字符](#lastCommand_12)
    * [如果查看文件编码格式？](#lastCommand_13) 
    * [如果修改文件编码格式？](#lastCommand_14) 
    * [关于vim寄存器](#lastCommand_15)
    * [关于粘帖代码时vim的自动缩进的问题](#lastCommand_16)
    * [命令行搜索 ](#lastCommand_17)



***
<h3 id="insert">插入模式</h3>
<h4 id="insert_1">vim 的自动补全机制</h4>
    在插入模式下 键入一个字符  然后 单击 CTRL-N 编辑器将用同文件中出现的第一个以相同字母开头的标识符自动完成它。再次按下CTRL-N 将给出第二个符号要求的标识符！
<h4 id="insert_2">关于vim 的 可视模式</h4>

可以理解为有3中可视模式 

>* v    一个字符一个字符的选 从开始到结束的位置都会选中

>* V(Shift+v)    一行一行的选则.. 从开始的行到结束的行都会选中

>* Ctrl+v        一块一块的选中...... 可以用来删除一列或者多列...

按任意键(对于一些字符可以产生相应的效果..例如 d 可以删除选中的内从 ">" 可以在前面都加入 tab格)就可以退出可视模式




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


<h4 id="command_7">关于vim编辑器增加自定义结构体 补全功能</h4>

>* ～/.vimrc中增加如下两行：

filetype plugin indent on

set completeopt=longest,menu

      打开文件检测和智能补全，并关闭智能补全时的预览窗口。

>* 在vim中使用方法:
 
      光标放到 "->"或者"." 之后 "ctrl+x" 在点击 "ctrl+o" 会弹出一个下拉菜单来..
      

<h4 id="command_8">关于VISUAL模式</h4>


      一般而言 VISUAL有3中 分别为:
      >* VISUAL 模式(v) 
      
      这种模式会将光标的开始与结尾的所有字符选择上
        
      >* VISUAL BLOCK(ctrl+v) 
      
      这种模式是成块成块选择的 光标跳转为对角线方式跳转.
      
      常用的是同时更改(编辑,增加,删除 替换)相同的行
        
      例如  增加 注释 
          
      >>* ctrl+v 选中需要增加的地方..
      >>* shift+i 变成插入方式
      >>* 编辑内容(例如写 # 字符)
      >>* ESC 键  则同步其它行
      
      >*  (VISUAL LINE)shift+v
      
      这种模式是成行成行选择的.
      
      __当然在选中块之后可以进行一些常用的编辑选项.r 是替换的. d 是删除的, y是复制的__




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
    
<h4 id="lastCommand_11">设置tab键的空格多少 </h4>

    set ts=4 设置table(ts表示的含义tablestop)键 为4个空格     

<h4 id="lastCommand_12">查找的一些用法 </h4>

    n/N  查找(顺着之前的方向/反着之前的方向)下一个
    
    /或者?： 向下/向上 查找 ( 后面接字符串则查找字符串，否则查找刚查找的最后一个字符串)

<h4 id="lastCommand_13">如何查看文件编码格式? </h4>

    可以借鉴vim 工具。。1.用vim打开文件。2.set encoding
    
<h4 id="lastCommand_14">如何修改文件编码格式? </h4> 

     set encoding=utf-8  这样就把文件的编码更改为utf-8 了

<h4 id="lastCommand_15"> 关于vim的寄存器</h4> 

    :reg  显示VIM的寄存器  其中很重要的是 “+  表示系统剪贴板  使用 "+p  表示粘贴内容到VIM时 ，同理使用 "+y 把vim中的内容复制到系统的剪贴板
     note: 并不是所有的默认都支持“+ 系统剪贴板 例如 12.10 64 位 ubuntu
     
     You first need to see if vim is compiled with clipboard support, run vim --version | grep clip and see if there is a + or - in front of clipboard and xterm-clipboard.
     If it has clipboard support, copying from and pasting into the * or + registers should use the system/X11 clipboards, so "*yy would copy a line and "*p would paste it.
     In Ubuntu 10.10 you can install vim-gnome to have clipboard support compiled in.

<h4 id="lastCommand_16"> 关于粘帖代码时vim的自动缩进的问题</h4> 

      set paste 命令即可
      
<h4 id="lastCommand_17"> 搜索底行命令 </h4>

      底行下搜索 可以使用"ctrl+f" 搜索命令

      ![](http://xiyoulaoyuanjia-sendtosaepic.stor.sinaapp.com/Screenshot%20from%202013-05-26%2020:47:15.png)







