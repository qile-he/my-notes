
- Floating Point 的来源：`binary point的位置不是固定的，而是用exponent控制`

- IEEE: $V=(-1)^sM2^E$

## Float: 32 bit
```
1        8              23
s |     exp      |      frac
```

## Double: 64 bit
```
1        11                    52
s |      exp       |           frac
```

### exp 既不全 0，也不全 1
→ **normalized**

$\boxed{E=Exp-Bias}$
$\boxed{Bias=2^{k-1}-1}$     `k` 是 exponent bit 数。

$\boxed{ \text{decimal} \rightarrow \text{binary} \rightarrow 1.xxx\times2^E \rightarrow s,\ Exp,\ frac }$


### exp = 000...000
→ **denormalized / subnormal**

$\boxed{E=1-Bias}$

目的：gradual overflow

有±0之分

### exp = 111...111
→ **special**

### Infinity
```
exp  = 111...111
frac = 000...000
```
则   $\infty\, or\,-\infty$

NaN
```
exp = 111...111
frac ≠ 0
```
若`x == NaN`
那么`x == x`为`False`
```c
NaN < 1
NaN > 1
NaN == 1
```
全部为`False`
检测NaN用`isnan(x)`


**越靠近 0，浮点数越密。**
**绝对值越大，相邻浮点数距离越大。**

### 浮点运算的思想
先得到一个“数学上完全精确的答案”，然后把它舍入到最近的可表示 floating-point number。
$\boxed{x+_fy=\operatorname{Round}(x+y)}$
$\boxed{x\times_fy=\operatorname{Round}(xy)}$
## Rounding Modes
1. Toward zero
2. Round down
3. Round up
4. Round to nearest, ties to even

ties to even在统计学上更加中性
even最后保留的bit为0


## Guard/Round/Sticky

- `G`：当前结果最低保留位，课件称 Guard bit；
- `R`：第一个被删除的 bit，课件称 Round bit；
- `S`：后续所有被删 bit 的 OR：$S=X_1\lor X_2\lor\cdots$

## 浮点乘法
假设：$x=(-1)^{s_1}M_12^{E_1}\quad y=(-1)^{s_2}M_22^{E_2}$
则：$xy=(-1)^{s_1\oplus s_2} (M_1M_2) 2^{E_1+E_2}$


exp = 0xFF 的时候要么是NaN要么是Infinity

对于一个 32-bit unsigned，**移位 32 位(>>32)是未定义行为**，不能依赖它自动得到 `0`



