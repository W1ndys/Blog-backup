---
title: 实验三、栈和队列的应用
tags:  数据结构
categories:  [学习笔记,数据结构作业,实验]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码
password: 5252why
---

![](https://cyberdownload.anrunlu.net/FruAGRXClw43THvg6TkSyPl_4S3q)

# 代码主体

> 数据来自bing ai

这是一个很好的练习，可以帮助你更好地理解栈和队列的数据结构。以下是一些基本的C++实现，你可以参考：

1. 顺序栈SeqStack的实现：

```
#define MAXSIZE 100
class SeqStack {
    int data[MAXSIZE];
    int top;
public:
    SeqStack(): top(-1) {}
    void push(int x) {
        if (top == MAXSIZE - 1) {
            cout << "Stack is full";
            return;
        }
        data[++top] = x;
    }
    int pop() {
        if (top == -1) {
            cout << "Stack is empty";
            return -1;
        }
        return data[top--];
    }
};

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

