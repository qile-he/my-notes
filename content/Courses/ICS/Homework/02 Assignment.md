
## 2.59
### Q：编写一个`C`表达式，它生成一个字，就由`x`的最低有效字节和`y`中剩下的字节组成。对于运算数`x=0x89ABCDEF`和`y=0x76543210`，就得到`0x765432EF`
### 答:
```c
(x&0xFF)|(y&~0xFF)
```

## 2.60

### Q：假设将一个 `w` 位字中的字节从 `0`（最低有效字节）到 `w/8 - 1`（最高有效字节）编号。编写函数 `replace_byte`，将无符号整数 `x` 的第 `i` 个字节替换为字节 `b`，并返回替换后的无符号整数

### 答：
```c
unsigned replace_byte(unsigned x, int i, unsigned char b){
	unsigned mask = ~(0xFFu<<(i<<3));
	return (x&mask)|((unsigned)b<<(i<<3));
}
```

## 2.71

### 答：

### A：没有考虑符号扩展，当遇到最高位为`1`的字节时，结果会错误翻译成正数
### B：

```c
int xbyte(packed_t word, int bytenum){
	return (int)(word<<((3-bytenum)<<3))>>24;
}
```