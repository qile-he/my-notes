## Array Allocation
## Array Access
>数组与指针

即数组名 `A` 在许多表达式中可以作为指向第一个元素的指针使用

|表达式|类型|结果|
|---|---|---|
|`val`|`int*`（退化后）|`0x1000`|
|`val + 1`|`int*`|`0x1004`|
|`&val[2]`|`int*`|`0x1008`|
|`*(val + 1)`|`int`|`5`|
|`val[4]`|`int`|`3`|
指针加一，不一定是地址加一
$p+i\Longrightarrow \operatorname{Address}(p)+i\operatorname{sizeof}(*p)$

| |`int` 数组|`long` 数组|
|---|---|---|
|元素字节数|4|8|
|地址缩放因子|4|8|
|读取指令|`movl`|`movq`|
|返回寄存器|`%eax`|`%rax`|

## Multidimensional Arrays：多维数组
二维数组在内存中并不是一个二维空间，而是一段连续的一维内存。
C 语言使用 Row-Major Ordering（行优先存储）


## Structures & Alignment

### 内存对齐
对于需要 $K$ 字节对齐的数据，其起始地址必须是 $K$ 的整数倍

| 类型       | 对齐要求 | 地址需要是几的倍数 |
| -------- | ---- | --------- |
| `char`   | 1    | 1         |
| `short`  | 2    | 2         |
| `int`    | 4    | 4         |
| `float`  | 4    | 4         |
| `long`   | 8    | 8         |
| `double` | 8    | 8         |
| 指针       | 8    | 8         |
如果不满足对齐要求，要先插入`Padding`（`Internal Padding`)

**结构体自身的大小是其对齐要求的整数倍**（`Tail Padding`）
通常情况下，结构体的对齐要求由成员中最大的对齐要求决定

## Floating Point
### XMM Register
XMM寄存器有128bits，也就是16个字节

### Scalar 与 SIMD
Scalar: 标量运算
`addss %xmm0, %xmm1`
含义是：
将 `%xmm0` 低 32 位的 `float` 与 `%xmm1` 低 32 位的 `float` 相加，结果写入 `%xmm1` 的低 32 位
`ss`：Scalar Single-Precision，单精度标量
`sd`：Scalar Double-Precision

SIMD：单指令，多数据
Single Instruction, Multiple Data
`addps %xmm0, %xmm1`
`ps`：表示Packed Single-Precision
它会将 XMM 寄存器中的四个 `float` 分别相加

| 后缀   | 含义            | 操作范围      |
| ---- | ------------- | --------- |
| `ss` | Scalar Single | 一个 float  |
| `sd` | Scalar Double | 一个 double |
| `ps` | Packed Single | 四个 float  |
| `pd` | Packed Double | 两个 double |
浮点函数的返回值由 `%xmm0` 传递

浮点数比较使用`ucomiss`和`ucomisd

|比较结果|ZF|PF|CF|
|---|---|---|---|
|大于|0|0|0|
|小于|0|0|1|
|等于|1|0|0|
|Unordered|1|1|1|
PF: Parity Flag
Unordered：至少一个比较操作数是 NaN
对于浮点比较，`ZF=1` 不一定表示两个数相等，也可能表示 Unordered

```asm
ucomisd %xmm1, %xmm0
jp .L_nan
```

```asm
cvtsi2sd
```
Signed Integer → Double
## Understanding Pointers & Arrays
```cpp
int A1[3];
int *A2[3];//指针数组
int (*A3)[3];//数组指针
int (*A4[3]);
```
`[]`的优先级比`*`高

`int (*C[4])[5];`
- `C[4]`：C 是一个长度为 4 的数组。
- `*C[4]`：数组中每个元素都是指针。
- `(*C[4])[5]`：这些指针分别指向一个含有 5 个元素的数组。
- 最后 `int`：数组里的元素是整数。

x86-64 的寻址比例因子只能是 1、2、4、8
错误：`leaq 24(%rdi,%rsi,24), %rax`❌
正确答案：
```
leaq (%rsi,%rsi,2), %rax
leaq 16(%rdi,%rax,8), %rax
```

指针加一的步长，取决于它所指向对象的大小，而不是指针自身的大小

```cpp
int A[5][7];
int (*p)[7] = A;
int *q = A[2];
```
- `A`：整个二维数组。
- `*p`：包含 7 个整数的一行数组。
- `*q`：一个整数。
