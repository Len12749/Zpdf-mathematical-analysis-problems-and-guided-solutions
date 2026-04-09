# Taylor公式



先说结论，Taylor公式是用多项式进行近似逼近可导函数的工具之一.

其中，Peano余项和Lagrange余项的作用分别是定性/定量.

前者常常在求极限中起到关键作用（利用高阶无穷小性质）.

后者常常在研究收敛域时起到关键作用（即数值分析）.

本文将给出一些直接且简单的应用，其更广范围上的应用是无穷无尽的.



## 1.含Peano余项的Taylor公式

若函数$f$在$x_0$存在直至$n$阶导数，则有$f(x)=T_n(x)+o((x-x_0)^n)$.

其中$T_n(x)$为其对应的Taylor多项式：
$$
f(x)=f(x_0)+\frac{f'(x_0)}{1!}(x-x_0)^1+\frac{f''(x_0)}{2!}(x-x_0)^2+\cdots+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n+o((x-x_0)^n)
$$
特别地，若令$x_0=0$，则称其为麦克劳林展开式，形式上更为美观一些.

在使用时，例如$\ln{x}$，由于$\ln1=0$，在$x=1$处展开不含无理数，我们试图在$x=1$处展开.

而为了让它有更为简洁的麦克劳林形式，故将函数作平移变换，研究$\ln(1+x)$.

此时$\ln(1+x)$在$x=0$处就有了非常简洁的展开形式：
$$
\ln(1+x)=x-\frac{x^2}{2}+\frac{x^3}{3}+\cdots+(-1)^{n-1}\frac{x^n}{n}+o(x^n)
$$
对于常见Taylor展开的形式，我们通常可以使用数学归纳法进行证明，是时候给出一些常见的结论了.



## 2.常见的含Peano余项的Taylor展开结论

$$
\begin{align}
e^x=&1+x+\frac{x^2}{2!}+\cdots+\frac{x^n}{n!}+o(x^n)\\
\sin{x}=&x-\frac{x^3}{3!}+\frac{x^5}{5!}+\cdots+(-1)^{n-1}\frac{x^{2n-1}}{(2n-1)!}+o(x^n)\\
\cos{x}=&1-\frac{x^2}{2!}+\frac{x^4}{4!}+\cdots+(-1)^n\frac{x^{2n}}{(2n)!}+o(x^n)\\
\ln(1+x)=&x-\frac{x^2}{2}+\frac{x^3}{3}+\cdots+(-1)^{n-1}\frac{x^n}{n}+o(x^n)\\
(1+x)^k=&1+kx+\frac{k(k-1)}{2!}x^2+\cdots+\frac{k(k-1)\cdots(k-n+1)}{n!}x^n+o(x^n)
\end{align}
$$

值得注意的是，上述的$n$有的是从0开始，有的是从1开始.

由于Taylor多项式在此有无穷阶，我们不对这种细枝末节进行规范性叙述，熟记即可.

除此之外，由于两个余项所对应的Taylor多项式是相同的，故下文不再给出Lagrange余项展开结论.



## 3.Peano余项在求极限中的简单展开应用

求极限：
$$
\lim\limits_{x\to0}\frac{\sin{x}-x}{x^3}
$$

### 证明

$$
原式=\lim\limits_{x\to0}\frac{x-\frac{x^3}{3!}+o(x^3)-x}{x^3}=\lim\limits_{x\to0}\frac{-\frac{x^3}{3!}}{x^3}+\lim\limits_{x\to0}\frac{o(x^3)}{x^3}=-\frac{1}{6}+0=-\frac{1}{6}
$$



## 4.Peano余项在求极限中的复合展开应用

题目取自南开大学2025年数学分析考研试题，求极限：
$$
\lim\limits_{x\to0}\frac{\sin{(\ln{(1+x)})-\ln(1+\sin{x})}}{\sin{(\sin{x})}-\ln(1+\ln(1+x))}
$$

### 证明

$Taylor$展开：
$$
\lim\limits_{x\to0}\frac{\ln(1+x)-\frac{(\ln(1+x))^3}{6}+o(x^3)-[\sin{x}-\frac{\sin^2x}{2}+\frac{\sin^3x}{3}+o(x^3)]}{\sin{x}-\frac{\sin^3x}{6}+o(x^3)-[\ln(1+x)-\frac{(\ln(1+x))^2}{2}+\frac{(\ln(1+x))^3}{3}+o(x^3)]}
$$
进一步展开：
$$
\lim\limits_{x\to0}\frac{x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^3}{6}-[x-\frac{x^3}{6}-\frac{x^2}{2}+\frac{x^3}{3}]+o(x^3)}{x-\frac{x^3}{6}-\frac{x^3}{6}-[x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^2}{2}+\frac{x^3}{3}]+o(x^3)}
$$
即：
$$
\lim\limits_{x\to0}\frac{o(x^3)}{x^2+o(x^2)}=\lim\limits_{x\to0}\frac{o(x^2)}{x^2+o(x^2)}=0
$$
特别地，在解题时为追求速度，我们可以根据分母来只看某一次的系数，但存在风险.



## 5.含Lagrange余项的Taylor公式（Taylor定理）

若函数$f$在$[a,b]$上存在直至$n$阶的连续导函数，在$(a,b)$上存在$n+1$阶导函数.

则对任意给定的$x,x_0\in[a,b]$，至少存在一点$\xi\in(a,b)$，使得：
$$
f(x)=f(x_0)+\frac{f'(x_0)}{1!}(x-x_0)^1+\frac{f''(x_0)}{2!}(x-x_0)^2+\cdots+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n\\
+\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}
$$
这个定理写的并不是那么清晰，实际上，不妨设$x>x_0$，若在$x_0$处展开，而$x$处代入.

显然可以视其为$a$到$b$上的展开，即此处$a$就是$x_0$，$b$就是$x$，那么就有：
$$
\xi\in(x_0,x)
$$
特别地，还可以改写为：
$$
\xi=x_0+\theta(x-x_0),\theta\in(0,1)
$$


## 6.利用Lagrange余项的Taylor展开进行数值分析

计算$e$的值，要求误差不超过$10^{-6}$.

### 证明

由Taylor定理：
$$
e=1+1+\frac{1}{2!}+\frac{1}{3!}+\cdots+\frac{1}{n!}+\frac{e^{\theta}}{(n+1)!},\theta\in(0,1)
$$
由于：
$$
\frac{e^\theta}{(n+1)!}<\frac{3}{(n+1)!}
$$
当$n=9$时：
$$
\frac{3}{(n+1)!}<10^{-6}
$$
而此时多项式值为：
$$
e\approx 2.718285
$$
证毕.

我们看到，由于这个放缩的存在，只要令$n$足够大，那么余项无穷小.

因此，可以引用类似思想去求得幂级数的收敛域，此处不予展示.



## 7.幂级数及收敛域

$$
\begin{align}
\sin{x}=&\mathop\Sigma\limits_{n=1}^\infty(-1)^{n-1}\frac{x^{2n-1}}{(2n-1)!}&,x\in\R
\\
\cos{x}=&\mathop\Sigma\limits_{n=0}^\infty(-1)^{n}\frac{x^{2n}}{(2n)!}&,x\in\R
\\
e^x=&\mathop\Sigma\limits_{n=0}^\infty\frac{x^n}{n!}&,x\in\R\\
\ln(1+x)=&\mathop\Sigma\limits_{n=1}^\infty(-1)^{n-1}\frac{x^n}{n}&,x\in(-1,1]
\end{align}
$$

特别地，对于：
$$
(1+x)^k=1+kx+\cdots+\frac{k(k-1)\cdots(k-n+1)}{n!}x^n+\cdots
$$
当$k$为整数时，二项式展开即可，我们只看$k$不为整数时：

若$x\leqslant-1$，收敛域为$(-1,1)$；

若$x\in(-1,0)$，收敛域为$(-1,1]$；

若$x>0$，收敛域为$[-1,1]$.



## 8.Lagrange余项的Taylor展开证明不等式的简单应用

证明当$x>0$时：
$$
\ln(1+x)-(x-\frac{x^2}{2})>0
$$

### 证明

Taylor展开：
$$
\ln(1+x)=x-\frac{x^2}{2}+\frac{\xi^3}{3},\xi\in(0,x)
$$
那么：
$$
\ln(1+x)-(x-\frac{x^2}{2})=\frac{\xi^3}{3}>0
$$
证毕.



## 9.Lagrange余项的Taylor展开证明不等式的复杂应用

已知$f(x)$在$[0,1]$具有二阶导数，且满足$\abs{f(x)}\leqslant a,\abs{f''(x)}\leqslant b$，且$a,b\geqslant0$，$c$是$(0,1)$任意一点.

证明：
$$
\abs{f'(x)}\leqslant 2a+\frac{b}{2}
$$

### 证明

由在$c$处的Taylor展开：
$$
f(0)=f(c)+f'(c)(0-c)+\frac{f''(\xi_1)}{2}(0-c)^2,\xi_1\in(0,c)\\
f(1)=f(c)+f'(c)(1-c)+\frac{f''(\xi_2)}{2}(1-c)^2,\xi_2\in(c,1)
$$
作差：
$$
f(1)-f(0)=f'(c)+\frac{f''(\xi_2)}{2}(1-c)^2-\frac{f''(\xi_1)}{2}c^2
$$
即：
$$
f'(c)=f(1)-f(0)-\frac{f''(\xi_2)}{2}(1-c)^2+\frac{f''(\xi_1)}{2}c^2
$$
那么：
$$
\abs{f'(c)}\leqslant2a+\frac{b}{2}[(1-c)^2+c^2]=2a+\frac{b}{2}(1-2c+2c^2)\leqslant2a+\frac{b}{2},c\in(0,1)
$$
其中，$c\in(0,1)$具有任意性，命题得证.



## Additional

Taylor公式的奥秘无穷无尽，我们要对其有正确的认知.

在求极限时，它往往可以作为估阶的好工具，利用Taylor展开，我们可以找到一个函数的等价幂函数.

但是，绝不能认为它和等价无穷小替换有什么本质上的联系，二者是两码事.

更没有所谓的等价无穷小替换是青春版、阉割版Taylor的说法.

那纯是对数学的亵渎、无知者的自作聪明.

此外，对于所谓的$x-\sin{x},\sin{x}-\tan{x}$等形式的等价幂函数，都是需要证明的.

特别地，我们可以记住结论之后带着余项去计算，这实际上是相当于背过了Taylor结论.

但从根本上来说、对初学者来说，它不属于一个既有公式，如果直接等价属于逻辑不清、无中生有.

至此，我们了解了Taylor公式在高等数学题目中的一般结论及其常见应用.