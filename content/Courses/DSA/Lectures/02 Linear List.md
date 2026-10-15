## 结构特征
- 第一个结点没有前驱，但有唯一的直接后继；
- 最后一个结点没有后继，但有唯一的直接前驱；
- 中间结点有唯一直接前驱，也有唯一直接后继。

## 向量

顺序表使用**定长一维数组**，元素类型相同，存储空间连续，每个元素有唯一的下标
```cpp
T* aList;
int maxSize;//总共分配了几个元素
int curLen;//目前存了多少元素
int position;
```
访问第 $i$ 个元素是 $O(1)$  random access
$Loc(k_i)=b+L\times i$

插入位置合法范围：$\boxed{0\le p\le curLen}$
已有位置合法范围：$\boxed{0\le p < curLen}$

- 读取指定位置元素：\(O(1)\)
- 插入：\(O(n)\)
- 删除：\(O(n)\)

## 链表
### 单链表
```cpp
struct ListNode {
    ELEM data;
    ListNode* next;
};
```

链表插入本身 \(O(1)\)，但“找到插入位置”可能是 \(O(n)\)

setPos(-1) = head;
```
head
 ↓
[头结点] → A → B → C → NULL
```

```cpp
d = p->next;

if (d == tail) {
    tail = p;
    p->next = NULL;
    delete d;
}
else {
    p->next = d->next;
    delete d;
}
```

### 双链表
>多保存一个指向前驱的指针

```cpp
struct DblListNode {
    T data;
    DblListNode* prev;
    DblListNode* next;
};
```

插入和删除都要注意边界条件，而且指针操作的次序也很重要


## Vector

```cpp
a.push_back(10);      // 尾部加入

a[0];                 // 访问第0个元素

a.size();             // 元素个数
a.empty();            // 是否为空
a.clear();            // 清空

a.pop_back();         // 删除最后一个
```
插入与删除
```cpp
a.insert(a.begin() + pos, x);
a.erase(a.begin() + pos);
```
边遍历边删除
```cpp
for (int i = 0; i < a.size(); ) {
    if (a[i] == 0)
        a.erase(a.begin() + i);
    else
        i++;
}
```
`poj`中的小技巧（适用于vector的删除）
```cpp
int k = 0;
for(int i=0;i<n;i++){
	if(a[i] != x){
		a[k++] = x;
	}
}
n = k; //O(n)复杂度，如果用正常的erase一个个擦除需要n的平方
```

---
## List

可以用数组来模拟
```cpp
int next[100005];
next[1] = 2;
next[2] = 3;
next[3] = 4;
next[4] = -1;

//假如想要删除3
next[2] = next[3];
```

双向链表也可以模拟
```cpp
int pre[MAXN];
int nxt[MAXN];

nxt[pre[x]]=nxt[x];
pre[nxt[x]]=pre[x];
```