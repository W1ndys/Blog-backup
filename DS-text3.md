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
seqstack<datatype>::~seqstack()
{

}

template<typename datatype>
void seqstack<datatype>::push(datatype x)
{
	top++;
	data[top] = x;
}

template<typename datatype>
datatype seqstack<datatype>::pop()
{
	datatype x;
	x = data[top];
	top--;
	return x;
}

template<typename datatype>
datatype seqstack<datatype>::gettop()
{
	return data[top];
}

template<typename datatype>
int seqstack<datatype>::empty()
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

template<typename datatype>
datatype seqstack<datatype>::toptop()
{
	return	top;
}

template<typename datatype>
seqstack<datatype>::seqstack()
{
	top = -1;
}
    /*
                   _ooOoo_
                  o8888888o
                  88" . "88
                  (| -_- |)
                  O\  =  /O
               ____/`---'\____
            .'  \\|     |//  `.
            /  \\|||  :  |||//  \
           /  _||||| -:- |||||-  \
           |   | \\\  -  /// |   |
           | \_|  ''\---/''  |   |
           \  .-\__  `-`  ___/-. /
         ___`. .'  /--.--\  `. . __
      ."" '<  `.___\_<|>_/___.'  >'"".
     | | :  `- \`.;`\ _ /`;.`/ - ` : | |
     \  \ `-.   \_ __\ /__ _/   .-` /  /
======`-.____`-.___\_____/___.-`____.-'======
                   `=---='
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    佛祖保佑       永不宕机     永无BUG
*/

int main()
{
	int ws1 = 0;
	seqstack<int> S{};//定义顺序栈变量
	S.push(1);
	S.push(2);
	S.push(3); 
	cout << "系统已压栈1,2,3" << endl;
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

## 链式栈LinkStack的实现：

> 自己写的

```c++
#include <iostream>
using namespace std;

template <typename datatype>
struct node
{
    datatype data;
    node<datatype>* next;
};

template <typename datatype>
class linkstack
{
public:
    linkstack();
    ~linkstack();
    void push(datatype x);  //入栈
    datatype pop();     //出栈
    datatype gettop();  //取栈顶
    int empty();        //判空
private:
    node<datatype>* top;
};

template <typename datatype>
linkstack<datatype>::linkstack()
{
    top = nullptr;
}

template <typename datatype>
linkstack<datatype>::~linkstack()
{
    cout << "程序退出，析构函数被调用!" << endl;
    while (!empty())
    {
        cout << "出栈元素：" << pop() << endl;
    }
    cout << "程序退出链栈已清空!" << endl;
}

template <typename datatype>
datatype linkstack<datatype> ::gettop()
{
    if (top == nullptr)
        throw "下溢异常";
    else
        return top->data;
}


template <typename datatype>
void linkstack<datatype> ::push(datatype x)
{
    node<datatype>* s = nullptr;
    s = new node<datatype>;
    s->data = x; //申请结点s数据域为x
    s->next = top;
    top = s; //将结点s插在栈顶
}

template <typename datatype>
datatype linkstack<datatype> ::pop()
{
    node<datatype>* p = nullptr;
    datatype x;
    if (top == nullptr) throw "下溢";
    x = top->data; p = top; //暂存栈顶元素
    top = top->next; //将栈顶结点摘链
    delete p;
    return x;
}

template <typename datatype>
int linkstack<datatype>::empty()
{
    if (top == nullptr) return 1;
    return 0;
}

    /*
                   _ooOoo_
                  o8888888o
                  88" . "88
                  (| -_- |)
                  O\  =  /O
               ____/`---'\____
            .'  \\|     |//  `.
            /  \\|||  :  |||//  \
           /  _||||| -:- |||||-  \
           |   | \\\  -  /// |   |
           | \_|  ''\---/''  |   |
           \  .-\__  `-`  ___/-. /
         ___`. .'  /--.--\  `. . __
      ."" '<  `.___\_<|>_/___.'  >'"".
     | | :  `- \`.;`\ _ /`;.`/ - ` : | |
     \  \ `-.   \_ __\ /__ _/   .-` /  /
======`-.____`-.___\_____/___.-`____.-'======
                   `=---='
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    佛祖保佑       永不宕机     永无BUG
*/
int main()
{
    int ws1 = 0;
    linkstack<int> S{};//定义顺序栈变量S
    S.push(1);
    S.push(2);
    S.push(3);
    cout << "系统已压栈1,2,3" << endl;
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
    while (S.empty() != 1)
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

## 循环队列CirQueue的实现：

```c++
#include<iostream>
using namespace std;

const int queuesize = 100; //最大长度
template <typename datatype>
class cirqueue
{
public:
	cirqueue();
	~cirqueue();
	void enqueue(datatype x);//入队
	datatype dequeue();//出队
	datatype getqueue();//取队头
	int empty();//判空操作
private:
	datatype data[queuesize];//存放需要的数组
	int front, rear;//队头和队尾指针
};

template<typename datatype>
cirqueue<datatype>::cirqueue()
{
	rear = front = queuesize - 1;
}

template<typename datatype>
cirqueue<datatype>::~cirqueue()
{

}

template<typename datatype>
void cirqueue<datatype>::enqueue(datatype x)
{
	rear = (rear + 1) % queuesize; //队尾指针+1
	data[rear] = x;			//在队尾插入元素
}

template<typename datatype>
datatype cirqueue<datatype>::dequeue()
{
	front = (front + 1) % queuesize;
	return data[front];
}

template<typename datatype>
datatype cirqueue<datatype>::getqueue()
{
	return data[(front + 1) % queuesize];
}

template<typename datatype>
int cirqueue<datatype>::empty()
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
	cirqueue<int> S{};
	int x = 0;
	S.enqueue(1);
	S.enqueue(2);
	S.enqueue(3);
	cout << "已入队1,2,3" << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.getqueue() << endl;
	cout << "请输入一个元素进行入队" << endl;
	cin >> x;
	S.enqueue(x);
	cout << "已入队：" << x << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.getqueue() << endl;
	cout << "******执行一次出队******" << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.empty() == 1)
	{ 
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	cout << "已出队：" << S.dequeue() << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.empty() == 1)
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

template<typename datatype>
struct node
{
	datatype data;
	node<datatype>* next;
};

template<typename datatype>
class linkqueue
{
public:
	linkqueue();
	~linkqueue();
	void enqueue(datatype x);
	datatype dequeue();
	datatype getqueue();
	int empty();
private:
	node<datatype>* front, * rear;
};

template<typename datatype>
linkqueue<datatype>::linkqueue()
{
	node<datatype>* s = nullptr;
	s = new node<datatype>;//开辟空间
	s->next = nullptr;
	front = rear = s;

}

template<typename datatype>
linkqueue<datatype>::~linkqueue()
{
	node<datatype>* q = nullptr;
	while (front != nullptr)
	{
		q = front;
		front = front->next;
		delete q;
	}
}

template<typename datatype>
void linkqueue<datatype>::enqueue(datatype x)
{
	node<datatype>* s = nullptr;
	s = new node<datatype>;
	s->data = x;
	s->next = nullptr;
	rear->next = s;	//插入到队尾
	rear = s;		//移动队尾
}

template<typename datatype>
datatype linkqueue<datatype>::dequeue()
{
	datatype x;
	node<datatype>* p = nullptr;
	p = front->next;
	x = p->data;
	front->next = p->next;
	delete p;
	return x;
}

template<typename datatype>
datatype linkqueue<datatype>::getqueue()
{
	return front->next->data;
}

template<typename datatype>
int linkqueue<datatype>::empty()
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
	linkqueue<int> S = {};
	S.enqueue(1);
	S.enqueue(2);
	S.enqueue(3);
	cout << "已入队1,2,3" << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.getqueue() << endl;
	cout << "请输入一个元素进行入队" << endl;
	cin >> x;
	S.enqueue(x);
	cout << "已入队：" << x << endl;
	cout << "******取一次队头******" << endl;
	cout << "队头是：" << S.getqueue() << endl;
	cout << "******执行一次出队******" << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.empty() == 1)
	{
		cout << "队列空" << endl;
	}
	else
	{
		cout << "队列非空" << endl;
	}
	cout << "已出队：" << S.dequeue() << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "已出队：" << S.dequeue() << endl;
	cout << "*****进行一次判空*****" << endl;
	if (S.empty() == 1)
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

