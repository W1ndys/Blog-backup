---
title:  DS作业-3-Ch2-22网安物联网-20230927
tags:  数据结构
categories:  [学习笔记,数据结构作业]
---

# 作业Ch2-1:总结单链表中引入头节点的原因？

为了使操作方便，加了头结点之后，无论单链表是否为空，头指针始终指向头节点，因此空表和非空表的处理也统一了

# 作业Ch2-2:编程题目，逆置一个单链表为一个新表，编制源代码并运行。

> 没用ai跑，自己写的，实际上原理就是头插法和尾插法，两个方法的顺序是相反的

```C++
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

## 伪代码

### 法一

```
输入：顺序表data，元素x
输出：删除所有值为x的元素后的顺序表

1. 初始化一个新的索引j为0
2. 对于顺序表data中的每个元素，执行以下操作：
   1. 如果当前元素不等于x，则将当前元素复制到j位置，并将j增加1
3. 将顺序表data的长度设置为j
```

### 法二

```
输入：顺序表data，元素x
输出：删除所有值为x的元素后的顺序表

1. 对于顺序表data中的每个元素，执行以下操作：
   1. 如果当前元素等于x，则执行以下操作：
      1. 对于从当前元素到倒数第二个元素的每个元素，将下一个元素复制到当前位置
      2. 将顺序表data的长度减1
      3. 将当前索引减1（因为删除了元素）
```

## 源代码

```C++
#include <iostream>
#include <random>
#include <chrono>

using namespace std;

const int MaxSize = 100;            //100只是示例性的数据，根据实际问题具体定义

template <class DataType>          //定义模板类SeqList
class SeqList
{
public:
    SeqList();                     //无参构造函数，建立空的顺序表
    SeqList(DataType a[], int n);      //有参构造函数，建立长度为n的顺序表
    ~SeqList();                    //析构函数
    DataType Delete(int i);            //删除操作，删除第i个元素
    void PrintList();                 //遍历操作，按序号依次输出各元素
private:
    DataType data[MaxSize];          //存放数据元素的数组
    int length;                       //线性表的长度
};

template <class DataType>
DataType SeqList<DataType> ::Delete(int x)
{   /*这段代码遍历顺序表，每次遇到值不等于x的元素时，就将其复制到新的位置。最后，它将顺序表的长度设置为新的长度。这个算法的空间复杂度是O(1)，因为它只使用了固定数量的额外空间。*/
    int j = 0;
    for (int i = 0; i < length; i++)
    {
        if (data[i] != x)
        {
            data[j] = data[i];
            j++;
        }
        
    }
    length = j;
    return x;
    /*
    这个有两种做法，还有一种是直接删除。每次遇到值为x的元素时，就将其删除。但是，这种方法的时间复杂度是O(n^2)，因为每次删除操作都需要O(n)的时间。
    for (int i = 0; i < length; i++)
    {
        if (data[i] == x)
        {
            for (int j = i; j < length - 1; j++)
            {
                data[j] = data[j + 1];
            }
            length--;
            i--;  // 因为删除了元素，所以需要将索引减1
        }
    }*/
}

template<class DataType>
SeqList<DataType> :: ~SeqList()
{

}

template <class DataType>
SeqList<DataType> ::SeqList()
{
    length = 0;
}

template <class DataType>
SeqList<DataType> ::SeqList(DataType a[], int n)
{
    if (n > MaxSize)
        throw "参数非法";
    for (int i = 0; i < n; i++)
        data[i] = a[i];
    length = n;
}

template <class DataType>
void SeqList<DataType> ::PrintList()
{
    for (int i = 0; i < length; i++)
        cout << data[i]<<" ";                   //依次输出线性表的元素值
}

int main()
{
    // 使用当前时间作为随机数生成器的种子
    unsigned seed = chrono::system_clock::now().time_since_epoch().count();
    // 创建一个随机数生成器
    default_random_engine generator(seed);
    // 创建一个均匀分布的随机数生成器，范围从1到100
    uniform_int_distribution<int> distribution(1, 10);
    int maxsize;
    cout << "请输入你要创建表的大小" << endl;
    cin >> maxsize;
    int* a = new int[maxsize];
    for (int i = 0; i < maxsize; i++)
    {
        a[i] = distribution(generator);//赋值
    }
    cout << "已创建一个最大长度" << maxsize << "的顺序表" << endl;
    SeqList<int> L{ a, maxsize };
    cout << "*******执行遍历链表******" << endl;
    L.PrintList();
    cout << endl;
    cout << "**************************" << endl;
    cout << "请输入你要删除的数据" << endl;
    int del;
    cin >> del;
    cout << "删除的数据是" << L.Delete(del) << endl;
    cout << "*******执行遍历链表******" << endl;
    L.PrintList();
    cout << endl;
    cout << "**************************" << endl;
    return 0;
}
```



# 作业Ch2-5:算法设计：已知单链表中各结点的元素值为整型且递增有序，设计算法删除链表中大于mink且小于maxk的所有元素，并释放被删结点的存储空间，给出算法伪代码和源代码。

> 还没写