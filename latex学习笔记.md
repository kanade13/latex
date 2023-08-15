# latex学习笔记

## 填写正文内容

### 0.查看宏包的文档

命令行输入:`texdoc diagbox`

### 1.被占用符号以命令形式输入

```latex
\# \$ \% \& \{ \}
\textbackslash %反斜杠

\ldots ...
```

更多符号要查看symbols文档

### 2.数学模式

0. 总是需要amsmath宏包,mathtools对amsmath做了补充和增强(例如长公式折行时确定空格长度)

1. 注意,不管是多短的行内还是显示公式,都要使用数学模式

​		显示(display)公式:

- 简单的不编号公式:`\]`和`\]`标识
- 基本的编号公式用`equation`环境
- 对齐环境`align`

   2.数学字母

- 括号:使用`\left,\right`放大

- 逗号,冒号`\colon`            $\colon$

- 二项式系数 `\binom`
- 点 `\cdot`

### 3.数字单位的一揽子解决方案:siunitx

`\num{1.235e96}`   1.235 x 10^96^

`\SI{299792458}{m/s}`		(\SI带千分位空格,\si没有)

还有建表格时按个位对齐的功能

### 4.chemformula编写化学式的宏包

(应该用不到)))

### 5.列表与文本块

- 有标题的列表 `enumerate`

- 不编号 `itemize`

- 有标题 `description`

- ![image-20230814222138424](C:\Users\王一\AppData\Roaming\Typora\typora-user-images\image-20230814222138424.png)


  **重复单元格格式的写法**

  ```latex
  \begin{tabular}{|c|c|c|c|c|p{4em}|p{4em}|}
  \begin{tabular}{|*{5}{c|}*{2}{p{4em}|}}
  
  即*{n}{格式}=n个{格式}
  ```

  **整列修饰格式的写法**

  辅助格式 > 和 <，用于给列格式前后加上修饰命令.

  ```latex
  \begin{tabular}{>{\itshape}r<{*}l}
  ```

  插入 \centering 等命令改变 p 列格式的对齐方式，一般还要加额外的命令 \arraybackslash 以免出错 

### 6.定理类环境

```latex
\newtheorem{thm}{定理}[section]

\begin{thm}
\end{thm}
```

### 7.抄录代码

```latex
\verb|#include<stdio.h>|
```

#### 代码高亮:listing宏包

#### 算法结构宏包:clrscode(算法导论使用了),algorithm2e

### 8.图标与浮动环境

#### 表格相关

[在线生成表格代码](https://www.tablesgenerator.com/latex_tables)

#####  单元格处理:multirow(好几行合并成一行),makecell(一个单元格里插好几行)

举例:multirow宏包:

```latex
\multicolumn{⟨n⟩}{⟨column-spec⟩}{⟨item⟩}
```

<img src="C:\Users\王一\AppData\Roaming\Typora\typora-user-images\image-20230814110729484.png" alt="image-20230814110729484" style="zoom:50%;" />

- 长表格:longtable(过长的表格自动换页)
- 定宽表格(不太常用):xtabular
- 表线控制:booktabs(画三线表) ,diagbox(画斜线)

#### 图片相关

使用graphicx宏包

#### 浮动环境

```latex
\begin{table}\centering
\begin{tabular}{|ccccc|}\hline
1&2&3&4&5\\
1&2&3&4&5\\
1&2&3&4&5\\
1&2&3&4&5\\\hline
\end{tabular}
\caption{标题}
\end{table}
```



### 9.自动化工具

bibtex宏包:用于生成参考文献

jetref工具管理.bib数据库



## 设计文档格式

### 基本原则

需要遵循**格式与内容分离**的原则,例如:

```latex
推荐:\emph{important},\caption{流程图}
不推荐:\textit{important},\textbf{图 1:} 流程图
```

### 使用宏包

- 不要重复造轮子
- 不要引入不需要的宏包,避免造成兼容性问题

### 字体字号

1. 字体

   **在LaTeX中，一个字体有5种属性**

   **字体编码**
   正文字体编码：OT1、T1、EU1等
   数学字体编码：OML、OMS、OMX等
   **字体族**
   罗马字体：笔画起始处有装饰
   无衬线字体：笔画起始处无装饰
   打字机字体：每个字符宽度相同，又称等宽字体
   **字体系列**
   粗细
   宽度
   **字体形状**
   直立
   斜体
   伪斜体
   小型大写
   **字体大小**

   第一列和第二列的命令区别在于作用域

<img src="C:\Users\王一\AppData\Roaming\Typora\typora-user-images\image-20230814232524886.png" alt="image-20230814232524886" style="zoom:80%;" />

在传统的正文印刷中，普遍认为衬线体能带来更佳的可读性。尤其是在大段落的文章中，衬线增加了阅读时对字母的视觉参照。

而无衬线体往往被用在标题、较短的文字段落或者一些通俗读物中。相比严肃正经的衬线体，无衬线体给人一种休闲轻松的感觉。

2. 字号
   <img src="C:\Users\王一\AppData\Roaming\Typora\typora-user-images\image-20230814223042701.png" alt="image-20230814223042701" style="zoom: 80%;" />

中文字号:	ctex文档 `\zihao{5}`

### 对齐

### 空白间距 
`\hspace{2cm},\vspace{3cm}`

### 版面布局
geometry(设置纸张大小)宏包,fancyhdr(设置页眉页脚)

### 分页断行 

```latex
\linebreak 断行,\\ 强制换行(正常的话正文不用)
\pagebreak \newpage(另起一页) \clearpage(比newpage多一个功能,保证前一页图表也画出来)
正常情况\linebreak\pagebreak基本不会用到
```

### 盒子

\mobx{内容}

\parbox{4em}{内容},minipage

### 在导言区设置格式

\parindent 段首缩进量

\parskip 两端之间垂直间距

\linespread 行距

\pagestyle 设置页眉页脚格式

\thesection 修改节的标号的输出格式

\labelenumi

\descriptionlabel

\figurename

ctex宏包设置中文格式,tocloft宏包设置 内容 表 图 目录的宏包

### 自定义格式(好用)

例如:

```latex
格式:\newcommand{\⟨name⟩}[⟨num⟩]{⟨definition⟩}
命令名  参数个数(可选,缺省默认0)  命令的具体定义
\newcommand{\tnss}{The not so Short Introduction to \LaTeXe}
\newcommand{\prg}[1]{\textcolor{blue}\texttt{#1}\index{#1 programe}}

\begin{document}
程序 \prg{sort}很有用.
\end{document}
```

**只需要改导言区的设置就可以更改格式**

### 章节标题

ctex中用\ctexset定制

### 浮动标题

caption宏包

### 列表环境

enumitem宏包

例如`\setlist{nosep}`控制列表间距
