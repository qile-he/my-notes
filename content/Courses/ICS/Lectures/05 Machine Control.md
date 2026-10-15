## Four Condition Codes
`leaq`不会修改condition code

### ZF: Zero Flag
若结果为0，则`ZF=1`
else `zf=0`

### SF: Sign Flag
运算结果按照有符号整数解释时，是不是负数。
所以 $SF = \text{结果最高位}$

### CF: Carry Flag
对于加法，如果最高位之外又产生一个进位：

```
   xxxxxxxx
 + xxxxxxxx
-----------
1 xxxxxxxx
↑
超出了当前位数
```

那么：$CF=1$
这对应 **unsigned overflow**

### OF: Overflow Flag
**signed overflow**
两个正数 + 两个正数 → 得到负数
两个负数 + 两个负数 → 得到非负数
两个异号数相减，如果结果符号与被减数不同，就发生 overflow


`cmp`: 只计算，不保留结果
根据这个“假想的减法”设置 condition codes

`test`: 也是只计算，不保存
`testq b, a --> a & b`
`testq %rax, %rax`本质上是看`%rax`是不是0/是不是负数
`test`还能起到`mask`的作用 
比如想看`%rax`最低位是不是`1`，`testq $1, %rax`

`lea`可以做算术，同时保留 condition codes

`setl %al`
`l`是`less`  `%al`是`%rax`的最低`8 bit`
若成立则为1，否则为0
`setX` 只设置目的寄存器的**最低一个字节**，其他字节不变
所以后面经常跟`movzbl %al, %eax`

$\boxed{x<y \iff SF\oplus OF=1}$

`sete  setne`  equal，看ZF

## Control Branches
#### Signed
```
g  = greater
ge = greater or equal
l  = less
le = less or equal
```
`je jge jl jle`
#### Unsigned
```
a = above
b = below
```
`ja jae jb jbe`

## Conditional Move
>条件传送 `cmov`

不发生跳转，直接根据条件选择结果
- `jg`：改变程序执行位置。
- `cmovg`：不改变程序执行位置，只决定是否赋值。

可能出现的问题

|情况|问题|
|---|---|
|两边计算都很昂贵|Bad Performance|
|某边计算可能非法|Unsafe|
|分支有副作用|Illegal|
`cmov` 适合候选结果计算简单、且提前计算不会破坏程序语义的情况。

| 寄存器    | 位数     | 对应部分          |
| ------ | ------ | ------------- |
| `%rax` | 64 bit | 完整寄存器         |
| `%eax` | 32 bit | `%rax` 低 32 位 |
| `%ax`  | 16 bit | `%rax` 低 16 位 |
| `%al`  | 8 bit  | `%rax` 低 8 位  |

`setl %al`

`movzbl %al, %eax`
- `mov`：传送数据
- `z`：zero extension，零扩展
- `b`：源操作数是 byte（8 位）
- `l`：目标操作数是 long（32 位）
在 x86-64 中，只要写入 `%eax`，CPU 就自动将 `%rax` 的高 32 位清零。

| 指令              | 会发生什么               |
| --------------- | ------------------- |
| `movb $1, %al`  | 仅修改低 8 位            |
| `movw $1, %ax`  | 仅修改低 16 位           |
| `movl $1, %eax` | 修改低 32 位，高 32 位自动清零 |
| `movq $1, %rax` | 直接写入完整 64 位         |

|后缀|英文全称|中文含义|数据宽度|
|---|---|---|---|
|`b`|byte|字节|8 bit|
|`w`|word|字|16 bit|
|`l`|long|长字|32 bit|
|`q`|quadword|四字（64 位）|64 bit|
## Loops
### do-while
```cpp
do {
    Body;
} while (Test);
```

### while
- Jump-to-Middle
```cpp
goto test;

loop:
    Body;

test:
    if (Test)
        goto loop;
```
因为执行程序时，第一步先跳过循环体，来到后面的 `test`。
- Do-While Conversion
```cpp
if (!Test)
    goto done;

loop:
    Body;

    if (Test)
        goto loop;

done:
```

| |Jump-to-Middle|Do-While Conversion|
|---|---|---|
|第一次进入|先跳到后面的 Test|在前面先检查 Test|
|循环体后面|再检查 Test|再检查 Test|
|PPT 对应优化级别|`-Og`|`-O1`|

## Switch Statement
### Jump Table
$\text{JumpTable}[x]=\text{对应代码块的地址}$
CPU 可以通过一次索引访问决定接下来执行哪部分代码。
```asm
.section .rodata
.align 8
.L4:
    .quad .L8    # x = 0
    .quad .L3    # x = 1
    .quad .L5    # x = 2
    .quad .L9    # x = 3
    .quad .L8    # x = 4
    .quad .L7    # x = 5
    .quad .L7    # x = 6
```

`jmp *.L4(,%rdi,8)`
```cpp
target = Memory[Address(L4) + 8*x];
goto target;
```
Indirect Jump（间接跳转）

Fall-Through