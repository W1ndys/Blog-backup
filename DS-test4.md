---
title: 实验四：字符串和多维数组的实现与应用
tags:  数据结构
categories:  [学习笔记,数据结构作业,实验]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码(输完按回车解开)
password: myj250
---

![](https://cyberdownload.anrunlu.net/FicVRmge8QVfGJ00XaVJaDVKtKiH)

# BF+KMP算法

```c++
#include <iostream>

#include <string.h>
#define MaxSize 1000
#define MaxLen 1000
using namespace std;

struct SeqString
{
	char ch[MaxSize];
	int len;
};

// BF算法
int BF(char S[], char T[])
{
	int i = 0, j = 0, start = 0;
	while (S[i] != '\0' && T[j] != '\0')
	{
		if (S[i] == T[j])
		{
			i++;
			j++;
		}
		else
		{
			start++;
			i = start;
			j = 0;
		}
	}
	if (T[j] == '\0')
	{
		return start + 1;
	}
	else
	{
		return 0;
	}
}

void GetNext(SeqString t, int next[])
{
	int j, k;
	j = 0;
	k = -1;
	next[0] = -1;
	while (j < t.len - 1)
	{
		if (k == -1 || t.ch[j] == t.ch[k])
		{
			j++;
			k++;
			next[j] = k;
		}
		else
			k = next[k];
	}
}

int KMP(SeqString s, SeqString t)
{
	int next[MaxLen], i = 0, j = 0;
	GetNext(t, next); // 求next值
	while (i < s.len && j < s.len)
	{
		if (j == -1 || s.ch[i] == t.ch[j])
		{
			i++;
			j++;
		}
		else
		{
			j = next[j];
		}
	}
	if (j >= t.len)
	{
		return (i - t.len); // 返回下标
	}
	else
	{
		return 0; // 不匹配
	}
}

int main()
{
	cout << "*******BF算法实验*******" << endl;
	char a[MaxLen], b[MaxLen];
	cout << "请输入主串" << endl;
	cin >> a;
	cout << "输入了" << a << endl;
	cout << "请输入子串" << endl;
	cin >> b;
	cout << "输入了" << b << endl;
	int bf = BF(a, b);
	if (bf == 0)
	{
		cout << "BF算法结果：未找到" << endl;
	}
	else
	{
		cout << "BF算法结果：位置是：" << bf << endl;
	}
	cout << "*******BF算法实验*******" << endl;
	cout << endl;
	cout << endl;
	cout << endl;
	cout << "*******KMP算法实验*******" << endl;
	SeqString s, t;
	cout << "请输入主串" << endl;
	cin >> s.ch;
	s.len = strlen(s.ch);
	cout << "输入了" << s.ch << endl;
	cout << "长度是：" << s.len << endl;
	cout << "请输入子串" << endl;
	cin >> t.ch;
	t.len = strlen(t.ch);
	cout << "输入了" << t.ch << endl;
	cout << "长度是：" << t.len << endl;
	int kmp = KMP(s, t);
	if (kmp == 0)
	{
		cout << "KMP算法结果：未找到" << endl;
	}
	else
	{
		cout << "KMP算法结果：位置是：" << kmp << endl;
	}
	cout << "*******KMP算法实验*******" << endl;
}
```

