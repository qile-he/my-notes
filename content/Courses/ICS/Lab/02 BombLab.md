
| 命令                | 作用                |
| ----------------- | ----------------- |
| `objdump -t bomb` | 显示符号表，包括函数和全局变量名称 |
| `objdump -d bomb` | 反汇编程序代码           |
| `strings bomb`    | 查找二进制文件中的可打印字符串   |

### 程序执行控制

| 命令                            | 含义                  |
| ----------------------------- | ------------------- |
| `run` / `r`                   | 启动程序                |
| `break phase_1` / `b phase_1` | 在第一关设置断点            |
| `continue` / `c`              | 继续执行，直到下一个断点        |
| `nexti` / `ni`                | 执行下一条机器指令，不进入被调用函数  |
| `stepi` / `si`                | 执行下一条机器指令，可以进入被调用函数 |
| `quit` / `q`                  | 退出 GDB              |

### 查看寄存器
```
info registers
```

可以显示寄存器状态。

如果只想看某一个寄存器：

```
p $rax
```

如果希望按十六进制显示：

```
p/x $rax
```

按十进制显示：

```
p/d $rax
```

其中 `p` 是 `print` 的缩写。

### 查看内存：x 命令
```
x/NFU ADDRESS
```

其含义是查看从指定地址开始的一段内存。

其中：

- `N`：查看多少个单位。
- `F`：以什么格式显示，例如 `x` 十六进制、`d` 十进制、`s` 字符串、`i` 指令。
- `U`：每个单位的大小，`b` 为 1 字节、`h` 为 2 字节、`w` 为 4 字节、`g` 为 8 字节。

### TUI：让 GDB 显示汇编界面
```
layout asm
```

GDB 会尝试进入文本界面模式，展示当前的汇编代码。

然后：

```
layout regs
```

就可以显示寄存器状态。

`incl`：将一个 32 位整数加 1
`jrcxz`：当 `%rcx == 0` 时跳转


```
2<=rax<=7
```

```cpp
void phase_5(string str){
	if(str.size()!= 4)
		bomb();
	int ecx= 1;
	int x= 0;
	for(int i=0;i<4;i++)){
		char edx= str(x);
		edx= edx& 7;
		int* rsi= array;
		ecx= ecx* array[rdx];
	}
	if(ecx!= 0x20d)
		bomb();
}
```


```cpp
void phase_6(){
	int* si;
	int bp= 0;
	if(bp<=5){
		rax= si[bp];
		rax--;
		if(rax>5)
			bomb();
		%r12d= %rbp+ 1;
		%ebx= %r12d;
		while(bx<- 5)
	}
}
```
