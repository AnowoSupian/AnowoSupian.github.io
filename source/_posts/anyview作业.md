---
title: anyview作业
date: 2025-09-04 14:47:24
tags: anyview
---
### 2025/9/11 实验课作业要求

>63:

```cpp

#include "allinclude.h"  //DO NOT edit this line

LinkList MakeNode(ElemType x) { 
    // Add your code here
    LinkList F = (LinkList)malloc(sizeof(LNode));

    if(F == NULL) return NULL;

    F->data = x;
    F->next = NULL;
    return F;
}

LinkList CreateLinkList(ElemType x, ElemType y) { 
    // Add your code here
    LinkList F1 = MakeNode(x),
             F2 = MakeNode(y);
    
    if(F1 == NULL || F2 == NULL) return NULL;
    
    F1->next = F2;

    return F1; // This is a temporary code. Change it if necessary.
}

```

>65:

```cpp

#include "allinclude.h"  //DO NOT edit this line

LinkList MakeNode(ElemType x) { 
    // Add your code here
    LinkList F = (LinkList)malloc(sizeof(LNode));

    if(F == NULL) return NULL;

    F->data = x;
    F->next = NULL;
    return F;
}

LinkList CreateOrdLList(ElemType x, ElemType y) { 
    // Add your code here
    int tempMax = (x > y) ? x : y,
        tempMin = (x < y) ? x : y;

    LinkList F1 = MakeNode(tempMin),
             F2 = MakeNode(tempMax);

    if(F1 == NULL || F2 == NULL) return NULL;

    F1->next = F2;

    return F1;

}

```


### DC01PE03e

```cpp
#include "allinclude.h"  //DO NOT edit this line
int main()
{
	int a, b;

	//第1种交换a和b的值的方法：借助第三方变量
	printf("第1种交换a和b的值的方法：\n", a, b);
	a = 8;
	b = 10;
	printf("交换前：a = %d, b = %d\n", a, b);

	int c = b;
	b = a;
	a = c;
	printf("交换后：a = %d, b = %d\n\n", a, b);

	//第2种交换a和b的值的方法：算术运算（1）
	printf("第2种交换a和b的值的方法：\n", a, b);
	a = 8;
	b = 10;
	printf("交换前：a = %d, b = %d\n", a, b);

	a = b - a;
	b = b - a;
	a = a + b;
	printf("交换后：a = %d, b = %d\n\n", a, b);

	//第3种交换a和b的值的方法：算术运算（2）
	printf("第3种交换a和b的值的方法：\n", a, b);
	a = 8;
	b = 10;
	printf("交换前：a = %d, b = %d\n", a, b);

	a = a + b;
	b = a - b;
	a = a - b;
	printf("交换后：a = %d, b = %d\n\n", a, b);

	//第4种交换a和b的值的方法：异或运算
	printf("第4种交换a和b的值的方法：\n", a, b);
	a = 8;
	b = 10;
	printf("交换前：a = %d, b = %d\n", a, b);

	a = a ^ b;
	b = a ^ b;
	a = a ^ b;
	printf("交换后：a = %d, b = %d\n", a, b);

	//第5种交换a和b的值的方法：隐式赋值
	printf("第5种交换a和b的值的方法：\n", a, b);
	a = 8;
	b = 10;

	b = (a + b) - (a = b);
	printf("交换后：a = %d, b = %d\n", a, b);

	return 0;
}
```

### DC01PE06

```cpp
#include "allinclude.h"
void Descend(int &a, int &b, int &c)
{
    if (a < b) {
        int temp = a;
        a = b;
        b = temp;
    }
    if (a < c) {
        int temp = a;
        a = c;
        c = temp;
    }
    if (b < c) {
        int temp = b;
        b = c;
        c = temp;
    }
}

```

### DC01PE08

```cpp

#include "allinclude.h"  //DO NOT edit this line
float Polynomial(int n, int a[], float x0) 
{   // Add your code here
    float ans = 0.0;
    for (int i = 0; i <= n; i++) {
        ans += a[i] * pow(x0,i);
    }
    return ans;
}

```
### DC01PE11
```cpp

#include "allinclude.h"  //DO NOT edit this line
Status Fibonacci(int k, int m, int &f) { 
    // Add your code here
    int F[500010];
    if(k < 2 || m < 0) return ERROR;

    for (int i = 0; i <= m; i++) F[i] = 0;

    // if(k > m)
    // return ERROR;

    F[k-1] = 1;

    for (int i = k; i <= m; i++) {
        for (int j = i-k; j < i; j++) {
            F[i] += F[j];
        }
    }

    f = F[m];

    return OK;
}

```
### DC01PE49
```cpp

#include "allinclude.h"  //DO NOT edit this line
Status CreateSequence(Sequence &S, int n, ElemType *a) { 
   // Add your code here
   if (n <= 0) return ERROR;

   S.length = n;

   S.elem =  (ElemType*)malloc(n * sizeof(ElemType));

   if(!S.elem) return ERROR;

   for (int i = 0; i < n; i++) {
      S.elem[i] = a[i];
   }

   return OK;
}

```

### DC01PE61

```cpp

#include "allinclude.h"  //DO NOT edit this line
LinkList MakeNode(ElemType x) { 
    // Add your code here
    LinkList F = (LinkList)malloc(sizeof(LNode));
    if(F == NULL) return NULL;

    F->data = x;
    F->next = NULL;
    return F;
}

```

### DC01PE63

```cpp

#include "allinclude.h"  //DO NOT edit this line
LinkList CreateLinkList(ElemType x, ElemType y) { 
    // Add your code here
    LinkList F1 = (LinkList)malloc(sizeof(LNode)),
             F2 = (LinkList)malloc(sizeof(LNode));
    if(F1 == NULL || F2 == NULL) return NULL;

    F1->data = x;
    F2->data = y;
    F1->next = F2;
    F2->next = NULL;

    return F1; // This is a temporary code. Change it if necessary.
}

```

### DC01PE65

```cpp

#include "allinclude.h"  //DO NOT edit this line
LinkList CreateOrdLList(ElemType x, ElemType y) { 
    // Add your code here
    LinkList F1 = (LinkList)malloc(sizeof(LNode)),
             F2 = (LinkList)malloc(sizeof(LNode));
    if(F1 == NULL || F2 == NULL) return NULL;
    int temp = (x < y) ? x : y;
    F1->data = temp;

        temp = (x > y) ? x : y;
    F2->data = temp;

    F1->next = F2;
    F2->next = NULL;

    return F1;

}

```

### DC02PE03

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_Sq(SqStack S) { 
    // Add your code here
    return S.top == 0 ? TRUE : FALSE;
}

```

### DC02PE05
```cpp

#include "allinclude.h"  //DO NOT edit this line
Status GetTop_Sq(SqStack S, ElemType &e) 
{// Add your code here
    if (S.top == 0) return ERROR;
    e = S.elem[S.top - 1];
    return OK;
}

```

### DC02PE07
```cpp

#include "allinclude.h"  //DO NOT edit this line
Status Pop_Sq(SqStack &S, ElemType &e) { 
    // Add your code here
    if (S.top == 0) return ERROR;
    e = S.elem[-- S.top];
    return OK;
} 

```

### DC02PE11

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status InitStack_Sq2(SqStack2 &S, int size, int inc) { 
    // Add your code here
    if (size <= 0 || inc <= 0) return ERROR;   //如果长度和加长不满足要求，报错
    
    S.elem = (ElemType*)malloc(size * sizeof(ElemType));
    if (S.elem == NULL) return ERROR;

    S.size = size;      //构建栈长
    S.increment = inc;  //构建加长
    S.top = S.elem;     //top指向初始elem位置
}
/*
typedef struct {
    ElemType *data;     // 存储数据的数组
    int capacity;       // 数组容量
    int top;            // 栈顶索引
    // 可选的函数指针，用于自定义扩容策略
    int (*grow_policy)(int current_capacity);
} SqStackDynamic;
Status InitStack_Sq2(SqStack2 &S, int size, int inc) { 
    // 检查参数有效性
    if (size <= 0 || inc <= 0) return ERROR;
    
    // 分配存储空间
    S.data = (ElemType*)malloc(size * sizeof(ElemType));
    if (S.data == NULL) return ERROR;
    
    // 初始化栈属性
    S.capacity = size;      // 设置初始容量
    S.top = -1;             // 栈顶索引初始化为-1，表示空栈
    
    // 设置默认扩容策略（容量翻倍）
    S.grow_policy = [](int current_capacity) {
        return current_capacity * 2;
    };
    
    return OK;  // 返回成功状态
}
*/

```

### DC02PE13

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_Sq2(SqStack2 S) { 
    // Add your code here
    return (S.top == S.elem) ? TRUE : FALSE; //判断栈顶指针是否等于栈底指针
}

```

### DC02PE15

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status Push_Sq2(SqStack2 &S, ElemType e) { 
    // Add your code here
    if (S.top - S.elem >= S.size) {
        ElemType *newElem = (ElemType*)realloc(S.elem, (S.size + S.increment) * sizeof(ElemType));
        
        if (!newElem) return ERROR; 
        
        S.elem = newElem;
        S.top = S.elem + S.size; //栈顶指针更新
        S.size += S.increment;
    } //扩容

    

    *S.top = e; //入栈
    S.top ++;
}

```

### DC02PE17

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status Pop_Sq2(SqStack2 &S, ElemType &e) { 
    // Add your code here
    if(S.top == S.elem) return ERROR;   //判断空栈

    e = *(--S.top);  //取栈元素 顺便出栈咯

    return OK;
}

```

### DC02PE23

```cpp

#include "allinclude.h"  //DO NOT edit this line
int QueueLength_Sq(SqQueue Q) { 
    // Add your code here
    return (Q.rear - Q.front + Q.maxSize) % Q.maxSize;
}

```

### DC02PE25

```cpp
#include "allinclude.h"  //DO NOT edit this line
Status EnCQueue(CTagQueue &Q, ElemType x) { 
    // Add your code here
    if(Q.front == Q.rear && Q.tag == 1) return ERROR;  //当Q.f = Q.r时，并且tag为1时，是满队列状态

    Q.elem[Q.rear] = x;
    Q.rear = (Q.rear + 1) % MAXQSIZE;

    if(Q.front == Q.rear) //入队成功还等了 那就是满了
    Q.tag = 1;
    else Q.tag = 0;

    return OK;
}

Status DeCQueue(CTagQueue &Q, ElemType &x){
   // Add your code here
   if(Q.front == Q.rear && Q.tag == 0) return ERROR;  //当Q.f = Q.r时，并且tag为1时，是满队列状态

    x = Q.elem[Q.front]; //取出队头
    Q.front = (Q.front + 1) % MAXQSIZE;

    if(Q.front == Q.rear) //出队成功还等了 那就是空了
    Q.tag = 0;
    else Q.tag = 1;

    return OK;
}

```

### DC02PE27
```cpp

#include "allinclude.h"  //DO NOT edit this line

Status EnCQueue(CLenQueue &Q, ElemType x) { 
    // Add your code here
    if(Q.length == MAXQSIZE)   //满队
    return ERROR;

    Q.rear = (Q.rear + 1) % MAXQSIZE;
    Q.elem[Q.rear] = x;
    Q.length++;
    //常规入队操作

    return OK;

}

Status DeCQueue(CLenQueue &Q, ElemType &x){
    // Add your code here
    if(Q.length == 0)   //空队
    return ERROR;

    int front = (Q.rear - Q.length + 1 + MAXQSIZE) % MAXQSIZE;

    x = Q.elem[front]; 
    Q.length--; 
    //常规出队操作

    return OK;
}  

```

### DC02PE45

```cpp

#include "allinclude.h"  //DO NOT edit this line
void Union(SqList &La, List Lb)
{   
    // Add your code here
    int n = ListLength_Sq(Lb);
    for (int i = 1; i <= n; i++) {
        ElemType e;
        GetElem_Sq(Lb, i, e);
        if (Search_Sq(La, e) == -1) {
            Append_Sq(La, e);
        }
    }
    //O(N^2)
}

```
### DS02ES30 Main.cpp
```cpp

#include <stdio.h>
#include "SqList.h"

void printSqList(SqList L) {
    int i = 0;
    for (i = 0; i < L.length - 1; i++) 
    {
        printf("%d, ", L.elem[i]);
    }
    printf("%d}", L.elem[i]);
    printf("\n");
}

void MergeList_Sq(SqList La, SqList Lb, SqList& Lc);
int getMainElement(SqList L);

int main() 
{
    int aa[6] = { 1, 2, 3, 4, 5, 8};
    SqList La = createList_Sq(aa, 6);
    int ab[6] = { 2, 5, 7, 9, 10, 12 };
    SqList Lb = createList_Sq(ab, 6);

    //Part1：两表合并
    // 1 2 2 3 4 5 5 7 8 9 10 12
    SqList Lc;
    MergeList_Sq(La, Lb, Lc);
    printf("Lc = {");
    printSqList(Lc);

    // //Part2：求序列的主元素
    // SqList L1;
    // int a1[7] = { 2, 6, 6, 3, 6, 8, 7 };
    // L1 = createList_Sq(a1, 7);
    // int result = getMainElement(L1);  //预期结果：-1
    // printf("result = %d", result);

    // SqList L2;
    // int a2[9] = { 2, 6, 6, 3, 6, 8, 6, 7, 6 };
    // L2 = createList_Sq(a2, 9);
    // result = getMainElement(L2);  //预期结果：6
    // printf("result = %d", result);

    // SqList L3;
    // int a3[8] = { 7, 7, 6, 7, 6, 7, 6, 7 };
    // L2 = createList_Sq(a3, 8);
    // result = getMainElement(L2);  //预期结果：7
    // printf("result = %d", result);

    return 0;
}

//练习4：将顺序表La和Lb合并为Lc
void MergeList_Sq(SqList La, SqList Lb, SqList& Lc) 
{
    int i = 0, j = 0;   
    ElemType ai, bj;
    
    //练习4.1：创建空表Lc 
    InitList_Sq(Lc, La.length + Lb.length + 5, 10);
    // if ( != OK) {
    //     printf("Error: Failed to initialize list Lc\n");
    //     return;
    // }

    //Add your code here 

    while (i < ListLength_Sq(La) && j < ListLength_Sq(Lb) )  // 表La和Lb均非空
    {      
      //练习4.2：两表合并 
      //Add your code here 
        GetElem_Sq(La, i+1, ai);

        GetElem_Sq(Lb, j+1, bj);

        if(ai <= bj)  Append_Sq(Lc,ai), i++;  //顺序性
        else Append_Sq(Lc,bj), j++;

    }

    //练习4.3：处理“La未空，但Lb已空”的情况
    while (i < La.length) { 
        GetElem_Sq(La, i+1, ai);
        Append_Sq(Lc,ai), i++;
       //Add your code here
    }

    //练习4.4：处理“La已空，但Lb未空”的情况
    //Add your code here  
    while (j < Lb.length) {
        GetElem_Sq(Lb, j+1, bj);
        Append_Sq(Lc,bj), j++;
    }   

}

//练习5：求序列A中的主元素，如果A没有主元素，则返回-1
int getMainElement(SqList L)
{
    //Add your code here

    return 0; //This is tempoary code. Modify it if necessary.
}

```
### DS02ES30

```cpp

#include <stdlib.h>
#include "SqList.h"

//练习1：初始化一个空的顺序表L
Status InitList_Sq(SqList& L, int size, int inc) 
{ 
    //Add your code here
    if(size<1 || inc < 1) return ERROR;
    L.elem = (ElemType*)malloc(size*sizeof(ElemType));
    if(L.elem == NULL) return ERROR;

    L.length = 0;
    L.size = size;
    L.increment = inc;

    return OK;
}

//练习2：获取第i个元素的值，用参数e返回该值
Status GetElem_Sq(SqList L, int i, ElemType& e) 
{
    if (i < 1 || i > L.length || L.length == 0) {
        return ERROR; //无效位置
    }
        
    //Add your code here
    e = L.elem[i - 1];


    return OK;
}

//练习3：在顺序表L表尾添加元素e
Status  Append_Sq(SqList& L, ElemType e) 
{         

    ElemType* newbase;
    if (L.length >= L.size) {  // 扩容
        //Add your code here
        newbase = (ElemType*)realloc(L.elem, (L.size + L.increment) * sizeof(ElemType));
        if(newbase == NULL) return ERROR;
        L.elem = newbase;
        L.size += L.increment;
    }

    L.elem[L.length] = e;
    L.length++;
    
    return OK;
}


int ListLength_Sq(SqList L){
    return L.length;
}

/**
  * 创建一个顺序表
  * @param a[]：数组中的每一个元素作为顺序表中的元素
  * @param n: 数组中的长度
  */
SqList createList_Sq(int a[], int n)
{
    SqList L;
    InitList_Sq(L, n, 10);
    for (int i = 0; i < n; i++)
    {
        Append_Sq(L, a[i]);
    }

    return L;
}

```

### DS02E30

```cpp

#pragma once
typedef int ElemType;
typedef struct {
	ElemType* elem;     // 存储空间的基址
	int top;    // 栈顶元素的下一个位置，简称栈顶位标
	int size;    // 当前分配的存储容量
	int increment;    // 扩容时，增加的存储容量
} SqStack;         // 顺序栈

#define OVERFLOW -1
#define OK 1
#define ERROR 0
#define TRUE 2
#define FALSE -2

#define INITSIZE 5   //栈的初始容量
#define INCREMENT 2   //栈扩容时的增量

typedef int Status;

Status InitStack_Sq(SqStack& S, int size, int inc);
Status StackEmpty_Sq(SqStack S);
Status Push_Sq(SqStack& S, ElemType e);
Status Pop_Sq(SqStack& S, ElemType& e);

```

### DS02E30  去重

```cpp
//练习4：将顺序表La和Lb合并为Lc
void MergeList_Sq(SqList La, SqList Lb, SqList& Lc) 
{
    int i = 0, j = 0,k = 0;   
    ElemType ai, bj, ck;
    
    //练习4.1：创建空表Lc 
    InitList_Sq(Lc, ListLength_Sq(La) + ListLength_Sq(Lb) + 5, 10);
    // if ( != OK) {
    //     printf("Error: Failed to initialize list Lc\n");
    //     return;
    // }

    //Add your code here 

    while (i < ListLength_Sq(La) && j < ListLength_Sq(Lb) )  // 表La和Lb均非空
    {      
      //练习4.2：两表合并 
      //Add your code here 
        GetElem_Sq(La, i+1, ai);

        GetElem_Sq(Lb, j+1, bj);

        if(ai < bj ){ if(ai != Lc.elem[ListLength_Sq(Lc)-1]) Append_Sq(Lc,ai); i++;  }//顺序性
        else {if(bj != Lc.elem[ListLength_Sq(Lc)-1])  Append_Sq(Lc,bj); j++;}
    }


    //练习4.3：处理“La未空，但Lb已空”的情况
    while (i < La.length) { 
        GetElem_Sq(La, i+1, ai);
        if(ai != Lc.elem[ListLength_Sq(Lc)-1])
        Append_Sq(Lc,ai); i++;
       //Add your code here
    }

    //练习4.4：处理“La已空，但Lb未空”的情况
    //Add your code here  
    while (j < Lb.length) {
        GetElem_Sq(Lb, j+1, bj);
        if(bj != Lc.elem[ListLength_Sq(Lc)-1])
        Append_Sq(Lc,bj); j++;
    }   



}

```

### DC02PE53

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_L(LStack S) 
{    // Add your code here
    if(S == NULL) return TRUE;
    else return FALSE;

}

```

### DC02PE55

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status GetTop_L(LStack S, ElemType &e) 
{    // Add your code here
    if(S == NULL) return ERROR;

    e = S -> data;

    return OK;


}

```

###  DC02PE61

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status QueueEmpty_LQ(LQueue Q)
{    // Add your code here
    if(Q.front == NULL) return TRUE;
    return FALSE;

}

```

### DC02PE63

```cpp
#include "allinclude.h"  //DO NOT edit this line
int QueueLength_LQ(LQueue Q) {
    int count = 0;
    QueuePtr current = Q.front;
    while (current != NULL) {
        count++;
        current = current->next;
    }
    return count;
}

```

### DC02PE71

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status ListEmpty_L(LinkList L) 
{    // Add your code here

    if(L->next == NULL) return TRUE;
    
    return  FALSE;

}

```
### DC02PE82

```cpp

#include "allinclude.h"  //DO NOT edit this line

LinkList MakeNode(ElemType x) {

    LinkList F = (LinkList)malloc(sizeof(LNode));

    if(F == NULL) return NULL;

    F->data = x;
    F->next = NULL;

    return F;
}

Status InsertAfter_L(LNode *p, LNode *q) {
    if(p == NULL || q == NULL)  //不合法
    return ERROR;
    q -> next = p -> next;
    p -> next = q;

    return OK;
}

LinkList Search(LinkList L, int i) {
    // 在单链表L中查找第i个位置
    // 判断i的合法性，i过小或者过大返回NULL
    // 若存在则返回第i-1个位置（结点指针）

    if (L == NULL || i < 1) return NULL;

    LinkList p = L;
    //不要改变链表
    int j = 0;

    while (p != NULL && j < i - 1) {
        p = p->next;
        j++;
    }
    
    return p;
}

Status Insert_L(LinkList L, int i, ElemType e) 
{   // Add your code here
    LinkList p = Search(L, i);
    if (p == NULL) {
        return ERROR;
    }

    LinkList newNode = MakeNode(e);
    
    if (newNode == NULL) return ERROR;
    
    newNode->next = p->next;
    p->next = newNode;
    
    return OK;
}

```

### DC02PE75

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status ClearList_L(LinkList &L)
{    // Add your code here
    if (L == NULL) {
        return ERROR;
    }
    LinkList p = L->next;
    LinkList temp;
    while (p != NULL) {
        temp = p;
        p = p->next;
        free(temp);
    }
    L->next = NULL;
    return OK;
}

```

### DC02PE84

```cpp
#include "allinclude.h"  //DO NOT edit this line

LinkList Search(LinkList L, int i) {
    // 在单链表L中查找第i个位置
    // 判断i的合法性，i过小或者过大返回NULL
    // 若存在则返回第i-1个位置（结点指针）

    if (L == NULL || i < 1) return NULL;

    LinkList p = L;
    //不要改变链表
    int j = 0;

    while (p != NULL && j < i - 1) {
        p = p->next;
        j++;
    }
    
    return p;
}

Status DeleteAfter_L(LNode *p, ElemType &e)
{
    LNode *q;
    if(p == NULL || p->next == NULL) return ERROR;
    q = p->next;
    p -> next = q -> next;
    e = q -> data;

    free(q);

    return OK;
}


Status Delete_L(LinkList L, int i, ElemType &e) 
{   // Add your code here
    
    LinkList p = Search(L, i);
    if (p == NULL || p->next == NULL) {
        return ERROR;
    }
    
    return DeleteAfter_L(p, e);
}

```

### DC02PE73

```cpp

#include "allinclude.h"  //DO NOT edit this line
Status DestroyList_L(LinkList &L) 
{    // Add your code here
    if (L == NULL) return OK; 
    
    LinkList p = L;
    LinkList temp;
    
    while (p != NULL) {
        temp = p;
        p = p->next;
        free(temp);
    }
    
    L = NULL; 
    return OK;
}

```

### DC02PE77

```cpp

#include "allinclude.h"  //DO NOT edit this line
int ListLength_L(LinkList L) 
{   // Add your code here
    if (L == NULL) return -1;

    int j = 0;
    LinkList p = L;
    while (p != NULL) {
        p = p->next;
        j++;
    }

    return j - 1;

}

```