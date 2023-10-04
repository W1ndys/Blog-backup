---
title:  DS作业-3-Ch2-22网安物联网-20230927
tags:  数据结构
categories:  [学习笔记,数据结构作业]
---

# 作业Ch2-1:总结单链表中引入头节点的原因？

为了使操作方便，加了头结点之后，无论单链表是否为空，头指针始终指向头节点，因此空表和非空表的处理也统一了

# 作业Ch2-2:编程题目，逆置一个单链表为一个新表，编制源代码并运行。

> 没用ai跑，自己写的，实际上原理就是头插法和尾插法，两个方法的顺序是相反的

```
#include <iostream>
using namespace std;

template<typename DataType>
struct Node
{
    DataType data;
    Node<DataType>* next;
};

template<typename DataType>
class linklist
{
public:
	linklist();
	linklist(DataType a[],int n);
	~linklist();
	void nizhi(DataType a[], int m);
	void display();
private:
	Node<DataType>* first;//头结点
};

template<typename DataType>
linklist<DataType>::linklist()
{
	first = new Node<DataType>;
	first->next = nullptr;//头结点指针置空
}

template <typename DataType>
linklist<DataType>::linklist(DataType a[], int n)
{
	first = new Node<DataType>;              // 生成头结点
	Node<DataType>* r = first, * s = nullptr; // 尾指针初始化
	for (int i = 0; i < n; i++)
	{
		s = new Node<DataType>;
		s->data = a[i];
		r->next = s;
		r = s; // 将结点s插入到终端结点之后
	}
	r->next = nullptr; // 单链表建立完毕，将终端结点的指针域置空
}

template<typename DataType>
void linklist<DataType>::nizhi(DataType a[], int n)
{
	first = new Node<DataType>;
	first->next = nullptr;
	for (int i = 0; i < n; i++)
	{
		Node<DataType>* s = nullptr;
		s = new Node<DataType>;
		s->data = a[i];
		s->next = first->next;
		first->next = s;
	}
}

template<typename DataType>
void linklist<DataType>::display()
{
	Node<DataType>* p = first->next;
	while (p != nullptr)
	{
		cout << p->data << "\t";
		p = p->next;
	}
}

template <class DataType>
linklist<DataType>::~linklist()
{
	Node<DataType>* q = NULL;
	while (first != NULL) // 释放单链表的每一个结点的存储空间
	{
		q = first;           // 暂存被释放结点
		first = first->next; // first指向被释放结点的下一个结点
		delete q;
	}
}

int main()
{
	int maxsize;
	cout << "请输入你要创建数组的大小" << endl;
	cin >> maxsize;
	int* a = new int[maxsize];
	for (int i = 0; i < maxsize; i++)
	{
		a[i] = i + 1;
		cout << " " << endl;
	}
	cout << "已创建一个最大长度" << maxsize << "的链表" << endl;
	linklist<int> L{ a, maxsize };
	cout << "执行遍历链表" << endl;
	L.display();
	cout << endl;
	cout << "下面逆置最大长度为" << maxsize << "的链表" << endl;
	L.nizhi(a, maxsize);
	L.display();
    return 0;
}
```



# 作业Ch2-3:教材P66, 2(1)题：请说明顺序表和单链表有何优缺点？并分析不同情况下采用何种存储结构更合适？

顺序表的优点:① 无需为表示表中元素之间的逻辑关系而增加额外的存储空间;② 可以快速地存取表中任一位置的元素(即随机存取)。

顺序表的缺点:① 插入和删除操作需移动大量元素;② 表的容量难以确定;③ 造成存储空间的“碎片”。

单链表的优点:① 不必事先知道线性表的长度;② 插入和删除元素时只需修改指针,不用移动元素。

单链表的缺点:① 指针的结构性开销;② 存取表中任意元素不方便,只能进行顺序存取。

⑴ 应选用顺序存储结构。因为顺序表是随机存取结构,单链表是顺序存取结构。本题很少进行插入和删除操作,所以空间变化不大,且需要快速存取,所以应选用顺序存储结构。

⑵ 应选用链接存储结构。链表容易实现表容量的扩充,适合表的长度动态发生变化。⑶ 应选用链接存储结构。因为一个城市的设计和规划涉及活动很多,需要经常修改、扩充和删除各种信息, 才能适应不断发展的需要。而顺序表的插入、删除的效率低,故不合适。

# 作业Ch2-4:算法设计：在顺序表中删除所有元素值为x的元素，要求空间复杂度为O(1)，给出算法伪代码和源代码。

# 作业Ch2-5:算法设计：已知单链表中各结点的元素值为整型且递增有序，设计算法删除链表中大于mink且小于maxk的所有元素，并释放被删结点的存储空间，给出算法伪代码和源代码。