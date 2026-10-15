## 01
给定⼀个只保存 int 的栈 S ，原有基本操作如下：
`S.push(x)` ：将 x 压⼊栈中。
`S.pop()` ：将栈顶元素出栈，并返回该元素。
`S.top()` ：返回栈顶元素。
请在不增加新的容器类数据结构的前提下，对上述操作进行必要的重写，并增加：
`S.getMax()` ：返回栈中的最大元素。
要求所有操作的时间复杂度均为 O(1) 。可以在原栈中额外压入辅助整数；无需考虑栈空或栈满。请
给出各操作的伪代码，并简要说明辅助信息的含义。

```cpp
push(x):
    if S 为空:
        m = x
    else:
        m = max(x, S.top())
    S.push(x)
    S.push(m)//压入目前的最大值

pop():
    S.pop()
    x = S.top()
    S.pop()
    return x

top():
    m = S.top()
    S.pop()
    x = S.top()
    S.push(m)
    return x

getMax():
    return S.top()
```

## 02
由 n 对左右括号组成的字符串中，若从左到右扫描时任意前缀内左括号数都不少于右括号数，且最
终两者数量相等，则称为合法括号序列。
请回答长度为 2n 的合法括号序列共有多少种，并写出递推关系、初始条件以及通项公式。另列出 n
= 3 时的全部合法序列。

卡特兰数
$A_n=\sum_{i=0}^{n-1}A_iA_{n-1-i}$

$A_n=\frac{1}{n+1}\binom{2n}{n}$
$A_0=1$

n=3时
```
()()(); ()(()); ((())); (()()); (())()
```

## 03
浏览器使⽤两个栈实现“后退”和“前进”：
栈 Back 保存可后退的页面；栈 Forward 保存可前进的⻚⾯。
变量 current 表示当前页面；访问新页面时，原当前页面压⼊ Back ，并清空 Forward 。
back() （后退）：若 Back 非空，将 current 压入 Forward ，再弹出 Back 的栈顶作为新
的 current ；否则不操作。
forward() （前进）：若 Forward 非空，将 current 压入 Back ，再弹出 Forward 的栈顶
作为新的 current ；否则不操作。
请回答：

1. 仅用 push 、 pop 、 empty 描述 visit(p) 、 back() 和 forward() 。

2. 初始时 current = Home ，两个栈均为空，依次执行：

写出最后的 current ，以及两个栈中从栈底到栈顶保存的页面。

1.
```
visit(p):
	Back.push(current);
	current = p;
	while(!Forward.empty())
        Forward.pop();

back():
	if(!Back.empty()){
		Forward.push(current);
		current = Back.pop();
	}
	
forward():
	if(!Forward.empty()){
		Back.push(current);
		current = Forward.pop();
	}
```

2.
current = A
Back里只有 home，Forward里只有 C

## 04
已知栈的三个基本操作定义如下：
push(S, x) ：将元素 x 压⼊栈 S 。
pop(S) ：弹出并返回栈 S 的栈顶元素。
isEmpty(S) ：判断栈 S 是否为空。
请设计⼀种⽅法，⽤两个普通栈 S1 、 S2 实现队列的三个基本操作：
enQueue(x) ：将元素插⼊队尾。
deQueue() ：删除并返回队⾸元素。
isEmpty() ：判断队列是否为空。
要求：

1. 说明两个栈各⾃保存什么，并写出 enQueue 与 deQueue 的伪代码。

2. 分析单次操作的最坏时间复杂度。

3. 若依次执⾏以下操作序列：

enQueue(5), enQueue(8), deQueue(), enQueue(2),

enQueue(7), deQueue(), deQueue()

请写出每次 deQueue() 的返回结果，并给出操作结束后队列中从队⾸到队尾的元素。

1.
```
enQueue(x):
    push(S1, x)

deQueue():
    if isEmpty(S2):
        while !isEmpty(S1):
            push(S2, pop(S1))

    if isEmpty(S2):
        return ERROR

    return pop(S2)

isEmpty():
    return isEmpty(S1) && isEmpty(S2)
```

2.
$\text{deQueue 单次操作的最坏时间复杂度}=O(n)$

3.

|操作|S1|S2|出队结果|
|---|---|---|---|
|初始|[]|[]|—|
|enQueue(5)|[5]|[]|—|
|enQueue(8)|[5, 8]|[]|—|
|deQueue()|[]|[8]|5|
|enQueue(2)|[2]|[8]|—|
|enQueue(7)|[2, 7]|[8]|—|
|deQueue()|[2, 7]|[]|8|
|deQueue()|[]|[7]|2|

