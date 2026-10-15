
- 1 Byte = 8 Bits

## 十六进制

- 一个十六进制位数 = 4 Bits
- i.e.  $\texttt{0xFA} = 11111010_2$
  `F = 1111`  `A = 1010`
## 各种类型所占据的字节

| 类型        | Bytes |
| --------- | ----- |
| `char`    | 1     |
| `short`   | 2     |
| `int`     | 4     |
| `long`    | 8     |
| `float`   | 4     |
| `double`  | 8     |
| `pointer` | 8     |

## Bit-level Operation: 位运算

### AND
```c
A & B
```
1 & 1 = 1
只有两者都为`1`才为`1`

### OR
```c
A | B
```
至少有一个是`1`就是`1`

### XOR
```c
A ^ B
```
不同为 `1`：

$$0\oplus1=1,\qquad1\oplus0=1 \ $$
相同为 `0`：

$$ 0\oplus0=0,\qquad1\oplus1=0 \ $$

### NOT
```c
~A
```
逐位反转

## Bit vector 可以表示集合

交集对应AND 并集对应OR
对称差对应XOR 补集对应NOT

## 位运算 vs 逻辑运算
### 位运算
是逐bit计算
```c
0x69 & 0x55 = 0x41
```
### 逻辑运算
只在乎是不是0
```
0      → false
非0     → true
```

```c
0x69 & 0x55 = 1
```

### short-circuit
```c
p && *p
```
如果`p = NULL`
则第一项就是False，第二项就不会执行

### Shift
#### 左移
```c
x << k
```
整体向左移动k位
左边溢出的被丢掉，右边补0
直观上相当于乘一个2的次方

#### 右移有两种
##### Logical right shift
- 左边补0
##### Arithmetic right shift
- 左边复制最高位
为什么？
因为在补码中，最高位 1 表示负数。
unsigned 和 signed 的右移行为不一样，有时候需要先转换一下

## 整数表示： Unsigned 与 Two's Complement

设 $X = [x_{w-1},\dots,x_1,x_0]$
### Unsigned
$B2U(X)=\sum_{i=0}^{w-1}x_i2^i$
### 补码 Two's Complement
$B2T(X) = -x_{w-1}2^{w-1} + \sum_{i=0}^{w-2}x_i2^i$

## Signed ↔ Unsigned conversion

- 转换时 bit pattern 不变，只改变解释方式

## Casting Surprises

- 当signed 和 unsigned 混在同一个表达式里，signed 通常会转换为 unsigned

## Sign Extension: 符号扩展

- 复制sign bit

## Truncation: 截断

- 直接扔掉高位

## Unsigned Addition

- $UAdd_w(u,v) = (u+v)\mod2^w$


`sizeof`也是unsigned

# 内存模型

## Point

- pointer 存的就是 address

## Endianness: 大小端
```c
int x = 0x01234567;
```
```
四个Bytes是
01 23 45 67
假设初始地址
0x100
则big endianness
地址     100 101 102 103
内容      01  23  45  67
little endianness
地址     100 101 102 103
内容      67  45  23  01
```
x86 使用的就是 little endian


# 易错点

- `-TMin = TMin`
```
x>y 不能推出 -x<-y
```

- unsigned右移可当作除以$2^k$，signed要小心负数取整

- 判断一个正整数是不是2的幂次
```c
x > 0 && (x & (x-1)) == 0
```