---
title: LaTeX 超链接
date: '2025-01-17 22:41:23'
updated: '2025-01-25 23:17:00'
tags:
  - Latex
permalink: /post/latex-hyperlink-27n7kt.html
comments: true
toc: true
---



latex两种超链接的方法

## 使用hyperref包

​`使用hyperref`​包，将交叉引用模块变成超链接，甚至连目录都会

```latex
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,            %链接颜色
    linkcolor=blue,             %内部链接
    filecolor=magenta,          %本地文档
    urlcolor=cyan,              %网址链接
    pdftitle={Overleaf Example},
    pdfpagemode=FullScreen,
    }
```

上面的命令显然会使得目录显示为蓝色，如果想要变成黑色，需要将linkcolor设置为black

## 链接网址

## 显示网址: \\url{...}

```latex
\url{ https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.197.pdf}
```

## 不显示网址而显示想要的内容: \\href{...}

```latex
\href{https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.197.pdf}{AES}
```

样式分别如下：

​![](undefined)
