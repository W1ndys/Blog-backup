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

 (1) 写出按BF算法对主串S进行模式匹配的过程;

 (2) 手工计算模式串T的next值;

 (3) 写出利用求得的next数组，按KMP算法对主串S进行模式匹配的过程。

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