---
title: 实验三、栈和队列的应用
tags:  数据结构
categories:  [学习笔记,数据结构作业,实验]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码
password: 5252why

---

> 声明：仅供留档查阅，仅用作起到提示引导性作用，仅用作学习交流，切勿直接照搬

<a href="https://cyberdownload.anrunlu.net/FruAGRXClw43THvg6TkSyPl_4S3q"><img src="https://cyberdownload.anrunlu.net/FruAGRXClw43THvg6TkSyPl_4S3q" alt="pPvix0S.jpg" border="0" /></a>



# 代码主体

## 顺序栈SeqStack的实现：

> 自己写的

```c++
#include <iostream>
using namespace std;
const int StackSize = 100;  // 定义最大栈顶具体情况具体分析

template<typename DataType>   //定义模板类SeqStack
class SeqStack
{
public:
	SeqStack();   //构造函数，初始化空栈
	~SeqStack();	//析构函数
	void Push(DataType x);	//压栈
	DataType Pop();	//出栈
	DataType GetTop();//取栈顶
	DataType TopTop();//取栈顶下标
	int empty();	//判空操作
private:
	DataType data[StackSize];	//存放栈元素的数组
	int top;	//栈顶元素的下标
};

template<typename DataType>
SeqStack<DataType>::~SeqStack()
{

}

template<typename DataType>
void SeqStack<DataType>::Push(DataType x)
{
	if (top == StackSize -1 )
	{
		cout << "栈满" << endl;
	}
	else
	{
		top++;
		data[top] = x;s
	}

}

template<typename DataType>
DataType SeqStack<DataType>::Pop()
{
	if (top == -1 )
	{
		cout << "栈空" << endl;
	}
	else
	{
		DataType x;
		x = data[top];
		top--;
		return x;
	}
}

template<typename DataType>
DataType SeqStack<DataType>::GetTop()
{
	if (top == -1 )
	{
		cout << "栈空" << endl;
	}
	else
	{
		return data[top];
	}

}

template<typename DataType>
int SeqStack<DataType>::empty()
{
	if (top == -1)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

template<typename DataType>
DataType SeqStack<DataType>::TopTop()
{
	return	top;
}

template<typename DataType>
SeqStack<DataType>::SeqStack()
{
	top = -1;
}


int main()
{
	int ws1 = 0;
	SeqStack<int> S{};//定义顺序栈变量
	S.Push(1);
	S.Push(2);
	S.Push(3); 
	cout << "系统已压栈1,2,3" << endl;
	cout << "输入一个元素进行压栈" << endl;
	cin >> ws1;
	S.Push(ws1);
	cout << "当前栈顶元素为：" << S.GetTop() << endl;
	cout << "*****************" << endl;
	cout << "执行一次出栈操作" << endl;
	cout << "已释放" << S.Pop() << endl;
	cout << "当前栈顶元素为：" << S.GetTop() << endl;
	cout << "*****************" << endl;
	cout << "执行一次判空操作" << endl;
	if (S.empty() == 1)
	{
		cout << "栈空" << endl;
	}
	else
	{
		cout << "栈非空" << endl;
	}
	cout << "*****************" << endl;
	cout << "正在出所有栈" << endl;
	for (int i = S.TopTop(); i > -1 ; i--)
	{
		cout << "已释放" << S.Pop() << endl;
	}
	cout << "已释放出所有栈" << endl;
	cout << "*****************" << endl;
	cout << "执行一次判空操作" << endl;
	if (S.empty() == 1)
	{
		cout << "栈空" << endl;
	}
	else
	{
		cout << "栈非空" << endl;
	}
    return 0;
}
```

## 链式栈LinkStack的实现：

> 自己写的

```c++
#include <iostream>
using namespace std;

template <typename DataType>
struct Node
{
    DataType data;
    Node<DataType>* next;
};

template <typename DataType>
class LinkStack
{
public:
    LinkStack();
    ~LinkStack();
    void Push(DataType x);  //入栈
    DataType Pop();     //出栈
    DataType GetTop();  //取栈顶
    int Empty();        //判空
private:
    Node<DataType>* top;
};

template <typename DataType>
LinkStack<DataType>::LinkStack()
{
    top = nullptr;
}

template <typename DataType>
LinkStack<DataType>::~LinkStack()
{
    cout << "程序退出，析构函数被调用!" << endl;
    while (!Empty())
    {
        cout << "出栈元素：" << Pop() << endl;
    }
    cout << "程序退出链栈已清空!" << endl;
}

template <typename DataType>
DataType LinkStack<DataType> ::GetTop()
{
    if (top == nullptr)
        cout << "下溢异常" << endl;
    else
        return top->data;
}


template <typename DataType>
void LinkStack<DataType> ::Push(DataType x)
{
    Node<DataType>* s = nullptr;
    s = new Node<DataType>;
    s->data = x; //申请结点s数据域为x
    s->next = top;
    top = s; //将结点s插在栈顶
}

template <typename DataType>
DataType LinkStack<DataType> ::Pop()
{
    Node<DataType>* p = nullptr;
    DataType x;
    if (top == nullptr)
    {
        cout << "栈空" << endl;
    }
    else
    {
        x = top->data; p = top; //暂存栈顶元素
        top = top->next; //将栈顶结点摘链
        delete p;
        return x;
    }
}

template <typename DataType>
int LinkStack<DataType>::Empty()
{
    if (top == nullptr)
    {
        return 1;
    }
    else
    {
        return 0;
    }

}

int main()
{
    int ws1 = 0;
    LinkStack<int> S{};//定义顺序栈变量S
    S.Push(1);
    S.Push(2);
    S.Push(3);
    cout << "系统已压栈1,2,3" << endl;
    cout << "输入一个元素进行压栈" << endl;
    cin >> ws1;
    S.Push(ws1);
    cout << "当前栈顶元素为：" << S.GetTop() << endl;
    cout << "*****************" << endl;
    cout << "执行一次出栈操作" << endl;
    cout << "已释放" << S.Pop() << endl;
    cout << "当前栈顶元素为：" << S.GetTop() << endl;
    cout << "*****************" << endl;
    cout << "执行一次判空操作" << endl;
    if (S.Empty() == 1)
    {
        cout << "栈空" << endl;
    }
    else
    {
        cout << "栈非空" << endl;
    }
    cout << "*****************" << endl;
    cout << "正在出所有栈" << endl;
    while (S.Empty() != 1)
    {
        cout << "已释放" << S.Pop() << endl;
    }
    cout << "已释放出所有栈" << endl;
    cout << "*****************" << endl;
    cout << "执行一次判空操作" << endl;
    if (S.Empty() == 1)
    {
        cout << "栈空" << endl;
    }
    else
    {
        cout << "栈非空" << endl;
    }
    return 0;
}
```

## 循环队列CirQueue的实现：

```c++
#include<iostream>
using namespace std;

const int QueueSize = 100; //最大长度
template <typename DataType>
class CirQueue
{
public:
	CirQueue();
	~CirQueue();
	void EnQueue(DataType x);//入队
	DataType DeQueue();//出队
	DataType GetQueue();//取队头
	int Empty();//判空操作
private:
	DataType data[QueueSize];//存放需要的数组
	int front, rear;//队头和队尾指针
};

template<typename DataType>
CirQueue<DataType>::CirQueue()
{
	rear = front = QueueSize - 1;
}

template<typename DataType>
CirQueue<DataType>::~CirQueue()
{

}

template<typename DataType>
void CirQueue<DataType>::EnQueue(DataType x)
{
	if ((rear+1)%QueueSize==front)
	{
		cout << "队满" << endl;
	}
	else
	{
		rear = (rear + 1) % QueueSize; //队尾指针+1
		data[rear] = x;			//在队尾插入元素
	}
}

template<typename DataType>
DataType CirQueue<DataType>::DeQueue()
{
	if ((rear + 1)%QueueSize==front )
	{
		cout << "队空" << endl;
	}
	else
	{
		front = (front + 1) % QueueSize;
		return data[front];
	}
}

template<typename DataType>
DataType CirQueue<DataType>::GetQueue()
{
	if (front == rear)
	{
		cout << "队空" << endl;
	}
	else
	{
		return data[(front + 1) % QueueSize];
	}
	
}

template<typename DataType>
int CirQueue<DataType>::Empty()
{
	if (front == rear)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int main()
{
	CirQueue<int> S{};
	int x = 0;
	S.EnQueue(1);
	S.EnQueue(2);
	S.EnQueue(3);
	cout << "已入队1,2,3" << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.GetQueue() << endl;
	cout << "请输入一个元素进行入队" << endl;
	cin >> x;
	S.EnQueue(x);
	cout << "已入队：" << x << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.GetQueue() << endl;
	cout << "******执行一次出队******" << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.Empty() == 1)
	{ 
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.Empty() == 1)
	{
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	return 0;
}
```

## 链式队列LinkQueue的实现：

```c++
#include<iostream>
using namespace std;

template<typename DataType>
struct node
{
	DataType data;
	node<DataType>* next;
};

template<typename DataType>
class LinkQueue
{
public:
	LinkQueue();
	~LinkQueue();
	void enQueue(DataType x);
	DataType DeQueue();
	DataType GetQueue();
	int Empty();
private:
	node<DataType>* front, * rear;
};

template<typename DataType>
LinkQueue<DataType>::LinkQueue()
{
	node<DataType>* s = nullptr;
	s = new node<DataType>;//开辟空间
	s->next = nullptr;
	front = rear = s;

}

template<typename DataType>
LinkQueue<DataType>::~LinkQueue()
{
	node<DataType>* q = nullptr;
	while (front != nullptr)
	{
		q = front;
		front = front->next;
		delete q;
	}
}

template<typename DataType>
void LinkQueue<DataType>::enQueue(DataType x)
{
	node<DataType>* s = nullptr;
	s = new node<DataType>;
	s->data = x;
	s->next = nullptr;
	rear->next = s;	//插入到队尾
	rear = s;		//移动队尾
}

template<typename DataType>
DataType LinkQueue<DataType>::DeQueue()
{
	DataType x;
	node<DataType>* p = nullptr;
	if (reat==front )
	{
		cout << "队空" << endl;
	}
	else
	{
		p = front->next;
		x = p->data;
		front->next = p->next;
		delete p;
		return x;
	}
}

template<typename DataType>
DataType LinkQueue<DataType>::GetQueue()
{
	if (front == rear)
	{
		cout << "队空" << endl;
	}
	else
	{
		return front->next->data;
	}
}

template<typename DataType>
int LinkQueue<DataType>::Empty()
{
	if (front == rear )
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int main()
{
	int x;
	LinkQueue<int> S = {};
	S.enQueue(1);
	S.enQueue(2);
	S.enQueue(3);
	cout << "已入队1,2,3" << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.GetQueue() << endl;
	cout << "请输入一个元素进行入队" << endl;
	cin >> x;
	S.enQueue(x);
	cout << "已入队：" << x << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.GetQueue() << endl;
	cout << "******执行一次出队******" << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.Empty() == 1)
	{
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "已出队：" << S.DeQueue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.Empty() == 1)
	{
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	return 0;
}
```

5. 十进制转换为二至九进制之间的任一进制的算法实现：

```
我跑路了
```

