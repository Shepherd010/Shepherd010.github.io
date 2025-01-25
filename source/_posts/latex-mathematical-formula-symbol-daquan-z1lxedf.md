---
title: Latex数学公式符号大全
date: '2024-12-28 21:46:01'
updated: '2025-01-25 22:56:19'
tags:
  - Latex
permalink: /post/latex-mathematical-formula-symbol-daquan-z1lxedf.html
comments: true
toc: true
---



## 基本符号

### 小写希腊字母

 **注：部分希腊字母在数学公式中常以变量形式出现，例如**​**$\epsilon$**​**在数学中一般写法为**​**$\varepsilon$**​ **，**​**$\phi$**​**在数学中通常写作**​**$\varphi$**

|符号|语法|符号|语法|符号|语法|
| ------| ------------| ------| -----------------| ------| ------------|
|$\alpha$|\\alpha|$\beta$|\\beta|$\gamma$|\\gamma|
|$\theta$|\\theta|$\varepsilon$|\\varepsilon|$\delta$|\\delta|
|$\mu$|\\mu|$\nu$|\\nu|$\eta$|\\eta|
|$\zeta$|\\zeta|$\lambda$|\\lambda|$\psi$|\\psi|
|$\sigma$|\\sigma|$\xi$|\\xi|$\tau$|\\tau|
|$\phi$|\\phi|$\varphi$|\\varphi|$\rho$|\\rho|
|$\chi$|\\chi|$\omega$|\\omega|$\pi$|\\pi|

### 大写希腊字母

 大写希腊字母通常是小写希腊字母的LATEX  
语法第一个字母改为大写，见下表

|符号|语法|符号|语法|符号|语法|
| ------| -------------| ------| ------------| ------| ------------|
|$\Sigma$|\\Sigma|$\Pi$|\\Pi|$\Delta$|\\Delta|
|$\Gamma$|\\Gamma|$\Psi$|\\Psi|$\Theta$|\\Theta|
|$\Lambda$|\\Lambda|$\Omega$|\\Omega|$\Phi$|\\Phi|
|$\Xi$|\\Xi|||||

### 常用字体

 默认的字体为$ABCdef$，也就是\\mathnormal{ABCdef}（当然，打公式的时候不需要加上这个\\mathnormal，直接打字母就是这个效果）

|字体|语法|字体|语法|
| ------| -----------------------| ------| ----------------------|
|$\mathrm{ABCdef}$|\\mathrm{ABCdef}|$\mathbf{ABCdef}$|\\mathbf{ABCdef}|
|$\mathit{ABCdef}$|\\mathit{ABCdef}|$\pmb{ABCdef}$|\\pmb{ABCdef}|
|$\mathscr{ABCdef}$|\\mathscr{ABCdef}|$\mathcal{ABCdef}$|\\mathcal{ABCdef}|
|$\mathfrak{ABCdef}$|\\mathfrak{ABCdef}|$\mathbb{ABCdef}$|\\mathbb{ABCdef}|

### 常见运算符

|运算符|语法|运算符|语法|运算符|语法|
| --------| --------------------| --------| -----------------------| --------| -------------|
|$+$|+|$-$|-|$\times$|\\times|
|$\pm$|\\pm|$\cdot$|\\cdot|$\ast$|\\ast|
|$\cup$|\\cup|$\cap$|\\cap|$\circ$|\\circ|
|$\lor$|\\lor或\\vee|$\land$|\\land或\\wedge|$\lnot$|\\lnot|
|$\oplus$|\\oplus|$\ominus$|\\ominus|$\otimes$|\\otimes|
|$\odot$|\\odot|$\oslash$|\\oslash|$\bullet$|\\bullet|
|$\sqrt{x}$|\\sqrt{x}|$\sqrt[n]{x}$|\\sqrt[n]{x}|||

### 大尺寸运算符

|运算符|语法|运算符|语法|运算符|语法|
| --------| -------------| --------| ---------------| --------| ------------|
|$\sum$|\\sum|$\prod$|\\prod|$\int$|\\int|
|$\bigcup$|\\bigcup|$\bigcap$|\\bigcap|$\oint$|\\oint|
|$\bigvee$|\\bigvee|$\bigwedge$|\\bigwedge|$\iint$|\\iint|
|$\coprod$|\\coprod|$\bigsqcup$|\\bigsqcup|$\oiint$|\\oiint|

### 常见关系符号

|符号|语法|符号|语法|符号|语法|
| ------| ----------------| ------| ----------------| ------| -------------|
|$<$|\<|$>$|\>|$=$|\=|
|$\leq$|\\leq|$\geq$|\\geq|$\neq$|\\neq|
|$\ll$|\\ll|$\gg$|\\gg|$\equiv$|\\equiv|
|$\subset$|\\subset|$\supset$|\\supset|$\approx$|\\approx|
|$\subseteq$|\\subseteq|$\supseteq$|\\supseteq|$\sim$|\\sim|
|$\in$|\\in|$\ni$|\\ni|$\propto$|\\propto|
|$\vdash$|\\vdash|$\dashv$|\\dashv|$\models$|\\models|
|$\mid$|\\mid|$\parallel$|\\parallel|$\perp$|\\perp|
|$\notin$|\\notin|$\Join$|\\Join|$\nsim$|\\nsim|
|$\subsetneq$|\\subsetneq|$\supsetneq$|\\supsetneq|||

### 数学模式重音符

|符号|语法|符号|语法|符号|语法|
| ------| -------------------| ------| ---------------------| ------| --------------------|
|$\hat{a}$|\\hat{a}|$\bar{a}$|\\bar{a}|$\tilde{a}$|\\tilde{a}|
|$\vec{a}$|\\vec{a}|$\dot{a}$|\\dot{a}|$\ddot{a}$|\\ddot{a}|
|$\widehat{abc}$|\\widehat{abc}|$\widetilde{abc}$|\\widetilde{abc}|$\overline{abc}$|\\overline{abc}|

### 箭头

 如果需要长箭头，只需要在语法前面加上\\long，例如\\longleftarrow即为$\longleftarrow$，如果加上\\Long则变为双线长箭头，例如\\Longleftarrow即为$\Longleftarrow$

|符号|语法|符号|语法|符号|语法|
| ------------------------| -----------------------| ------| ------------------------| ------| ------------------------|
|$\leftarrow$|\\leftarrow|$\rightarrow$|\\rightarrow|$\leftrightarrow$|\\leftrightarrow|
|$\Leftarrow$|\\Leftarrow|$\Rightarrow$|\\Rightarrow|$\Leftrightarrow$|\\Leftrightarrow|
|$\uparrow$|\\uparrow|$\downarrow$|\\downarrow|$\updownarrow$|\\updownarrow|
|$\Uparrow$|\\Uparrow|$\Downarrow$|\\Downarrow|$\Updownarrow$|\\Updownarrow|
|$\leftharpoonup$|\\leftharpoonup|$\leftharpoondown$|\\leftharpoondown|$\rightharpoonup$|\\rightharpoonup|
|$\rightharpoondown$|\\rightharpoondown|$\rightleftharpoons$|\\rightleftharpoons|$\leftrightharpoons$|\\leftrightharpoons|
|⟺        \\iff⟺|\\iff|$\mapsto$|\\mapsto|||

### 括号

|括号|语法|括号|语法|括号|语法|
| ------| ------------------------| ------| ----------------------| ------| ------------------------|
|$()$|()|$[]$|[]|$\{\}$|\\{\\}|
|$\lfloor\rfloor$|\\lfloor\\rfloor|$\lceil\rceil$|\\lceil\\rceil|$\langle\rangle$|\\langle\\rangle|

### 大尺寸括号

|括号|语法|括号|语法|
| ------| ----------------------------------------------------------| ------| -----------------------------------------------------------|
|$\left(\right)$|\\left( \\right)|$\left[ \right]$|\\left[ \\right]|
|$\overbrace{x_1x_2\ldots x_n}^{n}$|\\overbrace{x\_1x\_2\\ldots x\_n}\^{n}|$\underbrace{x_1x_2\ldots x_n}_{n}$|\\underbrace{x\_1x\_2\\ldots x\_n}\_{n}|

 **注：大尺寸的()和[]是可以根据公式的高度自动调节的，例如**

```latex
\arg\min_{\theta}
\left[
    -\sum_{i=1}^{n}
    \left[
        \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) +
        (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
    \right]
\right]
```

 $\arg\min_{\theta} \left[ -\sum_{i=1}^{n} \left[ \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) + (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)})) \right] \right]$

 可以看出，括号高度可以框住整个公式

 因此在这种大型的公式中，使用大尺寸括号视觉效果更美观

### 其他常见符号

|符号|语法|符号|语法|符号|语法|
| ------| ---------------| ------| ----------------| ------| ------------|
|$\forall$|\\forall|$\exist$|\\exist|$\angle$|\\angle|
|$\emptyset$|\\emptyset|$\partial$|\\partial|$\infty$|\\infty|
|$\ldots$|\\ldots|$\cdots$|\\cdots|$\dots$|\\dots|
|$\vdots$|\\vdots|$\ddots$|\\ddots|$\prime$|\\prime|
|$\because$|\\because|$\therefore$|\\therefore|$\Box$|\\Box|
|$\triangle$|\\triangle|$\S$|\\S|||

## 数学公式写法

### 上下标

* ​`^`​：上标
* ​`_`​：下标

 例如:

* ​`\sum_{i=1}^{n}X_n`​表示$\sum_{i=1}^{n}X_n$
* ​`\int_{0}^{\infty}x^2dx`​表示$\int_{0}^{\infty}x^2dx$
* ​`\prod_{i=1}^{n}X_n`​表示$\prod_{i=1}^{n}X_n$

### 分数

 使用`\frac{}{}`​即可，例如`\frac{a}{b}`​表示$\frac{a}{b}$

### 插入文字

 使用`\text`​，例如`\text{hello,world!}`​表示$\text{hello,world!}$

### 常见函数

|函数|语法|函数|语法|函数|语法|
| ------| ------------------------------------| ------| ------------------------------------| ------| -------------------------------------|
|$\log()$|\\log()|$\ln()$|\\ln()|$\lg()$|\\lg()|
|$\max$|\\max|$\min$|\\min|$\lim_{x \to \infty}$|\\lim\_{x \\to \\infty}|
|$\arg\max_{c \in C}$|\\arg\\max\_{c \\in C}|$\arg\min_{c \in C}$|\\arg\\min\_{c \\in C}|$\exp$|\\exp|

### 矩阵、行列式

 `&`​表示分隔元素，`\\`​表示换行

```latex
A=
\begin{pmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{pmatrix}
```

 $A=$

$$
\begin{pmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{pmatrix}
$$

 A\=(a11​a21​​a12​a22​​)

```latex
A=
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
```

 $A=$

$$
\begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}
$$

 A\=[a11​a21​​a12​a22​​]

```latex
A=
\begin{Bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{Bmatrix}
```

 $A=$

$$
\begin{Bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{Bmatrix}
$$

 A\={a11​a21​​a12​a22​​}

```latex
A=
\begin{vmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{vmatrix}
```

 $A=$

$$
\begin{vmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{vmatrix}
$$

 A\= ​a11​a21​​a12​a22​​ ​

```latex
A=
\begin{Vmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{Vmatrix}
```

 $A=$

$$
\begin{Vmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{Vmatrix}
$$

 A\= ​a11​a21​​a12​a22​​ ​

```latex
A=
\begin{matrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{matrix}
```

 $A=$

$$
\begin{matrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{matrix}
$$

 A\=a11​a21​​a12​a22​​

### 多行公式对齐

 使用`\begin{split} \end{split}`​，在需要对齐的地方添加`&`​符号，注意需要用`\\`​来换行。

 例如：

```latex
\begin{split}
L(\theta)
&=	\arg\max_{\theta}\ln(P_{All})\\
&=	\arg\max_{\theta}\ln\prod_{i=1}^{n}
    \left[
        (h_{\theta}(\mathbf{x}^{(i)}))^{\mathbf{y}^{(i)}}\cdot
        (1-h_{\theta}(\mathbf{x}^{(i)}))^{1-\mathbf{y}^{(i)}}
    \right]\\
&=	\arg\max_{\theta}\sum_{i=1}^{n}
	\left[
		\mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) +
		(1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
	\right]\\
&=	\arg\min_{\theta}
	\left[
        -\sum_{i=1}^{n}
        \left[
            \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) +
            (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
        \right]
	\right]\\
&=	\arg\min_{\theta}\mathscr{l}(\theta)
\end{split}
```

 <span data-type="inline-math" data-subtype="math" data-content="l

(

θ

)" contenteditable="false" class="render-node"></span>

$$
\begin{split} L(\theta) &= \arg\max_{\theta}\ln(P_{All})\\ &= \arg\max_{\theta}\ln\prod_{i=1}^{n} \left[ (h_{\theta}(\mathbf{x}^{(i)}))^{\mathbf{y}^{(i)}}\cdot (1-h_{\theta}(\mathbf{x}^{(i)}))^{1-\mathbf{y}^{(i)}} \right]\\ &= \arg\max_{\theta}\sum_{i=1}^{n} \left[ \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) + (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)})) \right]\\ &= \arg\min_{\theta} \left[ -\sum_{i=1}^{n} \left[ \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) + (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)})) \right] \right]\\ &= \arg\min_{\theta}\mathscr{l}(\theta) \end{split}
$$

 L(θ)​\=argθmax​ln(PAll​)\=argθmax​lni\=1∏n​[(hθ​(x(i)))y(i)⋅(1−hθ​(x(i)))1−y(i)]\=argθmax​i\=1∑n​[y(i)ln(hθ​(x(i)))+(1−y(i))ln(1−hθ​(x(i)))]\=argθmin​[−i\=1∑n​[y(i)ln(hθ​(x(i)))+(1−y(i))ln(1−hθ​(x(i)))]]\=argθmin​l(θ)​ 上例中，在`=`​前添加了`&`​，因此实现**等号对齐**；

 `\begin{split} \end{split}`​语法**默认为右对齐**，也就是说如果不在任何地方添加`&`​符号，则公式默认右侧对齐，例如：

```latex
\begin{split}
L(\theta)
=	\arg\max_{\theta}\ln(P_{All})\\
=	\arg\max_{\theta}\ln\prod_{i=1}^{n}
    \left[
        (h_{\theta}(\mathbf{x}^{(i)}))^{\mathbf{y}^{(i)}}\cdot
        (1-h_{\theta}(\mathbf{x}^{(i)}))^{1-\mathbf{y}^{(i)}}
    \right]\\
=	\arg\max_{\theta}\sum_{i=1}^{n}
	\left[
		\mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) +
		(1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
	\right]\\
=	\arg\min_{\theta}
	\left[
        -\sum_{i=1}^{n}
        \left[
            \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) +
            (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
        \right]
	\right]\\
=	\arg\min_{\theta}\mathscr{l}(\theta)
\end{split}
```

 上述LATEX代码没有添加`&`​符号，则公式[右对齐](https://so.csdn.net/so/search?q=%E5%8F%B3%E5%AF%B9%E9%BD%90&spm=1001.2101.3001.7020)：  
 <span data-type="inline-math" data-subtype="math" data-content="l

(

θ

)" contenteditable="false" class="render-node"></span>

$$
\begin{split} L(\theta) = \arg\max_{\theta}\ln(P_{All})\\ = \arg\max_{\theta}\ln\prod_{i=1}^{n} \left[ (h_{\theta}(\mathbf{x}^{(i)}))^{\mathbf{y}^{(i)}}\cdot (1-h_{\theta}(\mathbf{x}^{(i)}))^{1-\mathbf{y}^{(i)}} \right]\\ = \arg\max_{\theta}\sum_{i=1}^{n} \left[ \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) + (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)})) \right]\\ = \arg\min_{\theta} \left[ -\sum_{i=1}^{n} \left[ \mathbf{y}^{(i)}\ln(h_{\theta}(\mathbf{x}^{(i)})) + (1-\mathbf{y}^{(i)})\ln(1-h_{\theta}(\mathbf{x}^{(i)})) \right] \right]\\ = \arg\min_{\theta}\mathscr{l}(\theta) \end{split}
$$

 L(θ)\=argθmax​ln(PAll​)\=argθmax​lni\=1∏n​[(hθ​(x(i)))y(i)⋅(1−hθ​(x(i)))1−y(i)]\=argθmax​i\=1∑n​[y(i)ln(hθ​(x(i)))+(1−y(i))ln(1−hθ​(x(i)))]\=argθmin​[−i\=1∑n​[y(i)ln(hθ​(x(i)))+(1−y(i))ln(1−hθ​(x(i)))]]\=argθmin​l(θ)​ 如果希望**左对齐**，例如

```latex
\begin{split}
&\ln h_{\theta}(\mathbf{x}^{(i)})
=	\ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}
= 	-\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\
&\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
=	\ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}})
= 	-\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}})
\end{split}
```

 $)$

$$
\begin{split} &\ln h_{\theta}(\mathbf{x}^{(i)}) = \ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}} = -\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\ &\ln(1-h_{\theta}(\mathbf{x}^{(i)})) = \ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}) = -\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}}) \end{split}
$$

 ​lnhθ​(x(i))\=ln1+e−θTx(i)1​\=−ln(1+eθTx(i))ln(1−hθ​(x(i)))\=ln(1−1+e−θTx(i)1​)\=−θTx(i)−ln(1+eθTx(i))​ 除了`\begin{split} \end{split}`​，也可以用`\begin{align} \end{align}`​，用法与`split`​相同，对齐方式也相同；

 只有一点不同：​**采用align环境会默认为每一条公式编号**​（如下例），split  
则不会编号。

```latex
\begin{align}
&\ln h_{\theta}(\mathbf{x}^{(i)})
=	\ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}
	= -\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\
&\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
=	\ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}})
	= -\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}})
\end{align}
```

 $)$

$$
\begin{align} &\ln h_{\theta}(\mathbf{x}^{(i)}) = \ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}} = -\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\ &\ln(1-h_{\theta}(\mathbf{x}^{(i)})) = \ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}) = -\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}}) \end{align}
$$

 ​lnhθ​(x(i))\=ln1+e−θTx(i)1​\=−ln(1+eθTx(i))ln(1−hθ​(x(i)))\=ln(1−1+e−θTx(i)1​)\=−θTx(i)−ln(1+eθTx(i))​​ 但可以在align后加一个`*`​号，则align环境也可以取消公式自动编号，如下：  
 (也就是说`align*`​和`split`​的用法完全相同)

```latex
\begin{align*}
&\ln h_{\theta}(\mathbf{x}^{(i)})
=	\ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}
	= -\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\
&\ln(1-h_{\theta}(\mathbf{x}^{(i)}))
=	\ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}})
	= -\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}})
\end{align*}
```

 $)$

$$
\begin{align*} &\ln h_{\theta}(\mathbf{x}^{(i)}) = \ln\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}} = -\ln(1+e^{\theta^T \mathbf{x}^{(i)}})\\ &\ln(1-h_{\theta}(\mathbf{x}^{(i)})) = \ln(1-\frac{1}{1+e^{-\theta^T \mathbf{x}^{(i)}}}) = -\theta^T \mathbf{x}^{(i)}-\ln(1+e^{\theta^T \mathbf{x}^{(i)}}) \end{align*}
$$

 ​lnhθ​(x(i))\=ln1+e−θTx(i)1​\=−ln(1+eθTx(i))ln(1−hθ​(x(i)))\=ln(1−1+e−θTx(i)1​)\=−θTx(i)−ln(1+eθTx(i))​

### 方程组

 使用`\begin{cases} \end{cases}`​

 例如：

```latex
\begin{cases}
    \begin{split}
        p &= P(y=1|\mathbf{x})=
        	\frac{1}{1+e^{-\theta^T\mathbf{X}}}\\
        1-p &= P(y=0|\mathbf{x})=1-P(y=1|\mathbf{x})=
        	\frac{1}{1+e^{\theta^T\mathbf{X}}}
    \end{split}
\end{cases}
```

 $X$

$$
\begin{cases} \begin{split} p &= P(y=1|\mathbf{x})= \frac{1}{1+e^{-\theta^T\mathbf{X}}}\\ 1-p &= P(y=0|\mathbf{x})=1-P(y=1|\mathbf{x})= \frac{1}{1+e^{\theta^T\mathbf{X}}} \end{split} \end{cases}
$$

 ⎩ ⎨ ⎧​p1−p​\=P(y\=1∣x)\=1+e−θTX1​\=P(y\=0∣x)\=1−P(y\=1∣x)\=1+eθTX1​​​ 注意[LATEX语法](https://so.csdn.net/so/search?q=LATEX%E8%AF%AD%E6%B3%95&spm=1001.2101.3001.7020)可以嵌套使用，上例即为`\begin{cases} \end{cases}`​下嵌套了`begin{split} \end{split}`​。

 也可以将公式和文字结合起来，例如：

```latex
\text{Decision Boundary}=
\begin{cases}
    1\quad \text{if }\ \hat{y}>0.5\\
    0\quad \text{otherwise}
\end{cases}
```

 $\text{Decision Boundary}=$

$$
\begin{cases} 1\quad \text{if}\quad \hat{y}>0.5\\ 0\quad \text{otherwise} \end{cases}
$$

 Decision Boundary\={1ify\^\>0.50otherwise  
 注：`\quad`​表示空格。
