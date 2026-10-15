## CPU Architecture
Architecture / ISA
>程序员眼中的CPU

Microarchitecture
>CPU内部怎么把这个ISA实现出来

```
ISA = 软件和硬件之间的接口
Microarchitecture = ISA 的具体硬件实现
```

```
Machine Code:
CPU 实际执行的 byte-level program

Assembly Code:
Machine Code 的文本表示
```

### PC: Program Count
>程序计数器（%rip）

保存下一条将要执行的指令的位置
%rip = “代码执行到哪里了”

### Register
>寄存器

CPU内部一些非常小、非常快的存储位置

C 里的变量名到了汇编层经常消失

### Condition Code
>条件跳转的基础

### Memory
>Byte Addressable Array

## 汇编语言实际做的事情
1. Memory ↔ Register
2. Arithmetic / logical operations
3. Transfer control


Disassembler
`objdump -d sum`

x86-64有16个整数寄存器
```
%rax
%rbx
%rcx
%rdx
%rsi
%rdi
%rsp
%rbp
%r8
%r9
%r10
%r11
%r12
%r13
%r14
%r15
```

|参数顺序|对应寄存器|
|---|---|
|第 1 个整数/指针参数|`%rdi`|
|第 2 个整数/指针参数|`%rsi`|
|第 3 个整数/指针参数|`%rdx`|
|第 4 个整数/指针参数|`%rcx`|
|第 5 个整数/指针参数|`%r8`|
|第 6 个整数/指针参数|`%r9`|
|整数/指针返回值|`%rax`|


`%eax`是 `%rax` 的：

> low-order 4 bytes

也就是低 32 位。
```
63                           32 31                0
+------------------------------+------------------+
|                              |       %eax       |
+------------------------------+------------------+
|                    %rax                         |
+-------------------------------------------------+
```

| 寄存器    | 对应的值                 |
| ------ | -------------------- |
| `%rax` | `0x123456789ABCDEF0` |
| `%eax` | `0x9ABCDEF0`         |
| `%ax`  | `0xDEF0`             |
| `%ah`  | `0xDE`               |
| `%al`  | `0xF0`               |

`movq A, B` 理解为 `B = A`搬一个64-bit数据

## 三种操作数
### Immediate
表示常数
前面加`$`
e.g.`movq $5, %rax`
--> `%rax = 5`

### Register
前面有`%`

## Memory
最简单的形式`(%rax)`    类似`*p`

`movq`不允许`memory->memory`

内存寻址
`(R)` `D(R)`

`D(Rb, Ri, S)`
$\text{Mem}[\text{Reg}[Rb] + S\times \text{Reg}[Ri] + D]$
若 $s=1$ 则 $s$ 可以省略

```
movq 地址表达式, dst
= 算地址 + 访问内存

leaq 地址表达式, dst
= 只算地址
```

`lea`
>Load Effective Address

Computing addresses without a memory reference.

所以 `leaq` 还能非常高效地计算：$x+k y$


```
addq Src, Dest
subq Src, Dest
imulq Src, Dest
```
注意：
`subq %rax, %rbx`
$rbx=rbx-rax$ 
第二个操作数是被修改的那个

```asm
cqto
idivq %rsi
```
商在`%rax`，余数在`%rdx`

#### 三种移位
```
salq Src, Dest   左移
sarq Src, Dest   算术右移
shrq Src, Dest   逻辑右移
```


```
incq Dest  Dest++
decq Dest  Dest--
negq Dest  Dest = -Dest
notq Dest  Dest = ~Dest
```

C 的临时变量并不一定真的对应机器层面一个独立存储位置
编译器可以把整个表达式合并