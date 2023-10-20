---
title: DS作业-5-22网安物联网-20231016
tags:  数据结构
categories:  [学习笔记,数据结构作业,课后作业]
message: 作业答案被加密了，快暴揍W1ndys让他说出密码(输完按回车解开)
password: myj250

---

还没写，别看了

---

**作业ch4-1：**

设目标主串为S=“abcaabbcaaabababaabca”，模式串为T=“babab”

 (1) 写出按BF算法对主串S进行模式匹配的过程

1. 从主串S的第一个字符’a’开始，与模式串T的第一个字符’b’进行比较，发现不相等。

2. 从主串S的第二个字符’b’开始，与模式串T进行比较，发现前三个字符’b’, ‘a’, 'b’相等，但第四个字符’a’与模式串T的第四个字符’b’不相等。

3. 从主串S的第三个字符’c’开始，与模式串T进行比较，发现第一个字符不相等。

4. 以此类推，直到从主串S的第12个字符’b’开始，与模式串T进行比较，发现五个字符’b’, ‘a’, ‘b’, ‘a’, 'b’全部相等，说明找到了一个匹配。

   所以位置是12

 (2) 手工计算模式串T的next值;

| j       | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | 12   | 13   | 14   | 15   | 16   | 17   | 18   | 19   | 20   |
| ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| T[j]    | a    | b    | c    | a    | a    | b    | b    | c    | a    | a    | a    | b    | a    | b    | a    | b    | a    | a    | b    | c    | a    |
| next[j] | -1   | 0    | 0    | 0    | 1    | 1    | 2    | 0    | 0    | 1    | 1    | 1    | 2    | 1    | 2    | 1    | 2    | 1    | 1    | 2    | 0    |

 (3) 写出利用求得的next数组，按KMP算法对主串S进行模式匹配的过程。

1. S[0]与T[0]不匹配，移动模式串到S[1]。
2. S[1]与T[0]不匹配，移动模式串到S[2]。
3. 

<br/>

附：BF算法全套代码

```C++
#include <iostream>
#include <string.h>
#define MaxLen 1000
using namespace std;

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
}
```

**作业ch4-2：**

若两个M×N的矩阵A和B都是利用三元组顺序表压缩存储，若要得到同样采用三元组顺序表压缩存储的矩阵C，C＝A＋B（对应元素相加），请写出算法。

   Status AddSMatrix(TSMatrix &C, TSMatrix A, TSMatrix B)

**作业ch4-3：**

若将n×n的右上半三角矩阵Aij压缩存储为一维数组Sk，请写出二维下标i,j与一维下标k的对应关系。

**作业ch4-4：**

假设按行序为主序的存储方式存储整数数组A9×3×5×8，第一个元素的字节地址为100，每个元素占两个字节，问下列元素的地址是什么？

​    (1)A0000  (2)A1111  (3)A3125    (4)A8247

**作业ch4-5：**

求下列广义表操作的结果。

   (1)GetHead((p,h,w))    

   (2)GetTail((p,h,w))

   (3)GetHead(((a,b),(c,d))) 

   (4)GetTail(((a,b),(c,d)))

   (5)GetHead(GetTail(((a,b),(c,d))))

   (6)GetTail(GetHead(GetTail(((a,b),(c,d)))))