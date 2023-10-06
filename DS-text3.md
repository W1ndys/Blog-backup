---
title: 实验三、栈和队列的应用
tags:  数据结构
categories:  [学习笔记,数据结构作业,实验]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码
password: 5252why

---

> 声明：仅供留档查阅，仅用作起到提示引导性作用，仅用作学习交流，切勿直接照搬

![](https://cyberdownload.anrunlu.net/FruAGRXClw43THvg6TkSyPl_4S3q)

# 代码主体

## 顺序栈SeqStack的实现：

> 自己写的

```c++
#include <iostream>
using namespace std;
const int stacksize = 100;  // 定义最大栈顶具体情况具体分析

template<typename datatype>   //定义模板类seqstack
class seqstack
{
public:
	seqstack();   //构造函数，初始化空栈
	~seqstack();	//析构函数
	void push(datatype x);	//压栈
	datatype pop();	//出栈
	datatype gettop();//取栈顶
	datatype toptop();//取栈顶下标
	int empty();	//判空操作
private:
	datatype data[stacksize];	//存放栈元素的数组
	int top;	//栈顶元素的下标
};

template<typename datatype>
datatype seqstack<datatype> ::toptop()
{
	return	top;
}

template<typename datatype>
seqstack<datatype> ::seqstack()
{
	top = -1;
}

template<typename datatype>
seqstack<typename datatype> ::~seqstack()
{

}

template<typename datatype>
void seqstack<typename datatype> ::push(datatype x)
{
	top++;
	data[top] = x;
}

template<typename datatype>
datatype seqstack<typename datatype> ::pop()
{
	datatype x;
	x = data[top];
	top--;
	return x;
}

template<typename datatype>
datatype seqstack<typename datatype> ::gettop()
{
	return data[top];
}

template<typename datatype>
int seqstack<typename datatype> ::empty()
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

int main()
{
	int ws1 = 0, ws2 = 0;
	seqstack<int> S{};//定义顺序栈变量S
	cout << "系统已压栈1,2,3" << endl;
	S.push(1);
	S.push(2);
	S.push(3);
	cout << "输入一个元素进行压栈" << endl;
	cin >> ws1;
	S.push(ws1);
	cout << "当前栈顶元素为：" << S.gettop() << endl;
	cout << "*****************" << endl;
	cout << "执行一次出栈操作" << endl;
	cout << "已释放" << S.pop() << endl;
	cout << "当前栈顶元素为：" << S.gettop() << endl;
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
	for (int i = S.toptop(); i > -1 ; i--)
	{
		cout << "已释放" << S.pop() << endl;
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

2. 链式栈LinkStack的实现：

```
struct Node {
    int data;
    Node* next;
};
class LinkStack {
    Node* top;
public:
    LinkStack(): top(NULL) {}
    void push(int x) {
        Node* newNode = new Node();
        newNode->data = x;
        newNode->next = top;
        top = newNode;
    }
    int pop() {
        if (top == NULL) {
            cout << "Stack is empty";
            return -1;
        }
        int x = top->data;
        Node* temp = top;
        top = top->next;
        delete temp;
        return x;
    }
};

```

3. 循环队列CirQueue的实现：

```
#define MAXSIZE 100
class CirQueue {
    int data[MAXSIZE];
    int front, rear;
public:
    CirQueue(): front(0), rear(0) {}
    void enqueue(int x) {
        if ((rear + 1) % MAXSIZE == front) {
            cout << "Queue is full";
            return;
        }
        rear = (rear + 1) % MAXSIZE;
        data[rear] = x;
    }
    int dequeue() {
        if (front == rear) {
            cout << "Queue is empty";
            return -1;
        }
        front = (front + 1) % MAXSIZE;
        return data[front];
    }
};

```

4. 链式队列LinkQueue的实现：

```
struct Node {
    int data;
    Node* next;
};
class LinkQueue {
    Node *front, *rear;
public:
    LinkQueue() {
        front = rear = new Node();
    }
    void enqueue(int x) {
        Node* newNode = new Node();
        newNode->data = x;
        newNode->next = NULL;
        rear->next = newNode;
        rear = newNode;
    }
    int dequeue() {
        if (front == rear) {
            cout << "Queue is empty";
            return -1;
        }
        Node* temp = front->next;
        int x = temp->data;
        front->next = temp->next;
        if (rear == temp)
            rear = front;
        delete temp;
        return x;
    }
};

```

5. 十进制转换为二至九进制之间的任一进制的算法实现：

```
void decToBase(int n, int base) {
    SeqStack S; // 假设SeqStack已经实现
    while (n > 0) {
        S.push(n % base);
        n /= base;
    }
    while (!S.isEmpty()) { // 假设isEmpty()已经实现
       cout << S.pop();
   }
}

```

