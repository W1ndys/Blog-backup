---
title:  C++常用的代码模板
tags:  C++
categories: [C++,常用代码]
---

# 1.生成随机数

```c++
#include <iostream>
#include <random>
using namespace std;

int main() {
    default_random_engine generator;// 创建一个随机数生成器
    uniform_int_distribution<int> distribution(1,100);// 创建一个1到100的均匀分布
    int random_number = distribution(generator);// 生成随机数
    cout << "生成的随机数是: " << random_number << endl;// 输出随机数
    return 0;
}
```

```c++
default_random_engine generator;// 创建一个随机数生成器
```

```c++
uniform_int_distribution<int> distribution(1,100);// 创建一个1到100的均匀分布
```

```c++
int random_number = distribution(generator);// 生成随机数
```

