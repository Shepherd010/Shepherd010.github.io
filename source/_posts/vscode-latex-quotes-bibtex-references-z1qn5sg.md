---
title: VSCode+latex引用bibtex参考文献
date: '2025-01-18 19:05:27'
updated: '2025-01-25 23:15:36'
excerpt: >-
  本文介绍了在VSCode中使用LaTeX和BibTeX进行文献引用的步骤。首先，用户需在与.tex文件同一文件夹下创建一个.bib文件，例如ref.bib，并将所需引用的文献以BibTeX格式保存。接着，在LaTeX文档中导入所需的包，使用\cite命令进行文献引用，并指定参考文献文件和排版风格。最后，提供了编译输出的方法，特别强调在VSCode中，通过保存操作自动执行LaTeX编译，并在终端中运行BibTeX命令来生成最终的PDF文档。该过程简化了传统的手动编译步骤，使得文献管理更加高效便捷。
tags:
  - Latex
permalink: /post/vscode-latex-quotes-bibtex-references-z1qn5sg.html
comments: true
toc: true
---



---

* VSCode+latex引用bibtex参考文献_vscode 使用latex bib-CSDN博客
* [https://blog.csdn.net/JohnJim0/article/details/103309475](https://blog.csdn.net/JohnJim0/article/details/103309475)

---

### 操作步骤

#### 新建lib

 在.tex同一文件夹下，新建一个.bib文件，例如ref.bib，把要引用的文献的bibtex格式复制粘贴进去，这个各大搜索引擎如谷歌学术什么的应该都有，以下是一个例子，注意其中mirowski2018learning为引用文献的变量名

```bibtex
@misc{mirowski2018learning,
    title={Learning to Navigate in Cities Without a Map},
    author={Piotr Mirowski and Matthew Koichi Grimes and Mateusz Malinowski and Karl Moritz Hermann and Keith Anderson and Denis Teplyashin and Karen Simonyan and Koray Kavukcuoglu and Andrew Zisserman and Raia Hadsell},
    year={2018},
    eprint={1804.00168},
    archivePrefix={arXiv},
    primaryClass={cs.AI}
}
```

#### latex编写

```;atex
\documentclass[UTF8]{ctexart} 

\usepackage{cite} % 导入引用的包，能够使用\cite

\begin{document}

% \cite括号内为引用文献的变量名，\cite前要有一个空格
% 在正文中引用，如果不引用则在参考文献部分中不显示该文献
Learning to Navigate in Cities Without a Map \cite{mirowski2018learning}. 

\bibliography{ref} % 导入lib，ref为“ref.lib"的文件名
\bibliographystyle{ieeetr} % 参考文献排版风格，这个是IEEE transaction的，其他可以自查
\end{document}
```

#### 编译显示

 标准编译命令如下，对于文件名"refrences.tex"的tex文件，在命令行需执行命令顺序如下

```bash
latex references.tex
bibtex references
latex references.tex
latex references.tex
```

 但是对于VSCode，由于latex  
 workshop的插件，使得只需要保存就是自动执行latex编译"latex references.tex"，所以具体步骤可以稍作修改，如下

* 编辑好tex文件后，保存(快捷键cmd(ctrl)+s)
* 在VSCode终端内运行命令"bibtex reference"
* 回到tex在保存

 此时就可以预览生成好的pdf文件了，效果如下，注意添加参考文献即更改lib文件之后需重新执行以上操作。  
 ![在这里插入图片描述](http://127.0.0.1:3606/assets/network-asset-c1f43b3940bb5b848e373222e0ffc5c2-20250118190527-nhv1bob.png)​

‍
