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