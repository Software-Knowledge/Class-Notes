<!-- TOC -->

- [1. 数组](#1-数组)
  - [1.1. 一维数组](#11-一维数组)
  - [1.2. 一位数组的初始化](#12-一位数组的初始化)
  - [1.3. 二维数组](#13-二维数组)
  - [1.4. 多维数组](#14-多维数组)
  - [1.5. 字符数组](#15-字符数组)

<!-- /TOC -->

# 1. 数组
1. 数组作为参数`int a[]`
2. 特征:
    1. 相同类型
    2. **连续存储**:0 - n-1
3. 数组名的含义:
  + `int A[6]`的A是代表6个int的集合
  + `sizeof(A)`:6 * sizeof(int)

## 1.1. 一维数组
1. 类型定义`T name[number]`
2. 赋值操作，部分赋值的话，之后按照默认值
3. 函数接口:`void f(int a[], int n);//这里面的a的身份已经发生了变化`
  + 此时a已经不知道有多少个元素了
  + C++是允许数组的越界(给予语言表达极大的灵活性)，不检查数组的越界
  + 元素个数需通过参数**显式**给出，不可以通过sizeof来获得:`void f(char a[]);`
```c++
char s1[]="abc";
cout << s1;//实际上是{'a','b','c','\0'}
char s2[]={'a','b','c'};
cout << s2;//错误
```
4. 读取字符数组的时候，我们可以根据`\0`来判断是否字符串结束
5. 为什么会出现“烫烫烫”:`0xCC`是烫(在VS下由于未初始化，VS为了帮助你发现问题，对于未使用的内存空间我们都使用0xCC填充，0xCC是指3号中断)
  + 0xCC:烫
  + 0xCD:屯:heap(在栈部分出现的额问题)
  + 数组未初始化:在对应位置填充0xCC,其上下文填充0xFD
  + 释放内存，如果没有请0，则会帮你将内存中的值清理成一个特定的值，用来防止内存为清零。

## 1.2. 一位数组的初始化
1. 整数数组的初始化
```c++
//默认初始化
int a[5] = {};    //[0, 0, 0, 0, 0]
//全部初始化为0
int a[5] = {0};    //[0, 0, 0, 0, 0]
//c++11新写法
int a[5]{};    //[0, 0, 0, 0, 0]

//注意，想要整型数组 全部初始化为1的时候不能粗暴的设置为 
int a[5] = {1};    //[1, 0, 0, 0, 0]
// 因为 数组初始化列表中的元素个数小于指定的数组长度时， 不足的元素以默认值填补。
//可以分别赋值
int a[5] = {1,1,1,1,1}; //[1,1,1,1,1]
```

2. 字符串的初始化-栈初始化
```c++
string *str = string[5];    //调用5次默认构造函数
string *str1 = string[5]{"aaa"};    //数组中的第一个元素调用 string::string(const char *)  进行初始化。后面四个调用 默认构造函数
```

3. 数组的默认初始化:如果不明确指出初始化列表，那么基本类型**不会被初始化**（全局变量和静态变量除外），所有内存都是脏数据；且自定义的类类型会为每个元素调用默认构造函数进行初始化
```c++
int a[5]{};
a[6];      //32766
a[10];    //1474921429
// Xcode会提示 Array index 10 is past the end of the array (which contains 5 elements)。虽然不会爆红，但是Xcode提示越界了。这在程序中也是需要特别注意的,越界时会取到脏数据。
string str[5];     //["","","","",""]
string str1[5] = {"","2","",""};     //["","2","',"",""]
string str2[5] = {"a"};     //["a","","","",""]
```

## 1.3. 二维数组
1. `T name[number1][number2]`
2. 也是按照顺序进行排列的，不过是一行一行的放置而已
3. 二维数组初始化

```c++
int **p;
p = new int*[10];//一个有10个元素的指针数组
for(int i = 0; i < 10; ++i){
  p[i] = new int[5];
}
```

## 1.4. 多维数组
1. 定义:`T  A[c1][c2]`
2. 存储组织:
3. 参数传递:`void f(int a[][3], int n);`
  + 理解为int[3] a[] (单个元素是三个int)
  + 缺省第1维
```c++
typedef T T1[c2];
typedef T1 A[c1]; 
```
4. 升/降维处理


## 1.5. 字符数组
1. 直接按照字符串形式输出
2. 字符数组的约定是，以`\0`作为结尾
