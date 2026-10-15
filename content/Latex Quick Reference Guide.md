## 1. 基本公式环境

### 行内公式

```
$x^2+y^2=z^2$
```
---
### 独立公式

```
$$
x^2+y^2=z^2
$$
```
---

# 2. 上标与下标

|功能|LaTeX|效果|
|---|---|---|
|上标|`x^2`|$x^2$|
|多字符上标|`x^{100}`|$x^{100}$|
|下标|`a_1`|$a_1$|
|多字符下标|`a_{n+1}`|$a_{n+1}$|
|上下标同时使用|`a_i^2`|$a_i^2$|

建议多字符时始终使用 `{}`：

```
x^{n+1}
a_{i+1}
```

---

# 3. 分数与根号

## 分数

```
\frac{a}{b}
```

效果：

$$  
\frac{a}{b}  
$$

复杂分数：

```
\frac{x^2+1}{x-1}
```

$$  
\frac{x^2+1}{x-1}  
$$

---

## 根号

平方根：

```
\sqrt{x}
```

$$  
\sqrt{x}  
$$

$n$ 次根：

```
\sqrt[n]{x}
```

$$  
\sqrt[n]{x}  
$$

---

# 4. 基本运算符

|符号|LaTeX|
|---|---|
|$+$|`+`|
|$-$|`-`|
|$\pm$|`\pm`|
|$\times$|`\times`|
|$\div$|`\div`|
|$\cdot$|`\cdot`|
|$=$|`=`|
|$\neq$|`\neq`|
|$\approx$|`\approx`|
|$<$|`<`|
|$>$|`>`|
|$\leq$|`\leq`|
|$\geq$|`\geq`|
|$\infty$|`\infty`|

例如：

```
-\infty < x \leq +\infty
```

$$  
-\infty < x \leq +\infty  
$$

---

# 5. 箭头

|符号|LaTeX|
|---|---|
|$\to$|`\to`|
|$\rightarrow$|`\rightarrow`|
|$\leftarrow$|`\leftarrow`|
|$\leftrightarrow$|`\leftrightarrow`|
|$\Rightarrow$|`\Rightarrow`|
|$\Leftarrow$|`\Leftarrow`|
|$\Leftrightarrow$|`\Leftrightarrow`|

例如：

```
x>0 \Rightarrow x^2>0
```

$$  
x>0 \Rightarrow x^2>0  
$$

---

# 6. 希腊字母

## 小写

|LaTeX|效果|LaTeX|效果|
|---|---|---|---|
|`\alpha`|$\alpha$|`\beta`|$\beta$|
|`\gamma`|$\gamma$|`\delta`|$\delta$|
|`\epsilon`|$\epsilon$|`\varepsilon`|$\varepsilon$|
|`\theta`|$\theta$|`\lambda`|$\lambda$|
|`\mu`|$\mu$|`\pi`|$\pi$|
|`\rho`|$\rho$|`\sigma`|$\sigma$|
|`\tau`|$\tau$|`\phi`|$\phi$|
|`\psi`|$\psi$|`\omega`|$\omega$|

## 大写

|LaTeX|效果|
|---|---|
|`\Gamma`|$\Gamma$|
|`\Delta`|$\Delta$|
|`\Theta`|$\Theta$|
|`\Lambda`|$\Lambda$|
|`\Pi`|$\Pi$|
|`\Sigma`|$\Sigma$|
|`\Phi`|$\Phi$|
|`\Psi`|$\Psi$|
|`\Omega`|$\Omega$|

---

# 7. 集合符号

|含义|LaTeX|效果|
|---|---|---|
|属于|`\in`|$x\in A$|
|不属于|`\notin`|$x\notin A$|
|子集|`\subset`|$A\subset B$|
|子集或相等|`\subseteq`|$A\subseteq B$|
|真子集|`\subsetneq`|$A\subsetneq B$|
|超集|`\supset`|$A\supset B$|
|超集或相等|`\supseteq`|$A\supseteq B$|
|并集|`\cup`|$A\cup B$|
|交集|`\cap`|$A\cap B$|
|空集|`\emptyset`|$\emptyset$|
|集合差|`\setminus`|$A\setminus B$|

例如：

```
A\cap B=\emptyset
```

$$  
A\cap B=\emptyset  
$$

---

# 8. 常见数集

|数集|LaTeX|
|---|---|
|自然数 $\mathbb{N}$|`\mathbb{N}`|
|整数 $\mathbb{Z}$|`\mathbb{Z}`|
|有理数 $\mathbb{Q}$|`\mathbb{Q}`|
|实数 $\mathbb{R}$|`\mathbb{R}`|
|复数 $\mathbb{C}$|`\mathbb{C}`|

例如：

```
x\in\mathbb{R}
```

$$  
x\in\mathbb{R}  
$$

---

# 9. 逻辑符号

|含义|LaTeX|效果|
|---|---|---|
|非|`\neg`|$\neg P$|
|与|`\land`|$P\land Q$|
|或|`\lor`|$P\lor Q$|
|异或|`\oplus`|$P\oplus Q$|
|蕴含|`\Rightarrow`|$P\Rightarrow Q$|
|等价|`\Leftrightarrow`|$P\Leftrightarrow Q$|
|对所有|`\forall`|$\forall x$|
|存在|`\exists`|$\exists x$|
|不存在|`\nexists`|$\nexists x$|
|因为|`\because`|$\because$|
|所以|`\therefore`|$\therefore$|

例如：

```
\forall x\in A,\quad P(x)\Rightarrow Q(x)
```

$$  
\forall x\in A,\quad P(x)\Rightarrow Q(x)  
$$

---

# 10. 求和、乘积、极限

## 求和

```
\sum_{i=1}^{n} i
```

$$  
\sum_{i=1}^{n} i  
$$

---

## 连乘

```
\prod_{i=1}^{n} x_i
```

$$  
\prod_{i=1}^{n}x_i  
$$

---

## 极限

```
\lim_{x\to 0} f(x)
```

$$  
\lim_{x\to0}f(x)  
$$

---

# 11. 微积分

## 积分

```
\int_a^b f(x)\,dx
```

$$  
\int_a^b f(x),dx  
$$

不定积分：

```
\int f(x)\,dx
```

$$  
\int f(x),dx  
$$

---

## 导数

```
f'(x)
```

$$  
f'(x)  
$$

```
\frac{dy}{dx}
```

$$  
\frac{dy}{dx}  
$$

---

## 偏导

```
\frac{\partial f}{\partial x}
```

$$  
\frac{\partial f}{\partial x}  
$$

---

# 12. 括号

普通括号：

```
(x+y)
[x+y]
```

大括号需要转义：

```
\{x,y,z\}
```

$$  
{x,y,z}  
$$

复杂公式建议使用自动大小：

```
\left(
\frac{x+1}{x-1}
\right)
```

$$  
\left(  
\frac{x+1}{x-1}  
\right)  
$$

常见组合：

```
\left( \right)
\left[ \right]
\left\{ \right\}
```

---

# 13. 绝对值与范数

绝对值：

```
|x|
```

或：

```
\left|x\right|
```

$$  
\left|x\right|  
$$

范数：

```
\|x\|
```

$$  
|x|  
$$

更规范：

```
\left\|x\right\|
```

---

# 14. 向量、帽子、横线

|效果|LaTeX|
|---|---|
|$\vec{x}$|`\vec{x}`|
|$\hat{x}$|`\hat{x}`|
|$\bar{x}$|`\bar{x}`|
|$\tilde{x}$|`\tilde{x}`|
|$\dot{x}$|`\dot{x}`|
|$\ddot{x}$|`\ddot{x}`|

机器学习中经常看到：

```
\hat{y}
```

$$  
\hat{y}  
$$

平均值：

```
\bar{x}
```

$$  
\bar{x}  
$$

---

# 15. 粗体、花体等字体

## 粗体

```
\mathbf{x}
```

$$  
\mathbf{x}  
$$

经常用于表示向量或矩阵。

---

## 黑板粗体

```
\mathbb{R}
```

$$  
\mathbb{R}  
$$

---

## 花体

```
\mathcal{L}
```

$$  
\mathcal{L}  
$$

机器学习中经常用来表示 Loss：

```
\mathcal{L}(\theta)
```

$$  
\mathcal{L}(\theta)  
$$

---

# 16. 文本

在公式里插入普通文字：

```
\text{...}
```

例如：

```
x>0 \quad \text{if } x \text{ is positive}
```

$$  
x>0\quad \text{if }x\text{ is positive}  
$$

---

# 17. 空格

LaTeX 数学环境中，直接敲空格通常不会产生明显效果。

|LaTeX|含义|
|---|---|
|`\,`|小空格|
|`\`|普通空格|
|`\quad`|大空格|
|`\qquad`|更大空格|

例如：

```
x>0 \quad \Rightarrow \quad x^2>0
```

$$  
x>0\quad\Rightarrow\quad x^2>0  
$$

---

# 18. 矩阵

## 方括号矩阵

```
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
```

$$  
\begin{bmatrix}  
1 & 2\  
3 & 4  
\end{bmatrix}  
$$

其中：

- `&`：换列
    
- `\\`：换行
    

---

## 圆括号矩阵

```
\begin{pmatrix}
1 & 2 \\
3 & 4
\end{pmatrix}
```

$$  
\begin{pmatrix}  
1 & 2\  
3 & 4  
\end{pmatrix}  
$$

---

## 无括号矩阵

```
\begin{matrix}
1 & 2 \\
3 & 4
\end{matrix}
```

---

# 19. 分段函数

```
f(x)=
\begin{cases}
x^2, & x\geq 0\\
-x, & x<0
\end{cases}
```

$$  
f(x)=  
\begin{cases}  
x^2, & x\geq0\  
-x, & x<0  
\end{cases}  
$$

---

# 20. 多行公式对齐

```
\begin{aligned}
a &= b+c\\
  &= d+e\\
  &= f
\end{aligned}
```

$$  
\begin{aligned}  
a &= b+c\  
&= d+e\  
&= f  
\end{aligned}  
$$

`&` 表示对齐位置。

通常写成：

```
&=
```

让多个等号对齐。

---

# 21. 省略号

|效果|LaTeX|
|---|---|
|$1,2,\ldots,n$|`\ldots`|
|$1+\cdots+n$|`\cdots`|
|$\vdots$|`\vdots`|
|$\ddots$|`\ddots`|

例如：

```
1,2,\ldots,n
```

$$  
1,2,\ldots,n  
$$

---

# 22. 常见离散数学表达

## 集合

```
A=\{1,2,3\}
```

$$  
A={1,2,3}  
$$

---

## 集合描述法

```
A=\{x\in\mathbb{R}\mid x>0\}
```

$$  
A={x\in\mathbb{R}\mid x>0}  
$$

`\mid` 表示：

$$  
\mid  
$$

---

## 全称命题

```
\forall x\in A,\quad P(x)
```

$$  
\forall x\in A,\quad P(x)  
$$

---

## 存在命题

```
\exists x\in A,\quad P(x)
```

$$  
\exists x\in A,\quad P(x)  
$$

---

## 逻辑表达式

```
(P\land Q)\Rightarrow R
```

$$  
(P\land Q)\Rightarrow R  
$$

---

## 集合恒等式

```
(A\cup B)^c=A^c\cap B^c
```

$$  
(A\cup B)^c=A^c\cap B^c  
$$

---

# 23. 常见概率论符号

概率：

```
P(A)
```

条件概率：

```
P(A\mid B)
```

$$  
P(A\mid B)  
$$

期望：

```
\mathbb{E}[X]
```

$$  
\mathbb{E}[X]  
$$

方差：

```
\mathrm{Var}(X)
```

$$  
\mathrm{Var}(X)  
$$

概率分布：

```
X\sim\mathcal{N}(\mu,\sigma^2)
```

$$  
X\sim\mathcal{N}(\mu,\sigma^2)  
$$

---

# 24. 机器学习常见写法

## Loss

```
\mathcal{L}(\theta)
```

$$  
\mathcal{L}(\theta)  
$$

---

## Argmax / Argmin

```
\arg\max_x f(x)
```

$$  
\arg\max_x f(x)  
$$

```
\arg\min_\theta \mathcal{L}(\theta)
```

$$  
\arg\min_\theta \mathcal{L}(\theta)  
$$

更规范：

```
\underset{\theta}{\arg\min}\;\mathcal{L}(\theta)
```

$$  
\underset{\theta}{\arg\min};\mathcal{L}(\theta)  
$$

---

## 梯度

```
\nabla f(x)
```

$$  
\nabla f(x)  
$$

例如：

```
\theta_{t+1}
=
\theta_t-\eta\nabla_\theta\mathcal{L}(\theta_t)
```

\theta_t-\eta\nabla_\theta\mathcal{L}(\theta_t)  
$$

---

## Softmax

```
\mathrm{softmax}(x_i)
=
\frac{e^{x_i}}
{\sum_{j=1}^{n}e^{x_j}}
```

\frac{e^{x_i}}  
{\sum_{j=1}^{n}e^{x_j}}  
$$

---

# 25. 常见符号速查

```
上标          ^
下标          _

分数          \frac{}{}
根号          \sqrt{}

不等于        \neq
小于等于      \leq
大于等于      \geq
约等于        \approx
无穷          \infty

属于          \in
不属于        \notin
子集          \subset
子集或相等    \subseteq
并集          \cup
交集          \cap
空集          \emptyset

逻辑非        \neg
逻辑与        \land
逻辑或        \lor
对于所有      \forall
存在          \exists

推出          \Rightarrow
等价          \Leftrightarrow

求和          \sum
连乘          \prod
积分          \int
极限          \lim
偏导          \partial
梯度          \nabla

实数          \mathbb{R}
整数          \mathbb{Z}
自然数        \mathbb{N}
有理数        \mathbb{Q}
复数          \mathbb{C}

文字          \text{}
空格          \quad

alpha         \alpha
beta          \beta
theta         \theta
lambda        \lambda
sigma         \sigma
omega         \omega
```

---

# 26. 最常用模板

## 普通公式

```
$$

$$
```

---

## 分数

```
\frac{}{}
```

---

## 求和

```
\sum_{i=1}^{n}
```

---

## 极限

```
\lim_{x\to 0}
```

---

## 集合

```
\{x\in A\mid \}
```

---

## 矩阵

```
\begin{bmatrix}
& \\
&
\end{bmatrix}
```

---

## 分段函数

```
\begin{cases}
, & \\
, &
\end{cases}
```

---

## 多行推导

```
\begin{aligned}
&=\\
&=\\
&=
\end{aligned}
```

---

# 27. 使用规律

LaTeX 中大多数特殊数学符号都遵循：

```
\ + 英文名称
```

例如：

```
\alpha
\infty
\rightarrow
\subseteq
```

分别得到：

$$  
\alpha,\qquad  
\infty,\qquad  
\rightarrow,\qquad  
\subseteq  
$$

因此没有必要一开始全部背下来，常用符号在写笔记过程中逐渐熟悉即可。
