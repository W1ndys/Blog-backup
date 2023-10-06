---
title: DS作业-4-Ch3-22网安物联网-20230927
tags:  数据结构
categories:  [学习笔记,数据结构作业,课后作业]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码
password: 5252why
---

# Ch3-1. 总结栈空、栈满、队空、队满的判定条件。

栈和队列是两种常见的数据结构，它们的空和满的判断条件如下：

**栈**：

- **栈空**：当栈顶指针`top`等于-1时，表示栈为空。
- **栈满**：当栈顶指针`top`等于栈的最大容量减1（假设栈的最大容量为`maxSize`）时，表示栈已满，即`top == maxSize - 1`。

**队列**：

- **队空**：当队头指针`front`等于队尾指针`rear`时，表示队列为空。
- **队满**：这个判断条件取决于你如何实现队列。如果你使用数组实现循环队列，那么当`(rear + 1) % maxSize == front`时，表示队列已满（假设队列的最大容量为`maxSize`）。这里的 `%` 是取余运算，用于实现循环。

# Ch3-2. 循环队列的优点是什么？设用数组来存放循环队列，你有几种判断队满和队空的方案？

**循环队列**的优点主要有以下几点：

1. **有效利用空间**：在普通队列中，当队尾指针到达数组的末端时，即使数组的前端还有空闲空间，也无法再添加新的元素。而循环队列通过将队列的首尾相连，形成一个循环，使得在队尾指针到达数组末端时，可以从数组前端继续添加新的元素，从而更有效地利用了空间。
2. **避免数据迁移**：在普通队列中，每次出队操作后，为了维持队列的连续性，需要将所有元素向前移动一位，这会消耗大量的时间和计算资源。而在循环队列中，通过移动队头和队尾指针来实现入队和出队操作，无需移动元素本身，因此效率更高。

对于使用数组实现的循环队列，常见的判断队满和队空的方案有以下几种：

1. **牺牲一个存储空间**：这是最常见的方法。当`(rear + 1) % maxSize == front`时，判断队列已满；当`rear == front`时，判断队列为空。这种方法的缺点是会浪费一个数组的存储空间。
2. **使用一个标志位**：除了使用`front`和`rear`两个指针外，还可以额外使用一个标志位来判断队列的状态。当入队操作后`rear == front`时，将标志位设为满；当出队操作后`rear == front`时，将标志位设为空。这种方法可以充分利用所有存储空间，但需要额外的标志位。
3. **记录元素个数**：除了使用`front`和`rear`两个指针外，还可以使用一个计数器来记录队列中元素的个数。当计数器为0时，判断队列为空；当计数器等于数组大小时，判断队列已满。这种方法同样可以充分利用所有存储空间，但需要额外的计数器。

# Ch3-3. 假设以带头结点的循环单链表表示队列，并且只设一个尾指针Node*Rear 指向队尾结点（没有队头指针Node *front），试编写入队和出队算法。

> AI生成的，不想做了，谨慎查阅

```
#include <stdio.h>
#include <stdlib.h>

// 定义结点
typedef struct Node {
    int data;
    struct Node* next;
} Node;

// 定义队列
typedef struct Queue {
    Node* rear;
} Queue;

// 初始化队列
Queue* initQueue() {
    Node* head = (Node*)malloc(sizeof(Node));  // 创建头结点
    head->next = head;  // 循环链表
    Queue* queue = (Queue*)malloc(sizeof(Queue));
    queue->rear = head;  // 尾指针指向头结点
    return queue;
}

// 入队操作
void enQueue(Queue* queue, int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = data;
    newNode->next = queue->rear->next;  // 新结点指向头结点
    queue->rear->next = newNode;  // 尾结点指向新结点
    queue->rear = newNode;  // 更新尾指针
}

// 出队操作
int deQueue(Queue* queue) {
    if (queue->rear == queue->rear->next) {
        printf("队列为空，无法出队。\n");
        return -1;
    }
    Node* head = queue->rear->next;  // 头结点
    Node* firstNode = head->next;  // 第一个结点（即要出队的结点）
    int data = firstNode->data;
    head->next = firstNode->next;  // 头结点指向第二个结点
    if (firstNode == queue->rear) {  // 如果只有一个元素，出队后更新尾指针
        queue->rear = head;
    }
    free(firstNode);  // 释放出队的结点内存
    return data;
}

int main() {
    Queue* queue = initQueue();
    

    printf("入队：\n");
    for (int i = 1; i <= 5; i++) {
        printf("%d ", i);
        enQueue(queue, i);
    }
    
    printf("\n出队：\n");
    for (int i = 1; i <= 5; i++) {
        printf("%d ", deQueue(queue));
    }
    
    return 0;

}
```

