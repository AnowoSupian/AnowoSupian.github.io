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