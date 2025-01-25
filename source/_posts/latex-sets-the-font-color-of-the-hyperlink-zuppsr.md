---
title: Latex设置超链接的字体颜色
date: '2025-01-17 22:41:35'
updated: '2025-01-25 23:16:30'
tags:
  - Latex
permalink: /post/latex-sets-the-font-color-of-the-hyperlink-zuppsr.html
comments: true
toc: true
---



首先需要导入color包：

```latex
\usepackage{color}
```

 然后导入超链接包

```latex
\usepackage{hyperref}
```

 设置超链接的颜色

```latex
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=blue,  
    urlcolor=blue,
    citecolor=cyan,
}
%改变颜色
```

 然后就可以通过href插入超链接了，具体语法：

```latex
\href{超链接}{描述}
```

 如果想要把颜色改回来或者设置成不是hypersetup里的颜色怎么办？

```latex
\href{超链接}{\textcolor{想要修改的颜色}{描述}}
```

 这样就能够修改成自己想要的颜色了
