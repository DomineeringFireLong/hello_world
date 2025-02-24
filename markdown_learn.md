[TOC]

# Markdown语法
**轻量级的标记语言，可在纯文本文档中写入格式元素**
**markdown file->markdown解析->html/pdf**    

---
## 1.标题
# 标题等级1  <h1>标题等级1</h1> 

标题等级1
===============
标题等级2
---------------
## 标题等级2
<h2>标题等级2</h2>  

### 标题级别3

<h3>标题级别3</h3>

---

## 2.段落
直接回车，空白行分隔
换行，两个或多个空格结束一行，然后键入return。  
<p>html创建段落的方法,换行符"< br>".</p>
<p>html，This is the first line.<br>
And this is the second line.</p>
普通段落不该用空格或制表符来缩进  
不同的文字块之间，一定要空行以示区分，不然就会被归入同一文字块中。





---
## 3.字体

**加粗文字1**     __加粗文字2__
*斜体1*       _斜体2_
***粗斜体 ***   ___粗斜体___
~~删除线~~


<del>删除线</del>
<ins>下划线</ins>
<mark>标记</mark>
<small>小号</small>
<sup>上标</sup>
<sub>下标</sub>
<code>代码</code>
<kbd>键盘</kbd>
<var>变量</var>
<samp>样本</samp>
<cite>引用</cite>
quote>引用</quote>

---
## 4.注释

[//]:特殊字符注释
[%%]:特殊字符注释
<!-- Markdown 本身没有注释语法,可以用HTML注释 -->
[Markdown 的链接引用语法]:实现注释效果
[//]:工具类的东西学习起来一定要从实践到理论，动手比整理资料有用。
注释中间不能有空格

> 引用区块：This is a blockquote with two paragraphs.
>
> This is a blockquote with two paragraphs  

> 引用区块：This is a blockquote with two paragraphs.  

> This is a blockquote with two paragraphs  

---
## 5.区块引用
> 区块引用可以嵌套
>> 二级区块1
>> 二级区块2
>>> 三级区块1
>>> 三级区块2
>>
> 一级区块


分割线：注意要空一行，否则成了二级标题

---
## 6.列表

- [x] :吃饭
- [x] :工作
- [ ] :睡觉 


Markdown 支持有序列表和无序列表。 无序列表使用星号、加号或是减号作为列表标记。
- 无序列表1
- 无序列表2
- 无序列表3
+ 列表内容
* 列表内容

- 列表可以嵌套,用tab键分级   
    - 2级列表内容1
    - 2级列表内容1
    - 2级列表内容1
        - 三级列表内容1
        - 三级列表内容1
            - 四级列表内容1

1. 有序列表1,序号和内容中间有空格
    列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符。    
    第二段

2. 有序列表2
3. 有序列表3

---
## 7.表格
| 表格标题1 | 表格标题2 | 表格标题3 |
| --------- | :---------: | ---------:|
| 内容1     | 内容2     |   内容3  |
| 内容1     | 内容2     |   内容3  |

<!--  
- 有一个就行，为了对齐，多加了几个,文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右

 -->

---

## 8.代码块

1.缩进 4 个空格或是 1 个制表符

    code1: 这是一个代码区块。
2.反引号
单行代码：代码之间分别用一个反引号包起来即可；：`反引号引住：code`
代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行
```C++
code2: 这是一个代码区块。
code2: 这是一个代码区块。
code2: 这是一个代码区块。
```

---

# Markdown纯文本进阶语法
## 字体(html)
### 字体样式
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=red>我是红色</font>
<font color=#008000>我是绿色</font>
<font color=Blue>我是蓝色</font>
<font size=5>我是尺寸</font>
<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>

### 为文字添加背景色

[//]:style标签和属性不被支持，所以这里只能是借助table,tr,td等表格标签的bgcolor属性来实现背景色

<table><tr><td bgcolor=lightgrey>背景色lightgrey</td></tr></table>
<table bgcolor=lightgrey><tr><td>背景色lightgrey</td></tr></table>

---
## 超链接
插入一些图片，链接。  
由于Markdown只是关注于纯文本，因此这些操作都要通过引用来完成。  
Markdown 支持的链接语法： 行内式、参考式、自动链接。  
不管哪种，链接文字都是用 [方括号] 来标记。

在新页面中打开的话,html的超链接语法：
<a href="https://www.baidu.com">百度</a>

### 行内式
方块括号后面紧接着圆括号并插入网址链接

链接
This is [xhl website](http://example.com/ "Title") inline link.
[xhl website](http://example.net/) has no title attribute.

图片   

![Alt pic](/path/to/img.jpg)
![Alt pic](/path/to/img.jpg "Optional title")

### 参考式
在链接文字的括号后面再接上另一个方括号，第二个方括号里要填入用以辨识链接的标记：
在文件的任意处，把标记的链接内容定义  

链接
[id1]: http://example.com/  "an example"
This is [an example][id1] reference-style link.

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"

图片  

[id2]: /path/to/img.jpg  "Optional title attribute"
![Alt pic][id2]

### 图片放到分档内的方法
1. 用base64转码工具把图片转成一段字符串
2. 把字符串填到基础格式中链接的那个位置。
3. 由于图片转成base64编码，会非常的大，一般至少都要上千行，这个时候会发现插入的这一长串字符串会把整个文章分割开，非常影响编写文章时的体验。这时候就可以用参考式，把大段的base64字符串放在文章末尾，然后在文章中通过一个id来调用，文章就不会被分割的这么乱了。


### 自动链接  
用尖括号包起来，Markdown 就会自动把它转成链接
<http://example.com/>


### Latex公式
\$ 表示行内公式 \$$ 表示整行公式
可以参考[math.meta官网](https://math.meta.stackexchange.com/)

$ X\stackrel{F}{\longrightarrow}Y $

### 脚注
文章[^1]
[^1]: 文章链接

___
# Markdown、HTML、Mermaid、JSON 和 TXT关系
TXT 是纯文本文件格式，没有任何格式化   

        只包含纯文本内容，没有样式、图像等。  
        不支持任何格式化或复杂结构。
        适合存储简单的文本数据。
        TXT 是最基础的文本格式，其他格式（如 Markdown、HTML、JSON）都可以看作是对 TXT 的扩展。

HTML（HyperText Markup Language）是用于创建网页的标准标记语言

        HTML 是Web的基础语言，用标签（如 <h1>、<p>、<a> 等）来定义网页的内容、结构、样式和行为。  
        HTML 是最基础的网页格式，其他格式（如 Markdown、JSON）都可以看作是对 HTML 的扩展。  
        语法复杂，支持丰富的结构和样式。与 CSS 和 JavaScript 结合，可实现动态网页。
        Markdown 可以转换为 HTML，但 HTML 不能直接转换为 Markdown。
        HTML 的功能比 Markdown 更强大，但 Markdown 更易于使用。

Markdown 是一种轻量级标记语言，旨在简化文本格式化。

        使用简单的符号（如 #、*、- 等）来定义标题、列表、加粗、链接等基本格式。
        Markdown 的语法简单，但功能有限，无法实现复杂的样式和结构。
        Markdown 的功能比 HTML 更有限，但 Markdown 更易于使用。
        Markdown 不是基于 HTML，功能上相当于简化的html, 且可以直接嵌入 HTML 代码。

Mermaid 是一种基于文本的图表生成工具

        Mermaid 是一种独立的图表生成工具，其语法与 Markdown 无关。
        Mermaid 可以生成多种图表，如流程图、时序图、类图、状态图等，并支持多种样式和主题。
        Mermaid 的语法简单，但功能有限，无法实现复杂的图表。
        Mermaid 通常嵌入在 Markdown 或 HTML 文件中。
        在 Markdown 文件中，Mermaid 图表通常通过特定的标记（如 ```mermaid）来嵌入。

JSON（JavaScript Object Notation）是一种轻量级的数据交换格式。

        JSON 是一种数据交换的文本格式，主要用于存储和传输数据。   
        JSON 用键值对（key-value pairs）来表示数据。  （像：字典）
        JSON 可以与 HTML 结合，用于动态网页的数据传输。
        JSON 与 Markdown、HTML、Mermaid 不同，它主要用于数据交换。


