---
title:  latex和markdown支持的公式写法整理
data:  2023年8月23日10:46:59
tags:  maekdown
categories:  maekdown
update:  2023年8月23日10:47:37
---



# 目录

1. [希腊字母大小写](#希腊字母大小写)
2. [标记符号](#标记符号)
3. [分式](#分式)
4. [根式](#根式)
5. [运算符](#运算符)
   
    * [二元运算符](#二元运算符)
    * [关系符号](#关系符号)
    * [集合](#集合)
    * [逻辑](#逻辑)
6. [微积分](#微积分)
7. [空格](#空格)
8. [标注符号](#标注符号)
9. [箭头](#箭头)
10. [括号和定界符](#括号和定界符)
11. [多行公式](#多行公式)
12. [分段函数](#分段函数)
13. [矩阵](#矩阵)
    * [转置](#转置)
    * [无括号](#无括号)
    * [方括号](#方括号)
    * [圆形括号](#圆形括号)
    * [行列式写法](#行列式写法)

    由于markdown可以支持latex【非常强大】的数学公式的渲染因此下文整理内容两种均支持。
    markdown借鉴latex的公式输入
    主要是在jupyter-notebook和CSDN等基本多支持markdown，因此做这个公式输入的整理还是方便日后自己查找使用。

    需要记住的是，以下公式均写在\$\$内来被识别为latex公式。

# 希腊字母大小写

大写的首字母将全拼首字母大写即可。  
\$\全拼\$

|小写字母|表达式|大写字母|表达式|
|---|---|---|---|
|α|\alpha|Α|\Alpha|
|β|\beta|Β|\Beta|
|γ|\gamma|Γ|\Gamma|
|δ|\delta|Δ|\Delta|
|ε|\epsilon|Ε|\Epsilon|
|ζ|\zeta|Ζ|\Zeta|
|η|\eta|Η|\Eta|
|θ|\theta|Θ|\Theta|
|ι|\iota|Ι|\Iota|
|κ|\kappa|Κ|\Kappa|
|λ|\lambda|Λ|\Lambda|
|μ|\mu|Μ|\Mu|
|ν|\nu|Ν|\Nu|
|ξ|\xi|Ξ|\Xi|
|ο|\omicron|Ο|\Omicron|
|π|\pi|Π|\Pi|
|ρ|\rho|Ρ|\Rho|
|σ|\sigma|Σ|\Sigma|
|τ|\tau|Τ|\Tau|
|υ|\upsilon|Υ|\Upsilon|
|φ|\phi|Φ|\Phi|
|χ|\chi|Χ|\Chi|
|ψ|\psi|Ψ|\Psi|
|ω|\omega|Ω|\Omega|

# 标记符号

上标 ^  
下标 _  

下标的斜体和直立体意义不同
|示例|表达式|
|----|------|
|$x^{2}$|x^{2}|
|$a_{2}$|a_{2}|
|$x^{i+j}$|x^{i+j}|
|$x_{i}$|x_{i}|
|$x_{\text i}$|x_{\text i}|
|$\bar{a}$|\bar|
|$\acute{a}$|\acute|
|$\breve{a}$|\breve|
|$\grave{a}$|\grave|
|$\dot{a}$|\dot|
|$\ddot{a}$|\ddot|
|$\hat{a}$|\hat|
|$\check{a}$|\check|
|$\breve{a}$|\breve|
|$\tilde{a}$|\tilde|
|$\vec{a}$|\vec|
|$\overline{a+b+c}$|\overline|
|$\underline{a+b+c}$|\underline|
|$\overbrace{a+b+c}$|\overbrace|
|$\underbrace{a+b+c}$|\underbrace|
|$\overbrace{a + \underbrace{b + c}_{1.0} + d}^a$|\overbrace{a + \underbrace{b + c}_{1.0} + d}^a|

# 分式

\frac{分子}{分母}
单个字符还可以这么写：
\frac 分子 分母

\dfrac是显示类型(display)，可以显示的更大一点，作用一样

|示例|表达式|
|---|---|
|$\frac{1}{2}$|\frac{1}{2}|
|$\dfrac{1}{2}$|\dfrac{1}{2}|
|$\frac{x+y}{1+z}$|\frac{x+y}{1+z}|

# 根式

\sqrt[根的次数]{数值}  
默认是平方根

|示例|表达式|
|---|---|
|$\sqrt 2$|\sqrt 2|
|$\sqrt{x+y}$|\sqrt{x+y}|
|$\sqrt[3]{x+y}$|\squrt[3]

# 运算符

## 二元运算符

|名称|运算符|表达式|
|----|------|------|
|加|+|+|
|减|-|-|
|乘|$\times$|\times|
|点乘|$\cdot$|\cdot|
|除|$\div$|\div|
|正负|$\pm$|\pm|
|负正|$\mp$|\mp|

## 关系符号

|名称|运算符|markdown|
|----|------|--------|
|大于|$\gt$|\gt|
|小于|$\lt$|\le|
|大于等于|$\ge$|\ge|
|小于等于|$\le$|\le|
|远大于|$\gg$|\gg|
|远小于|$\ll$|\ll|
|不等于|$\ne$|\ne|
|约等于|$\approx$|\approx|
|恒等于|$\equiv$|\eqdiv|
|几何全等|$\cong$|\cong|
|几何相似|$\sim$|\sim|
|同余|$\equiv$|\eqiv|
|同余n|$\pmod n$|\pmod n|
|取模|$\bmod$|\bmod|

## 集合

|名称|运算符|表达式|
|----|------|------|
|真子集|$\subsetneqq$|\subsetqq
|空集|$\varnothing$|\varthing
|空集|$\emptyset $|\emptyset
|属于|$\in $|\in
||$\ni $|\ni
|不属于|$\notin $|\notin
|子集|$\subset $|\subset
||$\supset $|\supset
|非子集|$\not\subset $|\not\subset
|真子集|$\subseteq $|\subseteq
||$\supseteq $|\supseteq
|并集|$\cup $|\cup
|并集|$\bigcup $|\bigcup
|交集|$\cap $|\cap
|交集|$\bigcap $|\bigcap
|补集|$\complement_{b}A$|\complement_{b}A|
|多重集|$\uplus $|\uplus
|多重集|$\biguplus $|\biguplus
||$\sqsubset $|\sqsubset
||$\sqsupset $|\sqsupset
||$\sqcap $|\sqcap
||$\sqsubseteq $|\sqsubseteq
||$\sqsupseteq $|\sqsupseteq
||$\vee $|\vee
||$\wedge $|\wedge
|集合中的减法|$\setminus $|\setminus
|实数集|$\R$|\R|
|有理数集|$\mathbb{Q}$|\mathbb{Q}|
|自然数|$\N$|\N|
|整数集|$\Z$|\Z|
|正整数集|$\N^{+}$|\N^{+}

## 逻辑

|含义|示例|markdown|
|----|----|--------|
|因为|$\because$|\because|
|所以|$\therefore$|\therefore|
|任意|$\forall$|\forall|
|存在|$\exist$|\exist|
|不存在|$\nexists$|\exist|
|逻辑与|$\wedge$|\wedge|
|逻辑或|$\vee$|\vee|
|逻辑与|$\bigwedge$|\bigwedge|
|逻辑或|$\bigvee$|\bigvee|

# 微积分

|算符|实例|markdown|
|----|----|--------|
|求和|$\sum\limits_{i=1}^{n}i$|\sum\limits_{j=1}^{n}i|
|求和|$\sum_{i=1}^{n}i$|\sum\limits_{j=1}^{n}i|
|求积|$\prod\limits_{i=1}^{n}i$|\prod\limits_{j=1}^{n}i|
|求积|$\prod_{i=1}^{n}i$|\prod\limits_{j=1}^{n}i|
|极限|$\lim\limits_{x\rightarrow\infty}\frac{1}{x}$|\lim\limits_{x\rightarrow\infty}\frac{1}{x}|
|多元函数极限|$\lim\limits_{\substack{x\to\infty \\y\to\infty }} \dfrac{1}{x+y}$|\lim\limits_{ \substack{ x\to\infty \\y\to\infty } }|
|积分|$\int_{0}^{2} f(x) \mathrm{d} x$|\int_{0}^{2} f(x) \mathrm{d} x|
|微分|$\mathrm{d}f(x)$|\mathrm{d}f(x)|
|多重积分|$\iint\limits_{D} g(x,y) \mathrm{d} x$|\iint\limits_{D} g(x,y) \mathrm{d} x|
|导数|$y\prime$|y\prime|
|导数|$\dfrac{\mathrm{d}y}{\mathrm{d}x}$|\dfrac{\mathrm{d}y}{\mathrm{d}x}|
|偏微分|$\partial{a}$|\partial{a}|
|偏导数|$\dfrac{\partial{a}}{\partial{b}}$|\frac{\partial{a}}{\partial{b}}|
|回路积分|$\oint\limits_{D} x^2 \mathrm{d} x$|\oint\limits_{D} x^2 \mathrm{d} x|
|双重回路积分|$\oiint\limits_{D} (x+y)^{\frac{2}{x}} \mathrm{d} x$|\oiint\limits_{D} (x+y)^{\frac{2}{x}} \mathrm{d} x|

# 空格

|说明|示例|markdown|
|----|----|--------|
|空格距离：-3/18 em|$123\!123 $|123\\!123 |
|空格距离：3/18 em|$123\,123$|123\\,123|
|空格距离：4/18 em|$123\:123 $|123\\:123 |
|空格距离：5/18 em|$123\;123 $|123\\;123 |
|空格距离：1 em|$123\quad123 $|123\quad123 |
|空格距离：2 em|$123\qquad123 $|123\qquad123 |

# 标注符号

# 箭头

|箭头|markdown|
|----|--------|
|$\uparrow$|\uparrow|
|$\downarrow$|\downarrow|
|$\updownarrow$|\updownarrow|
|$\Uparrow$|\Uparrow|
|$\Downarrow$|\Downarrow|
|$\Updownarrow$|\Updownarrow|
|$\rightarrow$|\rightarrow|
|$\leftarrow$|\leftarrow|
|$\leftrightarrow$|\leftrightarrow|
|$\Rightarrow$|\Rightarrow|
|$\Leftarrow$|\Leftarrow|
|$\Leftrightarrow$|\Leftrightarrow|
|$\longrightarrow$|\longrightarrow|
|$\longleftarrow$|\longleftarrow|
|$\longleftrightarrow$|\longleftrightarrow|
|$\Longrightarrow$|\Longrightarrow|
|$\Longleftarrow$|\Longleftarrow|
|$\Longleftrightarrow$|\Longleftrightarrow|
|$\mapsto$|\mapsto|
|$\longmapsto$|\longmapsto|
|$\hookleftarrow$|\hookleftarrow|
|$\hookrightarrow$|\hookrightarrow|
|$\rightharpoonup$|\rightharpoonup|
|$\leftharpoondown$|\leftharpoondown|
|$\rightleftharpoons$|\rightleftharpoons|
|$\leftharpoonup$|\leftharpoonup|
|$\rightharpoondown$|\rightharpoondown|
|$\leadsto$|\leadsto|
|$\nearrow$|\nearrow|
|$\searrow$|\searrow|
|$\swarrow$|\swarrow|
|$\nwarrow$|\nwarrow|

# 括号和定界符

|算式|markdown|
|----|--------|
|$(, )$|(, )|
|$[, ]$|[, ]|
|$\lang, \rang $或$\langle, \rangle$|\lang, \rang 或 \langle, \rangle|
|$\lvert, \rvert$|\lvert, \rvert|
|$\lVert, \rVert$|\lVert, \rVert|
|$\lbrace, \rbrace $或$ "\{, \}"$|\lbrace, \rbrace 或 "\\{, \\}"|
|$\lfloor, \rfloor$|\lfloor, \rfloor|
|$\lceil, \rceil$|\lceil, \rceil|
|$(x)$|(x)|
|$\big( x \big)$|\big( x \big)|
|$\Big( x \Big)$|\Big( x \Big)|
|$\bigg( x \bigg)$|\bigg( x \bigg)|
|$\Bigg( x \Bigg)$|\Bigg( x \Bigg)|
|$\Bigg(\bigg(\Big(\big((x)\big)\Big)\bigg)\Bigg)$|\Bigg(\bigg(\Big(\big((x)\big)\Big)\bigg)\Bigg)|
|$\Bigg[\bigg[\Big[\big[[x]\big]\Big]\bigg]\Bigg]$|\Bigg[\bigg[\Big[\big[[x]\big]\Big]\bigg]\Bigg]|
|$\Bigg \langle \bigg \langle \Big \langle\big\langle\langle x \rangle\big\rangle\Big\rangle\bigg\rangle\Bigg\rangle$|\Bigg \langle \bigg \langle \Big \langle\big\langle\langle x \rangle\big\rangle\Big\rangle\bigg\rangle\Bigg\rangle|
|$\Bigg\lvert\bigg\lvert\Big\lvert\big\lvert\lvert x \rvert\big\rvert\Big\rvert\bigg\rvert\Bigg\rvert$|\Bigg\lvert\bigg\lvert\Big\lvert\big\lvert\lvert x \rvert\big\rvert\Big\rvert\bigg\rvert\Bigg\rvert|
|$\Bigg\lVert\bigg\lVert\Big\lVert\big\lVert\lVert x \rVert\big\rVert\Big\rVert\bigg\rVert\Bigg\rVert$|\Bigg\lVert\bigg\lVert\Big\lVert\big\lVert\lVert x \rVert\big\rVert\Big\rVert\bigg\rVert\Bigg\rVert|


# 多行公式

多行环境:\代表换行，默认右对其，可以在等号前加&实现等号对齐，具体是&后一对齐

$$\begin{align}
a\\f\\c
\end{align}$$

```latex
$$\begin{align}
a\\f\\c
\end{align}$$
```

# 分段函数

$$f(x)=
\begin{cases}
\sin x, -1\le x\le2\\
\cos x, else
\end{cases}
$$
```latex
$$f(x)=
\begin{cases}
\sin x, -1\le x\le2\\
\cos x, else
\end{cases}
$$
```

# 矩阵

## 转置

$$ \bf B^T $$

​```latex
$$ \bf B^T $$
```

$$
\begin{bmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{bmatrix}^{\bf T}
$$

```latex
$$
\begin{bmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{bmatrix}^{\bf T}
$$
```

## 无括号

没有括号的矩阵

$$
\begin{matrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{matrix}
$$

```latex
$$
\begin{matrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{matrix}
$$
```

## 方括号

方括号的矩阵

$$
\begin{bmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{bmatrix}^{\bf T}
$$

```latex
$$
\begin{bmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{bmatrix}^{\bf T}
$$
```

## 圆形括号

圆括号的矩阵

$$
\begin{pmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{pmatrix}
$$

```latex
$$
\begin{pmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{pmatrix}
$$
```

## 行列式写法

$$
\begin{vmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{vmatrix}
$$

```latex
$$
\begin{vmatrix}
a & b&c&\cdots&d\\
\vdots & \vdots & \vdots & \ddots &\vdots \\
e & k & f & \cdots & 0
\end{vmatrix}
$$
```

## 带省略号

$$
\left[
\begin{matrix}
a & b & \cdots & a\\
b & b & \cdots & b\\
\vdots & \vdots & \ddots & \vdots\\
c & c & \cdots & c
\end{matrix}
\right]
\tag{5}
$$

```latex
$$
\left[
\begin{matrix}
a & b & \cdots & a\\
b & b & \cdots & b\\
\vdots & \vdots & \ddots & \vdots\\
c & c & \cdots & c
\end{matrix}
\right]
\tag{5}
$$
```

## 带横线/竖线分割

$$
\left[
\begin{array}{c|cc}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{array}
\right]
\tag{6}
$$

```latex
$$
\left[
\begin{array}{c|cc}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{array}
\right]
\tag{6}
$$
```

横线用 \hline 分割

$$
\left[
    \begin{array}{c|cc}
    1 & 2 & 3 \\ \hline
    4 & 5 & 6 \\
    7 & 8 & 9
    \end{array}
\right]
\tag{7}
$$

```latex
$$
\left[
    \begin{array}{c|cc}
    1 & 2 & 3 \\ \hline
    4 & 5 & 6 \\
    7 & 8 & 9
    \end{array}
\right]
\tag{7}
$$
```

|算式|markdown|描述|
|----|--------|----|
|$\sin$|\sin|
|$\cos$|\cos|
|$\tan$|\tan|
|$\cot$|\cot|
|$\sec$|\sec|
|$\csc$|\csc|
|$\bot$|\bot|垂直
|$\angle$|\angle|角
|$40^\circ$|40^\circ|
|$\ast $|\ast |星号
|$\star $|\star |
|$\mid $|\mid |竖线
|$\nmid $|\nmid |
|$\circ $|\circ |圈
|$\bullet $|\bullet |
|$\cdot $|\cdot |点
|$\wr $|\wr |
|$\diamond $|\diamond |
|$\Diamond $|\Diamond |
|$\triangle $|\triangle |
|$\bigtriangleup $|\bigtriangleup |
|$\bigtriangledown $|\bigtriangledown |
|$\triangleleft $|\triangleleft |
|$\triangleright $|\triangleright |
|$\lhd $|\lhd |
|$\rhd $|\rhd |
|$\unlhd $|\unlhd |
|$\unrhd $|\unrhd |
|$\circ $|\circ |
|$\bigcirc $|\bigcirc |
|$\odot $|\odot |
|$\bigodot $|\bigodot |点积
|$\oslash $|\oslash |
|$\ominus $|\ominus |
|$\otimes $|\otimes |
|$\bigotimes $|\bigotimes |克罗内克积
|$\oplus $|\oplus |
|$\bigoplus $|\bigoplus |异或
|$\dagger $|\dagger |
|$\ddagger $|\ddagger |
|$\amalg $|\amalg |
|$\models $|\models |
|$\prec $|\prec |
|$\succ $|\succ |
|$\sim $|\sim |
|$\perp $|\perp |
|$\preceq $|\preceq |
|$\succeq $|\succeq |
|$\simeq $|\simeq |
|$\mid $|\mid |
|$\asymp $|\asymp |
|$\parallel $|\parallel |
|$\approx $|\approx |
|$\cong $|\cong |
|$\doteq $|\doteq |
|$\propto $|\propto |
|$\bowtie $|\bowtie |
|$\Join $|\Join |
|$\smile $|\smile |
|$\frown $|\frown |
|$\vdash $|\vdash |
|$\dashv $|\dashv |
|$\lim$|\lim|
|$\rightarrow$|\rightarrow|
|$\infty$|\infty|
|$\lim_{n\rightarrow+\infty}n$|\lim_{n\rightarrow+\infty}n|
|$\prime $|\prime |求导
|$\int $|\int |积分
|$\iint $|\iint |双重积分
|$\iiint $|\iiint |三重积分
|$\oint $|\oint |曲线积分
|$\nabla $|\nabla |梯度
|$\dots $|\dots |一般用于有下标的序列
|$\ldots $|\ldots |
|$\cdots $|\cdots |纵向位置比\dots稍高
|$\vdots $|\vdots |竖向
|$\ddots $|\ddots |
|$\dots$
|$\aleph$|\aleph|
|$\hbar$|\hbar|
|$\imath$|\imath|
|$\jmath$|\jmath|
|$\ell$|\ell|
|$\wp$|\wp|
|$\Re$|\Re|
|$\Im$|\Im|
|$\mho$|\mho|
|$\nabla$|\nabla|
|$\surd$|\surd|
|$\top$|\top|
|$\bot$|\bot|
|$\neg$|\neg|
|$\flat$|\flat|
|$\natural$|\natural|
|$\sharp$|\sharp|
|$\backslash$|\backslash|
|$\partial$|\partial|
|$\Box$|\Box|
|$\clubsuit$|\clubsuit|
|$\diamondsuit$|\diamondsuit|
|$\heartsuit$|\heartsuit|
|$\spadesuit$|\spadesuit|
