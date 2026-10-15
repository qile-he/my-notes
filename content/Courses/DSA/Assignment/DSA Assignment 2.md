## 1 给定⼀个带头结点的单链表 $L$，设计⼀个算法将链表中的所有元素原地逆置，要求只使用 $O(1)$ 的额外空间。
```cpp
void reverse(Node* head){
	Node* p=head->next;
	Node* temp;
	Node* front=nullptr;
	
	while (p!=nullptr) {
	    temp=p->next;
	    p->next=front;
	    front=p;
	    p=temp;
	}
	
	head->next=front;
}
```
## 2 给定⼀个不带头结点的单链表 $L$，其中 `head` 指向第⼀个数据结点，设计算法找到其中间节点。若节点数为偶数，规定返回两个中间节点中的后⼀个。要求只遍历链表⼀次。
```cpp
Node* findMiddle(Node* head){
	Node* fast=head, slow=head;
	while(fast!=nullptr && fast->next!=nullptr){
		slow=slow->next;
		fast=fast->next->next;
	}
	return slow;
}
```
## 3 给定两个无环单链表 $L1, L2$，请设计算法判断它们是否相交；若相交，找出它们的第⼀个公共节点。要求 $O(1)$ 额外空间。
```cpp
Node* findIntersection(Node* head1, Node* head2){
	Node* p=head1, q=head2;
	while(p!=q){
		p=(p==nullptr)?head2:p->next;
		q=(q==nullptr)?head1:q->next;
	}
	return p;
}
```
