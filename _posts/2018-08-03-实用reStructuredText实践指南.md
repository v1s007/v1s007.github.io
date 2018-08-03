---
layout:     post
title:      实用reStructuredText实践指南
subtitle:   手把手教你用reStructuredText轻量标记语言写文章
date:       2018-08-03
author:     LZP[原创]
header-img: img/bg-it5.jpg
catalog: true
tags:
    - reStructuredText
    - 标记语言
---


> **这篇《实用reStructuredText实践指南》，完全使用Markdown语言写成！**
> **其中，有一些不是标准Markdown语法，属于扩展实现。**
> **另外，Markdown不支持表格，可以嵌入html代码实现复杂表格，扩展的Markdown，根据扩展的不一样，可以实现的表格式样也不一样。**

*****

## 目录
>目录可以用.. toctree:: 直接生成；（需要使用标题格式，以便于索引）

*****

## 标题

    一级标题
    ========

    二级标题
    ---------

    三级标题
    ~~~~~~~~~~

    四级标题
    ^^^^^^^^^^^

    五级标题
    ++++++++++

    六级标题
    '''''''''''

*****

## 段落

#### 空行分段

        第一段内容。

        第二段和第一段间有一空行。


第一段内容。

第二段和第一段间有一空行。

*****

#### 自动续行

        一个回车不分段，
        本行续上行。


一个回车不分段，
本行续上行。

*****

#### 不留白续行

> 行尾转义字符让\续行之间不留白。

*****

#### 插入换行


方法一:

        | 保持换行符，
        | 本行不续行。

保持换行符，
本行不续行。

方法二::

    .. role:: raw-html(raw)
    :format: html

    用新定义的role插入换行，
    :raw-html:`<br />`
    本行不再续行。

用新定义的role插入换行，
本行不再续行。

*****

#### 段落缩进

方法一:

        邮件体段落缩进：

        > 第一级段落缩进。
        >
        > > 第二级段落缩进。
        >
        > 返回一级段落缩进。


邮件体段落缩进：

>第一级段落缩进。
>
>>第二级段落缩进。
>
>返回一级段落缩进。

（备注说明：显示有问题！）

方法二:

    Python式段落缩进：

        第一级段落缩进。

            第二级段落缩进。

        返回一级段落缩进。

Python式段落缩进：

  第一级段落缩进。

    第二级段落缩进。

  返回一级段落缩进。


*****

## 代码块

#### 代码块(基础)

双冒号后缩进为代码块。

    ::

        def foo():
            print "Love Python, Love FreeDome"
            print "E文标点,.0123456789,中文标点,. "

双冒号后缩进为代码块。

    def foo():
        print "Love Python, Love FreeDome"
        print "E文标点,.0123456789,中文标点,. "

*****

#### 代码块(增强)

还可声明语言类型实现语法加亮。

    .. code-block:: ruby

        require 'redcarpet'
        md = Redcarpet.new("Hello, world.")
        puts md.to_html
    

```ruby
require 'redcarpet'
md = Redcarpet.new("Hello, world.")
puts md.to_html
```

*****

## 列表
#### 无序列表

    * 星号、减号、加号开始列表。

      - 列表层级和缩进有关。

        + 和具体符号无关。

    * 返回一级列表。

* 星号、减号、加号开始列表。

  - 列表层级和缩进有关。

    + 和具体符号无关。

* 返回一级列表。

*****

#### 有序列表

    1. 数字和点是一种编号方式。

        A. 大写字母编号。

            a. 小写字母编号。

    2. 继续一级列表。

        (I) 大写罗马编号。

            i) 小写罗马编号。

1. 数字和点是一种编号方式。

    A. 大写字母编号。

        a. 小写字母编号。

2. 继续一级列表。

    I. 大写罗马编号。

        i. 小写罗马编号。

*****

#### 列表续行、段落和代码块

    1. 列表项可以折行，
       对齐则自动续行。

    2. 列表项可包含多个段落。

        空行开始的新段落，
        新段落要和列表项内容对齐。

    3. 列表下的代码段注意对齐即可。

        ::

            $ printf "Hello, world.\n"

1. 列表项可以折行，
    对齐则自动续行。

2. 列表项可包含多个段落。

    空行开始的新段落，
    新段落要和列表项内容对齐。

3. 列表下的代码段注意对齐即可。

        $ printf "Hello, world.\n"

*****

#### 定义

    git
        Simple and beautiful.

    hg
        Another DVCS.

    subversion
        VCS with many constrains.

        Why not Git?


*****

## 分隔线

    四条短线或以上显示为分隔线。

    ----

*****

## 字体

#### 粗体和斜体
    这是 **粗体** ，这是 *斜体* 。
    不留白的\ **粗体**\ 和\ *斜体*\ 效果。

这是**粗体**，这是*斜体*。
不留白的**粗体**和*斜体*效果。

*****

#### 删除线

    .. role:: strike
        :class: strike

    :strike:`删除线` 效果
    不留白的\ :strike:`删除线`\ 效果

~~删除线~~效果
不留白的~~删除线~~效果

*****

#### 下划线

    .. role:: ul
        :class: underline

    :ul:`下划线` 效果
    不留白的\ :ul:`下划线`\ 效果

<u>下划线</u>效果
不留白的<u>下划线</u>效果

*****

#### 上标、下标

    Water: H\ :sub:`2`\ O
    E = mc\ :sup:`2`

Water: H<sub>2</sub>O
E = mc<sup>2</sup>

*****

#### 等宽字体

    两个连续反引号嵌入代码，如: ``git status`` 。

两个连续反引号嵌入代码，如: `git status`。

*****

#### 引言
    
    反引号嵌入代码，如: `Got GitHub` by Jiang Xin.

>**备注说明：markdown无引言**

*****

#### 清除标记空白(无)

    标记符号前后空白\
    用\ **反斜线**\ 消除

标记符号前后空白用*反斜线*消除

*****

## 链接

#### URL自动链接

    网址 http://github.com/
    邮件 me@foo.bar

网址 http://github.com/
邮件 me@foo.bar

*****

#### 文字链接

    - 访问 `Google <http://google.com/>`_ 。
    - 上面已定义，直接引用 google_ 链接。
    - 链接地址在后面定义，如： GitHub_ 。
    - 反引号括起多个单词的链接。如 `my blog`_ 。

    .. _GitHub: http://github.com
    .. _my blog: http://www.worldhello.net

- 访问 [Google](http://google.com/)。
- 上面已定义，直接引用[google](#Google) 链接。
- 链接地址在后面定义，如： [GitHub][1] 。
- 反引号括起多个单词的链接。如 [my blog][] 。

 [1]: http://github.com
 [my blog]: http://www.worldhello.ne

*****

#### 内部跳转

    .. _fig1:

    .. figure:: https://longzeping.github.io/img/apple-touch-icon.png

        内部跳转图例

    上面定义的位置，可以：

    - 通过 fig1_ 跳转。
    - 或者 `点击这里 <#fig1>`__ 跳转。
    - 或者参见 :ref:`fig1`\ 。

<a name="fig1" id="fig1"></a>
![](https://longzeping.github.io/img/apple-touch-icon.png)
    内部跳转图例

上面定义的位置，可以：

- 通过 [fig1](#fig1) 跳转。
- 或者 [点击这里](#fig1) 跳转。
- 或者参见 [内部跳转图例](#fig1) 。
  
*****

#### 脚注(扩展实现)

    reST脚注的多种表示法：

    - 脚注即可以手动分配数字 [1]_ ，也可以使用井号自动分配 [#]_ 。

    - 自动分配脚注 [#label]_ 也可以用，添加标签形式 [#label]_ 多次引用。

    - 还支持用星号嵌入符号式脚注，如这个 [*]_ 和 这个 [*]_ 。

    - 使用单词做标识亦可 [CIT2012]_ 。

    .. [1] 数字编号脚注。
    .. [#] 井号自动编号。
    .. [#label] 井号添加标签以便多次引用。
    .. [*] 星号自动用符号做脚注标记。
    .. [*] 星号自动用符号做脚注标记。
    .. [CIT2012] 单词或其他规定格式。

reST脚注的多种表示法：

[^1]: 数字编号脚注。
[^#]: 井号自动编号。
[^#label]: 井号添加标签以便多次引用。
[^*]: 星号自动用符号做脚注标记。
[^†]: 星号自动用符号做脚注标记。
[^CIT2012]: [CIT2012] 单词或其他规定格式。

- 脚注即可以手动分配数字[^1] ，也可以使用井号自动分配 [^#] 。

- 自动分配脚注 [^#label]， 也可以用添加标签形式 [^#label] 多次引用。

- 还支持用星号嵌入符号式脚注，如这个 [^*] 和 这个 [^*] 。

- 使用单词做标识亦可 [^CIT2012] 。

（*备注：markdown不支持符号式脚注和单词式脚注，并且脚注数字符号的式样与RST也有差别。*）

*****

## 图片

    .. figure:: https://longzeping.github.io/img/apple-touch-icon.png
        :width: 32

        图：GitHub logo

    GitHub Logo: |logo|
    
    带链接的图片：
      |imglink|_
    
    下图向右浮动：
       .. image:: https://longzeping.github.io/img/apple-touch-icon.png
          :align: right

    .. |logo| image:: https://longzeping.github.io/img/apple-touch-icon.png
    .. |imglink| image:: https://longzeping.github.io/img/apple-touch-icon.png
    .. _imglink: https://github.com/

![](https://longzeping.github.io/img/apple-touch-icon.png)
    图：GitHub logo

GitHub Logo:![logo]

带链接的图片：
[![][logo]](https://github.com/)
    
下图向右浮动：
  ![](https://longzeping.github.io/img/apple-touch-icon.png)

[logo]: https://longzeping.github.io/img/apple-touch-icon.png "Logo"
    
*****

## 表格

    .. table:: 示例表格
        :class: classic

        +---------+--------+--------+
        | head1   | head2  | head3  |
        +=========+========+========+
        |         | cell   | cell   |
        | rowspan +--------+--------+
        |         | * colspan       |
        |         | * another line  |
        +---------+-----------------+

Markdown本身无法实现RST给出的这种带行列合并的复杂表格，但可以借助html代码实现。下面的表格不是Markdown标准语法实现，借助html语法实现。

<table>
<tr><td>head1</td><td>head2</td><td>head3</td></tr>
<tr><td rowspan=3>rowspan</td><td>cell</td><td>cell</td></tr>
<tr><td colspan=2 rowspan=2>*colspan <br> *another lien</td></tr>
<tr></tr>
</table>

下面是gfm扩展实现的Markdown简单表格：
|head1|head2 |head3|
|:---:|:---: |---: |
|rowspan|cell|cell |
|rowspan|cell|cell |
|rowspan|cell|cell |

*****

## 其它

#### 转义

        反斜线作为转义字符，\禁止对后面 \*字符* 做语法解析。

反斜线作为转义字符，\禁止对后面 \*字符* 做语法解析。

*****

#### 注释

    .. 注释

    ..   

       缩进内容也是注释

[//]:注释

[//]:
  缩进内容也是注释

*备注说明：标准markdown中没有注释，属于扩展实现。*


*****

#### 其它说明

* reStructedText的功能要多于Markdown，特别是表格、标注、脚注、链接、图片。

* 同时，reStructedText也比Markdown复杂，写无复杂格式的文章，Markdown比reStructureText更方便。
 
*****