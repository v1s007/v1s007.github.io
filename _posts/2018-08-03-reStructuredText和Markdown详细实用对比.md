---
layout:     post
title:      reStructuredText和Markdown详细实用对比
subtitle:   手把手教你用轻量标记语言
date:       2018-08-03
author:     LZP[原创]
header-img: img/bg-it4.jpg
catalog: true
tags:
    - reStructuredText
    - Markdown
    - 标记语言
---

> 以下内容，reStructuredText简称RST，Markdown简称md

## 目录

> RST: 目录可以用.. toctree:: 直接生成；（需要使用标题格式，以便于索引）
> MD: 目录可以用[toc]，直接生成；（需要使用标题格式，以便于索引）

-----

## 标题

  RST:

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
  
  MD:

        # 一级标题
        ## 二级标题
        ### 三级标题
        #### 四级标题
        ##### 五级标题
        ###### 六级标题 ######

-----

## 段落

#### 空行分段

**RST和MD相同：**

        第一段内容。

        第二段和第一段间有一空行。


第一段内容。

第二段和第一段间有一空行。

------

#### 自动续行

**RST和MD相同（但MD的扩展gfm是回车换行）：**

        一个回车不分段，
        本行续上行。


一个回车不分段，
本行续上行。

------

#### 不留白续行

>RST：行尾转义字符让\续行之间不留白。
>MD：无。

#### 插入换行

RST:

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

MD:

    行尾两空格  保持换行。
    


#### 段落缩进

**RST和MD相同（其中第二种方法是MD扩展实现）：**

**写法一:**

    邮件体段落缩进：

    > 第一级段落缩进。
    >
    > > 第二级段落缩进。
    >
    > 返回一级段落缩进。

**显示效果：**

邮件体段落缩进：

>第一级段落缩进。
>
>>第二级段落缩进。
>
>返回一级段落缩进。


**写法二:**

    Python式段落缩进：

        第一级段落缩进。

            第二级段落缩进。

        返回一级段落缩进。

**显示效果：**

Python式段落缩进：

  第一级段落缩进。

    第二级段落缩进。

  返回一级段落缩进。


-----

## 代码块
#### 代码块(基础)

RST：双冒号后缩进为代码块。

    ::

        def foo():
            print "Love Python, Love FreeDome"
            print "E文标点,.0123456789,中文标点,. "

MD：四格缩进为代码块。

    def foo():
        print "Love Python, Love FreeDome"
        print "E文标点,.0123456789,中文标点,. "

显示效果：

    def foo():
        print "Love Python, Love FreeDome"
        print "E文标点,.0123456789,中文标点,. "

#### 代码块(增强)

还可声明语言类型实现语法加亮。

RST：以.. code-block:: 开头来标记，后面跟语言类型。

    .. code-block:: ruby

        require 'redcarpet'
        md = Redcarpet.new("Hello, world.")
        puts md.to_html
    

MD：以```符号标记，后面跟语言类型。

    ```ruby
    require 'redcarpet'
    md = Redcarpet.new("Hello, world.")
    puts md.to_html
    ```

显示效果：

```ruby
require 'redcarpet'
md = Redcarpet.new("Hello, world.")
puts md.to_html
```


## 列表

#### 无序列表

**RST和MD相同，写法如下：**

    * 星号、减号、加号开始列表。

      - 列表层级和缩进有关。

        + 和具体符号无关。

    * 返回一级列表。

**显示效果：**

* 星号、减号、加号开始列表。

  - 列表层级和缩进有关。

    + 和具体符号无关。

* 返回一级列表。

-----

#### 有序列表

**RST写法：**

    1. 数字和点是一种编号方式。

        A. 大写字母编号。

            a. 小写字母编号。

    2. 继续一级列表。

        (I) 大写罗马编号。

            i) 小写罗马编号。

**RST显示效果：**

1. 数字和点是一种编号方式。

    A. 大写字母编号。

        a. 小写字母编号。

2. 继续一级列表。

    I. 大写罗马编号。

        i. 小写罗马编号。

**MD写法：**

    1. 数字和点开始有序列表。

      1. 注意子列表的缩进位置。

          1. 三级列表。
          1. 编号会自动更正。

      1. 二级列表，编号自动更正为2。

    1. 返回一级列表。

**MD显示效果：**

1. 数字和点开始有序列表。

   1. 注意子列表的缩进位置。

      1. 三级列表。
      1. 编号会自动更正。

   1. 二级列表，编号自动更正为2。

1. 返回一级列表。

#### 列表续行、段落和代码块

**RST写法：**

    1. 列表项可以折行，
       对齐则自动续行。

    2. 列表项可包含多个段落。

        空行开始的新段落，
        新段落要和列表项内容对齐。

    3. 列表下的代码段注意对齐即可。

        ::

            $ printf "Hello, world.\n"

**RST显示效果：**

1. 列表项可以折行，
    对齐则自动续行。

2. 列表项可包含多个段落。

    空行开始的新段落，
    新段落要和列表项内容对齐。

3. 列表下的代码段注意对齐即可。

        $ printf "Hello, world.\n"

**MD写法：**

    1. 列表项可以折行，
      对齐则自动续行。

    2. 列表项可包含多个段落。

        空行开始的新段落必须缩进四个空格，
        段落才属于列表项。

    3. 列表中的代码块要缩进8个空格。

            $ printf "Hello, world.\n"

**MD显示效果：**

1. 列表项可以折行，
   对齐则自动续行。

2. 列表项可包含多个段落。

    空行开始的新段落必须缩进四个空格，
    段落才属于列表项。

3. 列表中的代码块要缩进8个空格。

        $ printf "Hello, world.\n"

#### 定义

**RST写法：**

    git
        Simple and beautiful.

    hg
        Another DVCS.

    subversion
        VCS with many constrains.

        Why not Git?

**MD：无**

----

## 分隔线

**RST写法和显示效果：**

    四条短线或以上显示为分隔线。

    ----

----

**MD写法和显示效果：**

    三条或更多短线（或星号、下划线）\显示为分隔线。
        ---
        ***
        ___

---
***
___


## 字体

#### 粗体和斜体

**RST写法和显示效果：**

    这是 **粗体** ，这是 *斜体* 。
    不留白的\ **粗体**\ 和\ *斜体*\ 效果。

这是**粗体**，这是*斜体*。
不留白的**粗体**和*斜体*效果。

**MD写法和显示效果：**

    这些都是 **粗体** 或 __粗体__ ，
    这些都是 *斜体* 或 _斜体_ 。

这些都是 **粗体** 或 __粗体__ ，
这些都是 *斜体* 或 _斜体_ 。

-----

#### 删除线

**RST写法和显示效果：**

    .. role:: strike
        :class: strike

    :strike:`删除线` 效果
    不留白的\ :strike:`删除线`\ 效果

~~删除线~~效果
不留白的~~删除线~~效果

**MD写法和显示效果：**

    ~~删除线~~ 效果

~~删除线~~ 效果


------

#### 下划线

**RST写法和效果：**

    .. role:: ul
        :class: underline

    :ul:`下划线` 效果
    不留白的\ :ul:`下划线`\ 效果

<u>下划线</u>效果
不留白的<u>下划线</u>效果

**MD的写法和效果：**

    <u>下划线</u> 效果

<u>下划线</u> 效果

-----

#### 上标、下标

**RST写法和效果：**

    Water: H\ :sub:`2`\ O
    E = mc\ :sup:`2`

Water: H<sub>2</sub>O
E = mc<sup>2</sup>

**MD写法和效果：**

    Water: H<sub>2</sub>O
    E = mc<sup>2</sup>
    注解：通过直接嵌入HTML代码实现。

Water: H<sub>2</sub>O
E = mc<sup>2</sup>
注解：通过直接嵌入HTML代码实现。

-----

#### 等宽字体

**RST写法和效果：**

    两个连续反引号嵌入代码，如: ``git status`` 。

两个连续反引号嵌入代码，如: `git status`。

**MD写法和效果：**

    行内反引号嵌入代码，如: `git status` 。

行内反引号嵌入代码，如: `git status` 。

-----

#### 引言

**RST写法：**
    反引号嵌入代码，如: `Got GitHub` by Jiang Xin.

**MD：无**

#### 清除标记空白(无)

**RST写法和效果：**

    标记符号前后空白\
    用\ **反斜线**\ 消除

标记符号前后空白用*反斜线*消除

**MD：无**

-----

## 链接

#### URL自动链接

**RST和MD相同：**

    网址 http://github.com/
    邮件 me@foo.bar

网址 http://github.com/
邮件 me@foo.bar

------

#### 文字链接

**RST写法：**

    - 访问 `Google <http://google.com/>`_ 。
    - 上面已定义，直接引用 google_ 链接。
    - 链接地址在后面定义，如： GitHub_ 。
    - 反引号括起多个单词的链接。如 `my blog`_ 。

    .. _GitHub: http://github.com
    .. _my blog: http://www.worldhello.net

**MD写法：**

    - 访问 [Google](http://google.com/)。
    - 上面已定义，直接引用[google](#Google) 链接。
    - 链接地址在后面定义，如： [GitHub][1] 。
    - 反引号括起多个单词的链接。如 [my blog][] 。

    [1]: http://github.com
    [my blog]: http://www.worldhello.ne


**显示效果：**

- 访问 [Google](http://google.com/)。
- 上面已定义，直接引用[google](#Google) 链接。
- 链接地址在后面定义，如： [GitHub][1] 。
- 反引号括起多个单词的链接。如 [my blog][] 。

 [1]: http://github.com
 [my blog]: http://www.worldhello.ne

-----

#### 内部跳转

**RST写法：**

    .. _fig1:

    .. figure:: https://longzeping.github.io/img/apple-touch-icon.png

        内部跳转图例

    上面定义的位置，可以：

    - 通过 fig1_ 跳转。
    - 或者 `点击这里 <#fig1>`__ 跳转。
    - 或者参见 :ref:`fig1`\ 。

**MD写法：**

    <a name="fig1" id="fig1"></a>
    ![](https://longzeping.github.io/img/apple-touch-icon.png)
        内部跳转图例

    上面定义的位置，可以：

    - 通过 [fig1](#fig1) 跳转。
    - 或者 [点击这里](#fig1) 跳转。
    - 或者参见 [内部跳转图例](#fig1) 。


**显示效果：**

<a name="fig1" id="fig1"></a>
![](https://longzeping.github.io/img/apple-touch-icon.png)
    内部跳转图例

上面定义的位置，可以：

- 通过 [fig1](#fig1) 跳转。
- 或者 [点击这里](#fig1) 跳转。
- 或者参见 [内部跳转图例](#fig1) 。
  
---------

#### 脚注(扩展实现)

**RST写法：**

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

**MD写法：**

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

**显示效果：**

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

（*备注：markdown不支持符号式脚注和单词式脚注，并且脚注数字符号的式样与RST也有差别。用MD并不能完全描述出RST的脚注*）

------

## 图片

**RST写法：**

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

**MD写法：**

    ![](https://longzeping.github.io/img/apple-touch-icon.png)
        图：GitHub logo

    GitHub Logo:![logo]

    带链接的图片：
    [![][logo]](https://github.com/)
        
    下图向右浮动：
    ![](https://longzeping.github.io/img/apple-touch-icon.png)

    [logo]: https://longzeping.github.io/img/apple-touch-icon.png "Logo"

**显示效果：**

![](https://longzeping.github.io/img/apple-touch-icon.png)
    图：GitHub logo

GitHub Logo:![logo]

带链接的图片：
[![][logo]](https://github.com/)
    
下图向右浮动：
  ![](https://longzeping.github.io/img/apple-touch-icon.png)

[logo]: https://longzeping.github.io/img/apple-touch-icon.png "Logo"


（*备注：用MD并不能完全描述出RST的图片功能*）

-------

## 表格

**RST写法：**

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

**MD写法：**

*备注说明：Markdown本身无法实现RST给出的这种带行列合并的复杂表格，但可以借助html代码实现。下面的表格不是Markdown标准语法实现，借助html语法实现。*

    <table>
    <tr><td>head1</td><td>head2</td><td>head3</td></tr>
    <tr><td rowspan=3>rowspan</td><td>cell</td><td>cell</td></tr>
    <tr><td colspan=2 rowspan=2>*colspan <br> *another lien</td></tr>
    <tr></tr>
    </table>

**显示效果：**

<table>
<tr><td>head1</td><td>head2</td><td>head3</td></tr>
<tr><td rowspan=3>rowspan</td><td>cell</td><td>cell</td></tr>
<tr><td colspan=2 rowspan=2>*colspan <br> *another lien</td></tr>
<tr></tr>
</table>

**gfm扩展实现的写法和显示效果：**

    下面是gfm扩展实现的Markdown简单表格：
    |head1|head2 |head3|
    |:---:|:---: |---: |
    |rowspan|cell|cell |
    |rowspan|cell|cell |
    |rowspan|cell|cell |

下面是gfm扩展实现的Markdown简单表格：
|head1|head2 |head3|
|:---:|:---: |---: |
|rowspan|cell|cell |
|rowspan|cell|cell |
|rowspan|cell|cell |

------

## 其它

#### 转义

**RST和MD一样：**

        反斜线作为转义字符，\禁止对后面 \*字符* 做语法解析。

反斜线作为转义字符，\禁止对后面 \*字符* 做语法解析。

-------

#### 注释

**RST写法：**

    .. 注释

    ..   

       缩进内容也是注释

**MD写法：**

    [//]:注释

    [//]:
        缩进内容也是注释
    


*备注说明：标准markdown中没有注释，属于扩展实现。[]里面内容自定义，[^_^]、[comment]、[//]等等，都可以用。*


------

#### 其它说明

* reStructedText的功能要多于Markdown，特别是表格、标注、脚注、链接、图片。

* 同时，reStructedText也比Markdown复杂，写无复杂格式的文章，Markdown比reStructureText更方便。
 
------