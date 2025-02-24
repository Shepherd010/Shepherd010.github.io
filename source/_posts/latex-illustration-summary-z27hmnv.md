---
title: LaTeX 插图总结
date: '2025-01-17 22:39:12'
updated: '2025-01-25 22:57:16'
tags:
  - Latex
permalink: /post/latex-illustration-summary-z27hmnv.html
comments: true
toc: true
---

# LaTeX 插图总结

## includegraphics  命令

用法

```tex
\includegraphics[选项]{文件}
```

最简单的例子，下面的命令将 a.png 插入文档中 （为了演示方便，本文所有的图片都和tex文件同目录）

```tex
\documentclass{article}

\usepackage{graphicx}

\begin{document}

\includegraphics[scale=1]{a.png}

\end{document}
```

[在线运行这个例子](https://app.moonpapers.com/project/share/5fb69ba90c491510c37bc21f)

参数详解

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210222707.jpeg)​

### 指定大小

将 a.jpg 插入文档并且它的宽度被缩放到 3 英寸，高度也会 按相应的比例缩放

```tex
\includegraphics[width=3in]{a.jpg}
```

用 \\textwidth 或 \\em 等的函数来 指定宽度，而不是用像 3 英寸这样的固定尺寸，将会使你的 LATEX 文 档更具通用性。例如：

```tex
\includegraphics[width=\textwidth]{a.jpg}
```

使得插入图形的宽度为文本行宽的 80%

```tex
\includegraphics[width=0.80\textwidth]{a.jpg}
```

[在线运行例子](https://app.moonpapers.com/project/share/5fb6a0e60c491510c37bc225)

## 浮动图形环境

一般情况下我们很少会把图片直接插入到我们的文本当中，而是会给它放置在一个叫做浮动体的东西中。这样图片可以有一些相对位置的变换，不会造成分页困难等问题。

有效的利用浮动图形机制 需要注意以下几点：

* 不要使用依赖于图形放置位置的文本。 使用如 `这幅图...`​ 或 `下面的图形...`​ 等短语要求所指的图形需在固定位置。 而像 `图 5...`​ 这样的短语则允许 图形出现在任意位置。
* 放松。一些使用者在发现图形没有十分 准确的出现在他们所想要的位置时，往往非常着急。这没有 必要，图形的放置是 LATEX 的工作，最好放松一些。

### 创建浮动体

```tex
\begin{figure}
  \centering
  \includegraphics[totalheight=2in]{a.jpg}
  \caption{Jay} \label{fig:graph}
\end{figure}
```

效果：

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210223280.jpeg)​

[在线运行例子](https://app.moonpapers.com/project/share/5fb6a3400c491510c37bc22a)

图形的放置

图形（figure）环境有一个可选参数项允许用户来指示图形有可能 被放置的位置。

这一可选参数项可以是下列字母的任意组合。

* h 当前位置。 将图形放置在 正文文本中给出该图形环境的地方。如果本页所剩的页面不够， 这一参数将不起作用
* t 顶部。 将图形放置在页面的顶部。
* b 底部。 将图形放置在页面的底部 。
* p 浮动页。 将图形放置在一只允许 有浮动对象的页面上。

注：

* 如果在图形环境中没有给出上述任一参数，则缺省为 [tbp]。
* 给出参数的顺序不会影响到最后的结果。因为在考虑这些参数时 LaTeX 总是尝试以 h-t-b-p 的顺序来确定图形的位置。所以 [hb] 和 [bh] 都使 LATEX 以 h-b 的顺序来排版。
* 给出的参数越多， LaTeX 的排版结果就会越好。 [htbp], [tbp], [htp], [tp] 这些组合得到的效果不错。

## 定制插图标题

对于标题的其它属性的 自由控制，利用[caption2 宏](http://www.ctex.org/documents/latex/graphics/footnode.html#foot4725)来完成。*caption2*宏包可以和很多与浮动对象有关的宏包一起使用

## 标题样式

用法

```tex
\usepackage[选项]{caption2}
```

选项参数如下图

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210223840.jpeg)​

将整个 整个文档中的标题都为 centerlast 式样。

```tex
\usepackage[centerlast]{caption}
```

caption 宏包的标题样式参数如下：

* normal 标题文本两边对齐，其中最后一行为左对齐。
* center 标题文本居中。
* flushleft 标题文本左对齐。
* flushright 标题文本右对齐。
* centerlast 标题文本两边对齐，其中最后一行居中。
* indent 与 normal 式样相似，只是标题文本从第二行开始， 每行行首缩进由命令 `\captionindent`​ 给出的长度。因为  `\captionindent`​ 的缺省值为零，通常用像  `\setlength{\captionindent}{1cm}`​ 这样的命令 来设置缩进值。
* hang 与 normal 式样相似，只是标题文本从第二行开始， 每行行首缩进与标题标记宽度相等的长度。

[在线运行例子](https://app.moonpapers.com/project/share/5fb6a5a00c491510c37bc22f)

## 并列图形

使图形并列所需的命令依赖于用户到底想怎样来组织图形。这里介绍两种常见的并列图形。

* 多个图形并列于一个图形环境中。
* 多个并列的浮动图形

## 多个图形并列于一个图形环境中

```tex
\begin{figure}
  \centering
  \includegraphics[scale=0.5]{d.jpg}
  \hspace{1in}
  \includegraphics[scale=0.5]{c.jpg}
  \caption{两张图片并排在一个浮动体}
\end{figure}
```

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210224351.jpeg)​

[在线运行这个例子](https://app.moonpapers.com/project/share/5fb6a6e40c491510c37bc238)

### 多个并列的浮动图形

若将 `\caption`​ 命令放到每个小页环境 中，则每个小页环境就生成一浮动图形

```tex
\begin{figure}
  \begin{minipage}[t]{0.5\linewidth}
    \centering
    \includegraphics[scale=0.5]{d.jpg}
    \caption{Jay}
    \label{fig:side:a}
  \end{minipage}%
  \begin{minipage}[t]{0.5\linewidth}
    \centering
    \includegraphics[scale=0.5]{c.jpg}
    \caption{叶惠美}
    \label{fig:side:b}
  \end{minipage}
\end{figure}
```

效果如下图

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210224948.jpeg)​

[在线运行例子](https://app.moonpapers.com/project/share/5fb6a7430c491510c37bc23f)

## 图编号如何关联章节

通过引入`\usepackage{amsmath}`​包中的`\numberwithin{figure}{section}`​命令，我们可以将Latex中Figure的编号和所在的章节关联起来 （​**此方法已经过时**​）

自 2018年起LaTeX自带了 \\counterwithin 命令。

此命令的解释为：

> 将另一个计数器添加到现有计数器，当计数器增加时会导致重置

参考：[LaTeX/Counters](https://en.wikibooks.org/wiki/LaTeX/Counters#Counter_manipulation)

还可以参考 [Overleaf, Online LaTeX Editor](https://www.overleaf.com/learn/latex/Counters) 的解释

> This macro is included in the LATEX format since April 2018, if you're using an older version, you'll have to use the`chngctr`​package

完整例子代码

```tex
\documentclass{ctexart}

\usepackage{graphicx}
\counterwithin{figure}{section}

\begin{document}


\section{Jay}

一直以音乐制作人身份从事作词、作曲、编曲等工作的周杰伦，18岁时因创作吴宗宪的“屋顶”、“三暝三日”、“你比从前快乐”；许茹芸的“蜗牛”；王力宏的“打开爱”以及徐若宣的“姐你睡了吗?”等歌曲打开了知名度。害羞、内向似邻家大男孩的他凭着新作“可爱女人”的强力宣传，从幕后走到幕前成为歌坛耀眼的新人，首张同名专辑《周杰伦》于2000年11月3日在台湾正式发行。

\begin{figure}[htbp]
    \begin{center}
        \includegraphics{a.jpg}
    \end{center}
    \caption{Jay}
\end{figure}

\section{范特西}

周杰伦的出现，让人们相信台湾创造本土R\&B的可能性；周杰伦的走红，彻底地宣布音乐新声代的来临。作曲、填词、编曲、演唱样样俱精的周杰伦，首张同名专辑《Jay杰伦》推出后，销售势如破竹，不单有“音乐新人王”称号，他自成一格的R\&B演绎方法，更被誉为陶吉吉的劲敌。


\begin{figure}[htbp]
    \begin{center}
        \includegraphics{b.jpg}
    \end{center}
    \caption{范特西}
\end{figure}

\begin{figure}[htbp]
    \begin{center}
        \includegraphics{b-2.jpg}
    \end{center}
    \caption{范特西}
\end{figure}


\end{document}
```

[在线运行例子](https://app.moonpapers.com/project/share/5fb6a7a80c491510c37bc248)

效果：

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210225575.jpeg)​

​![](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224210226165.jpeg)​

## 参考资料

* [http://www.ctex.org/documents/latex/graphics/graphics.html](http://www.ctex.org/documents/latex/graphics/graphics.html)
* [https://en.wikibooks.org/wiki/LaTeX/Counters#LaTeX\_default\_counters](https://en.wikibooks.org/wiki/LaTeX/Counters#LaTeX_default_counters)
