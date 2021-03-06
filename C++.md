# 第1单元 初识C++

## 1.1 C++简介

### 1.1.1 C++的发展简史

#### 1.1.1.1 课程介绍

##### 书籍介绍

* C++ Prime 
* 大话数据结构
  
#### 1.1.1.2 编程环境

推荐使用Visual Studio 2019 

不过我用的是VS Code

#### 1.1.1.3 C++发展史

前期的阶段老师没讲

##### 重要的C++版本

* C++98
* C++11
* C++20

我们学的是C++11版本的

同时编译器使用的是2019版本的，因为编译器往往需要过两年才能适配新版本的语法。

##### C++的主要用途

- 服务器端编程
- 算法设计
- 通过Qt进行Linux、国产化操作系统的桌面应用程序开发，自主可控的软件开发。

### 1.1.2 C++的特点

#### 1.1.2.1支持四种编程范式

Java号称是纯面向对象的语言，他的main封装在class类里面。

四种编程范式：面向过程、面向对象、泛型编程、函数式编程

* 面向过程
    * 瀑布式开发模型
        * 其实就是正常的程序流程构设
        * 非常理想化，没有考虑在实际开发过程中可能产生的需求变化和将来的软件升级。
        * 在软件开发过程中唯一不变的是变化！
* 面向对象，OOP(Object-Oriented Programming)
    * 三个基本特征：封装、继承、多态
* 泛型编程 
    * 与类型无关的编程，是通过模板实现的。以模板为基础，STL实现通用的容器类。
    * 感觉上就是调用库。
* 函数式编程

#### 1.1.2.2 适合编写大型应用程序

1. 不适合编写操作系统，操作系统的内核还是由C语言完成的。
2. C++的一些语法设计，考虑了很多人同时开发，例如命名空间namespace。
3. 面向对象程序设计（OOP），根本上解决了需求发生变化、软件升级的问题

#### 1.1.2.3 可复用、可扩充、可维护和灵活性好

#### 1.1.2.4 C++的缺点

* C++的强大在于提供高级抽象的同时又不放弃对程序的细节控制。
* 过于频繁的更换，除了增加功能以外，也使得C++变得越来越复杂。苦了人脑，幸福电脑。

## 1.2 第一个C++程序

### 1.2.1 Hello World

```C++
#include <iostream>
int main(){
    std::cout<<"Hello World!\n";
}
```

#### 1.2.1.1 C++与C的不同

1. 头文件没有后缀名
2. C++兼容C，可以在C语言头文件名称前加上**c**后去除后缀名进行引用。
3. 基本输出不同
   
```C++
std::cout << "Hello,World!\n";
//std::cout是标准命名空间中定义、ostream类型的全局变量，代表显示器。
```

* std是标准命名空间（standard）
* ::是域操作符（相当于的）
* cout是控制台输出设备
* <<是输出运算符

## 1.3 C++对C语言的扩充

### 1.3.1 命名空间

为了解决合作开发时命名冲突的问题，C++引用了命名空间。

```C++
namespace Li{
    int a=100;
    void printInt(){std::cout << a << std::endl;}
    //endl是标准命名空间定义的换行符
}
namespace Han{
    int a=200;
    void printInt(){std::cout << a << std::endl;}
}
```

在不同的namespace中可以重复定义相同的函数或相同的变量。

```C++
//调用
int main(){
    Han::a = 300;
    Li::printInt();//输出100
    Han::printInt();//输出300
}
```

#### 1.3.1.1 命名空间简写方法

1. 使用 **::** 引用命名空间中定义的元素
`std::cout << "C++" << std::endl;`
2. 使用using引用命名空间中的某个元素

```C++
using std::cout;
cout << "C++" << std::endl;
```

3. 使用using引用命名空间
```C++
using namespace std;
cout << "C++" << endl;
```

### 1.3.2  控制台输入输出

#### C++的I/O解决方案

* 使用 **cin** 接收从键盘输入的数据，用 **cout** 向屏幕上输出数据（这2个过程又称为“标准I/O”）。
* C++也对从文件中读取数据和向文件中写入数据做了支持（统称为“文件I/O”）。

#### C++标准库中包含了“流类”

* istream：常用语接收从键盘输入的数据；
* ostream：常用语将数据输出到屏幕上；
* ifstream： 用于读取文件中的数据；
* ofstream： 继承自istream和ostream类，因为该类的功能兼两者于一身，既能用于输入，也能用于输出；
* fstream：兼ifstream和ofstream类功能于一身，既能读取文件中的数据，又能向文件中写入数据。
* cin是istream类的对象，cout是ostream类的对象，在<iostream>头文件中声明。
* 使用cin和cout需要包含<iostream>头文件，当然还需要使用std命名空间。

#### 输入

* 输入流对象cin和输入运算符>>配合，用于用户输入
* 在连续输入多个变量时，以空白(空格、回车、制表符)为分隔符
  
```C++
int a,b;
cin>>a>>b;
//如果是字符型的话，分隔符会被识别成数据。
```

####  输出

* 输出对象cout和输出运算符<<配合，用于用户输出
* 可以连续输出多个不同类型的常量或变量

```C++
cout<<"Hello,C++"<<endl;
//注意流的方向，要指向cout
```

1. **两个运算符都是从左向右结合**
2. cin>>a的返回值时cin,cout>>"Hello,C++"的返回值是cout。所以可以连续执行。

#### 小例子

```C++
#include<iostream>
using namespace std;
int main(){
    int a=0,b=0;
    cout << "Please Enter Two Integers:"
    cin >>a >> b;
    cout << a << "+" << b << "=" << a+b <<endl; 
}
```

C语言中的`scanf`是不安全的函数，如果要使用需要`#define _CRT_SECURE_NO_WARNINGS`

### 1.3.3 增强类型

1. const常变量
2. bool布尔类型
3. enum枚举类型

#### 1.3.3.1 const的基本概念

* 定义只读变量的关键字

```C++
const int a = 100;
//const的量一定要赋值进行初始化
const int * pa = &a;
 //const int * 类型的值不能用于初始化int*类型的实体
```

* 在C语言中const变量不能定义数组长度，但是在C++中可以。

```C++
const int size = 100;
int arr[size];
```

#### 1.3.3.2 const与指针

* 指向`常量`的指针，称为**常量指针**。
    * 解释：所指的量是一个常量。
    * int * const p
    * 当使用是形参时，传入变量地址就可以。
* `不能指向其他变量`的指针，称为**指针常量**。
    * const int * p;
    * int const * p;
    * 解释：只能指向某一量，设定后无法更改。
    * 数组就是**指针常量**
* 指向整型常量的指针常量。
    * const int * const p;

### 1.3.3 布尔类型

在C语言的C99版本中可以引用<stdbool.h>来使用bool类型

* enum

```C++
enum SEASON{SPRIG,SUMMER,AUTUMN,WINTER};
SEASON s1 = SUMMER；
```

### 1.3.4 参数默认值

直接在形参中初始化

```C++
#include<iostream>
using namespace std;
void add(int x,int y=1,int z=2){
    cout<<x+y+z<<endl;
}
int main(){
    add(1);     //4
    add(1,2);   //5
    add(1,2,3); //6
    return 0;
}
```

1. 参数默认值可在函数声明中出现一次，如果没有函数声明，只有函数定义，那么可以在函数定义中设定

```C++
//fun.h
int Add(int a,int b=1,int c=2);
//fun.cpp
int Add(int a,int b,int c){
    return a+b+c;
}
```

1. 默认参数赋值的顺序时自右向左

```C++
int Add(int a,int b=0,int c)
//这种是错的
```

### 1.3.5 函数重载

* 所谓函数重载，是指在同一个作用域内、函数名相同、参数列表不同的多个函数。
* 编译器会根据所给的参数自动选择相应的函数。
* 参数列表不同：
    1. 参数类型不同
    2. 参数个数不同
    3. 参数类型、个数均不同
    * **形参变量名不同不构成重载！**
* 当重载函数有默认值时，要防止二义性！
    * 两个同名函数之间，只差若干个默认值，当未指定默认值时，程序就不知道使用哪个函数了。

### 1.3.6 引用

#### 1.3.6.1 引用的基本概念

* 引用就是给变量取的一个别名

```C++
int a = 100;
int &ra = a;
ra = 200;
cout<<a<<endl;
```

* 引用的语法
    * 类型 & 引用名 = 变量名；
* &的含义
    1. int & ra = a;    在定义变量的时候使用&，表示引用
    2. int *p;p=&a;     一元操作，表示取地址
    3. a & b;           二元运算符，表示运算中的按位与
    4. a && b;            表示逻辑与
* 使用引用的注意事项
    1. 引用必须初始化
    2. 不能引用常量
    3. 不能引用数组
    4. 引用只能时某个固定变量的引用，不能再引用其他变量。
* 没必要在一个函数内使用引用，通常在两个函数之间使用引用
    * 形参是引用
        * 在C语言中，函数参数的两种形式
            * 传值
            * 传地址
    * 返回值是引用

#### 1.3.6.2 函数参数的三种形式

##### 1. 传值

``` C++
void Swap1(int x,int y){int temp=x;x=y;y=temp}
int main(){
    int a=100,b=200;
    Swap1(a,b);
}
```
* 传值，子函数无法改变调用函数中变量的值。
* 每个函数的一次运行都会有一个自动分配的栈，局部变量位于栈中。形参也是局部变量。
  
函数每一次运行都会有一个独立的栈，用来存放局部变量。这就导致了`主函数`和`自定义函数`中分别定义的变量不互通，主函数传入变量的时候仅仅传入了值，而非变量本身。

##### 2. 传地址

```C++
void Swap2(int *p,inty *q){int temp=*p;*p=*q;*q=temp;}
int main(){
    int a=100,b=200;
    Swap2(&a,&b);
}
```

* 传地址，子函数可以修改调用函数中变量的值
* 下面是比较常见的初学者的错误写法

```c++
Swap3(int *p,int *q){int *temp=p;p=q;q=temp;}
```

这种方式直接传输地址，使得不同函数可以直接读取或写入`其他函数栈`中`相应地址`的`变量`。

##### 3. 传引用

```C++
void Swap4(int &x,int &y){int temp=x;x=y;y=temp}
int main(){
    int a=100,b=200;
    Swap4(a,b);
}
```

* 传引用，可以达到传指针同样的效果，但是调用更方便。
* 与传地址不同的地方就是函数定义不是`*x`了，而是`&x`，这样传入的可以直接传入变量
* 个人理解：直接将传入函数`命名别名`后，在函数中进行使用。
* 尽管在形参中没有认为进行初始化，但是`从形参到实参的过程就是初始化！`

#### 1.3.6.3 引用——函数的返回值

不会在一个函数内部使用引用，引用仅应用于两个函数之间

1. 函数参数是引用类型
2. 函数的返回值是引用

```C++
int & At(int b[],int index){
    return b[index];
}
int main(){
    int a[3] = {1,2,3};
    At(a,1) = 100;
    //b[index]等价于a[1]
    //等价于a[1] = 100
}
```

* 也就是说，可以让`函数调用作为左值`。
* 可以避免返回值被拷贝
* 注意：不能返回局部变量的引用
    * 因为局部变量存在函数的栈中，函数一旦运行结束，栈会被释放清空，那么这个数据就不存在了。

#### 1.3.6.4 引用——常引用

* int & a=b;a就是b。
* 针对引用类型的函数参数，形参就是实参。这带来两种用途：
    1. 子函数可以通过引用类型的参数来修改调用函数中的变量，并且不用使用指针（都不喜欢指针，能不用尽量不用）。
    2. 避免了形参到实参的初始化过程，从而提高了效率。
* 如果只想2，而不想1，可以使用`常引用`
```C++
void fun(const XYZ & r){……}
```
* 在面向对象编程中，类类型属于自定义类型，比简单类型占用更多的内存空间。如果函数的参数类型是类类型，为了提高效率，我们往往使用常引用。

### 1.3.7 内存管理——堆、栈

* 不是数据结构中的堆和栈

1. C语言的内存区域
   * 堆
       * 堆是用于存放进程运行中被动态分配的`内存段`。当进程调用`malloc/free`等函数分配内存时，新分配的内存就被动态添加到堆上（堆被扩张）/释放的内存从堆中被剔除（堆被缩减）。
   * 栈
       * 栈又称堆栈，存放`程序的局部变量`(但不包括static声明的变量)和`函数被调用时的参数和返回值`。

* 从低位地址到高位地址逐个是：

  1. 代码区：函数代码块的二进制代码。
  2. 数据区
  3. 文字常量区：常量字符串存放于此
  4. 未初始化静态变量区：没有初始化的全局变量和静态变量
  5. 已初始化的静态变量区：初始化的全局变量和静态变量
  6. 堆区：动态分配的数据
  7. 栈区：局部变量存放于此
  8. 命令行参数区：命令行参数和局部变量

2.  C++内存区域
   * C++中内存分成5个区：
        1. 栈：内存由编译器在需要时`自动`分配和释放。通常用来存储局部变量和函数参数。（为运行函数而分配的局部变量、函数参数、返回地址等存放在`栈区`）
        2. 堆：内存使用`new`进行分配，使用`delete`释放。如果未能对内存进行正确的释放，会造成`内存泄漏`。
        3. 自由存储区：使用`malloc`进行分配，使用`free`进行回收。
        4. 全局/静态存储区：全局变量和静态变量被分配到同一块内存中，C语言中区分初始化和未初始化的，C++中不再区分了。(全局变量、静态数据、常量存放在`全局数据区`)
        5. 常量存储区：存储常量，不允许被修改。
* 栈和堆的对比
  * 栈
    1. 内个函数的第一次运行都会有一个独立的栈
    2. 自动分配、自动释放
    3. 通过变量直接使用
  * 堆
    1. 全局只有一个堆
    2. 手动分配、手动释放
    3. 通过指针间接使用

```C++
void fun(){
    int a = 0;
    a++;
}//函数运行结束，栈被自动释放
int main(){
    fun();
    fun();
}
//运行了两次，有两个栈，栈中的a都为1
```
```C++
void fun(){
    int * p =new int;
    //这里*p是局部变量，存在栈中。同时堆中开辟了一块int类型大小的空间。
    *p = 100;//p指向的内存单元为100，也就是堆中相应内存单元为100.
    delete p;
    //将堆中数据回收，但*p还在，仍然指向堆中的那个地址，称为“野指针”
}
```

### 1.3.8 new/delete

* 在C语言中，动态分配内存用`malloc()`函数，释放内存用`free()`函数。
```C++
int *p = (int*)malloc(sizeof(int));//分配一个int型的内存空间
//将int大小的空间分配给p并将无类型的p进行强制类型转换
free(p);//释放内存
//分配在堆中
```

* C++新增了两个关键字，使用起来更简介
  * `new`用来动态分配内存
```C++
int *p = new int;//分配一个int型的内存空间
```
  * delete用来释放内存
```C++
delete p;
```

1. 根据后面的数据类型来`自动推断所需空间大小`
2. 返回具体类型的指针，不需要进行类型转换

* 分配一组连续的数据（动态数组）
  * C语言版本
```C
int *p = (int *) malloc(sizeof(int)*10);
free(p);
```
  * 版本
```C++
int *p = new int[10];
delete []p;
```

* new/delete的优点
  * `new`可以自动推断所需空间大小，而`malloc`需要通过`sizeof`进行计算。
  * `new`自动返回所需类型指针，而`malloc`返回的是`void *`，还需要类型转换
  * `new`在分配空间的同时还可以初始化，而`malloc`只能分配空间
```C++
int *p = new int(100);
//将p初始化为100
```
  * 我们可以笼统的说`new`和`malloc`都是在`堆`中分配内存，但仍然有差别，所以`new/delete`和`malloc/free`不能混用。
  * `new/delete`支持C++的新特性，包括：重载、调用构造/析构函数。

### 1.3.8 静态数组、动态数组

* 静态数组
```C
const int SIZE = 100;//SIZE是常量
int a[SIZE]; // 定义数组时，数组的大小必须是常量
```
* 动态数组
```C++
int size = 100;//size是变量
int *p = new int[size];//可以在内存中分配任意大小的内存
```
* 指针p和数组名a都指向内存中一段内存的首地址，且用法都是一样的
```C++
*(a+10)=123;
p[10]=123;
//相互等价
```
* 差别在于，a是`指针常量`，p是`指针变量`,`p++`可以，`a++`不行。

### 1.3.9 各种指针和指针数组

因为指针的存在，所以C/C++的程序可以直接访问内存，从而提高程序的运行速度。

在大型程序中，核心数据不可能存放在栈中，一定是存放在堆中，所以只有通过指针进行访问。换言之，**核心数据一定是`new`出来的**！

* 在开发的过程中，能不用指针运算，尽量不用指针运算。
  * 使用下标运算，而不是用`*`运算，例如：`*(P+1)等价于p[i]`，不过`*p`比`p[0]`好看一些。
  * 能够使用引用，尽量使用引用，例如：通过指针和引用都可以实现交换函数，`swap(&a,&b)`肯定不如`swap(a,b)`。

struct和class中指针类型的成员变量，习惯上不会使用引用，而是指针

#### 各种指针

1. 指针和const组合：
   * 常量指针：指向常量的指针
   * 指针常量：`int a[100]`;
2. 指针和数组结合：
   * 指向数组的指针：`int *p = a`
   * 指针数组：数组的每一个元素都是指针。
     * `int *a[100]`
3. 指针的指针：
   * 指针和自己结合，`int **p`
   * 不仅仅数组名是指针常量，函数名也是指针常量
     * 通过函数指针，C语言也能做到面向对象
     * 函数指针->仿函数->Lambda表达式

## 1.4 C++中的两个新语法

### 1.4.1 nullptr——野指针

野指针主要是因为这些疏忽而出现的删除或申请访问受限内存区域的指针。

1. 指针变量未初始化
   * 任何指针变量刚被创建时不会自动称为空指针，它的缺省值是随机的，它会乱指一气。这个时候，通过指针访问内存就会出错。所以，指针变量在创建的同时应该被初始化，要么将指针设置为NULL，要么让它指向合法的内存。
2. 指针释放后未置空
   * 有时指针在free或delete后未赋值NULL，便会是人认为是合法的。他们只是吧指针所指的内存给释放掉，并没有吧指针本身干掉，此时指针指向的就是垃圾内存。释放后的指针应立即将指针归置为NULL，防止产生“野指针”。
3. 指针操作超越变量作用域
   * 在子函数中定义的局部变量指针，当函数运行结束后会被释放，此时再通过指针访问内存，就会报错。

不能将`nullptr`转换为int类型。

### 1.4.2 基于范围的for循环

类似于Python的for语法

```C++
int v[] = {1,2,3,4,5,6};
for(int e:v)
    cout<<e<<" ";

//等价于

int v[] = {1,2,3,4,5,6}
for(int i=0;i<6;i++)
    cout<<v[i]<<" ";
```

# 第2单元 类与对象

## 2.1 面向对象程序设计思想

### 2.1.1 面向对象的编程思想

对于**面向对象**程序设计而言，最重要的一个特征就是**数据封装**。

所谓**数据封装**，就是通过类来实现信息的抽象和隐藏。学习了类的相关知识，才能真正走进面向程序设计的世界。

#### 面向过程程序设计

**面向过程程序设计**对于较为简单的需求通常能够很好地满足。如果**问题比较复杂**，在项目开始之初就完成模块的**合理划分**往往比较困难。当**数据结构**改变时，所有相关的**处理过程**都要进行相应的修改，程序的**可用性极差**。

在程序中使用对象映射现实中的事物，利用对象之间的关系描述事物之间的联系，这种思想就是面向对象。

Object-Oriented，简称OO。

把构成问题的事物按照一定的规则划分为多个独立的对象，然后通过调用对象的方法解决问题。

当应用程序功能发生变更时，只需要修改个别对象就可以了。

#### 面向对象程序设计思想

1. 分析(OOAnalyse)
2. 设计(OODesign)
3. 开发(OOProgramming)
4. C++是一个面向对象的编程语言(OOPLanguage)

#### 概述

**面向对象程序设计**描述的是客观世界中的事物，以**对象**代表一个**具体的事物**，把**数据和数据的操作方法**放在一起而形成的一个**相互依存**又不可分割的整体。

由此可见，**面向对象程序设计**所强调的基本原则就是**直接面对客观存在的事实**，将人们在日常生活中习惯的**思维方式和思维表达式**应用**软件开发**中，使**软件开发**从过分专业化的**方法、规则**中回到客观世界，回到人们通常的**思维方式**。**面向对象**的思想更适合用于**大型系统项目**的开发。

### 2.1.2 面向对象的三大特征

#### 面向对象的三大特征

三大特征具有承上启下的关系，而且适用于所有面向对象的编程语言。

* 封装
  * 封装就是隐藏。它将数据(属性)和数据处理过程(行为)封装成一个独立性很强的模块(类)。对外提供接口，不需要让外界知道具体的实现细节。
  * 不封装会有哪些问题？
    * 容易因为传参错误出现逻辑错误。
    * 面向对象的程序设计过程中，数据和处理数据的函数封装在一个类中，不存在跨模块处理数据的问题。
* 继承
  * 继承描述的是父类和子类的关系。通过继承，子类可以扩展父类的功能，从而提高了代码的**可重用性**，降低了代码维护的难度。
  * 共同的功能写在父类中
  * 不同的功能写在子类中
* 多态
  * 是指不同事物对统一信息产生的不同行为。

## 2.2 初始类和对象

### 2.2.1 类的定义

C++中的类(class)可以看做C语言中的结构体(struct)的升级版。

结构体是一种构造类型，可以包含若干成员变量，每个成员变量的类型可以不同；可以通过结构体来定义结构体变量，每个变量拥有相同的成员，只是他们的取值不一样。

```c++
class Student{
    public:
    const char* name;
    int age;
    float score;
    void Display(){
        cout << name << "今年" << age << "岁，";
        cout << "考了" << score << "分" << endl;
    }
};

int main()
{
    Student s1;
    s1.name = "小明";
    //这里有问题，会在之后的章节里探讨
    sl.age = 15;
    sl.score = 95;
    sl.Display();
}
```

1. 关键字从`struct`变成了`class`
2. 访问权限`public`表示共有，是为了可以从外部访问。
3. `Display`从全局函数变成了成员函数，也就是对象s1的成员函数，所以函数参数、函数中通过形参引用`name`等成员，都省略了
4. Display(s1)写成了s1.Display();

#### 类的语法格式

```c++
class 类名
{
    成员访问限定符:
        数据成员;
    成员访问限定符:
        成员函数;
}
```

标识符的命名规范:
1. 只能包含字母、数字、下划线
2. 只能以字母、下划线开头
3. 不能是关键字

限定访问规则：
`puiblic > protected > private`

类是事物的抽象描述，若想定义类就需要抽象出事物的属性及方法。

### 2.2.2 类外定义成员函数

成员函数的函数体既可以写在类中，也可以类外实现。

```C++
//Student.h
class Student{
    void Study();
}

//Student.cpp
#include "Student.h"
void Student::Stundy(){
    cout << "学习C++";
}
```

Stundent.cpp -> Stundent.lib,然后和Stundent.h一起发布供第三方调用

# 第2次上课

```C++
int* p = new int;
//在Visual Studio中，*要跟int后面
```

一定要提防野指针，编译器无法识别！人工纠错非常的困难！

```C++
int* p = new int;
//在堆中分配内存，新建栈中指针p并指向堆
delete p;
//回收堆中内存，但p的指向还在
*p = 100
//编译器不会报错，运行的时候会随机报错，因为p指向的空间已经无法使用，无法写入数据！
p = new int;
//重新申请内存并使p指向这个内存。
```
# 网课

### 2.2.3 对象的创建和使用

* 对象的定义语法：

```C++
类名 对象名 [= 初始值];
类名 对象名 [(初始值列表)];
```

* 上述定义的对象和变量一样，仍然在栈中(自动分配和释放)
* 访问对象的公有成员(含成员变量、成员函数)，和结构体变量
* 访问成员的方法一致：
  * 对象名.成员变量
  * 对象名.成员函数(实例列表)
* 也可以在堆中创建对象：
  * `Student* ps = new Student; delete ps;`
* 指针是栈里的局部变量，指向堆(手动分配和释放)里面的对象
* 访问对象的公有成员(含成员变量、成员函数)，和结构体指针访问成员的方法一致：
  * 指针->成员变量
  * 指针->成员函数(实例参数)

#### 字符串类string的使用

* C语言不存在字符串类型，都是用字符数组(字符指针)处理字符串
* C++支持字符数组，另外还提供了字符串类：string。使用前必须`#include <string>`
* 使用string定义字符串，无须担心长度、空间等问题，且string重载了大量运算符，实现了大量成员函数，足以满足字符串的日常处理操作。

* 用法
  * 访问字符串中的字符与数组相同，可以连等。
  * 字符串间可以用加号链接
    * `cout<<S1+S2<<endl;`
    * `cout<<S1+=S2<<endl;`
  * 字符串的比较
    * `cout<<(S1<S2)<<endl;`
  * 计算字符串的长度
    * `cout<<S1.length()<<endl`
    * 一个汉字两个长度
  * 字符串交换
    * `S1.swap(S2)`

## 2.3 封装

* C++的封装是通过类类型(简称类)实现的，通过类把具体事物抽象成一个由属性(成员变量)和行为(成员函数)组成的独立单位(即类)。
* 在类的封装设计中，通过访问权限控制类成员访问，
  * 需要隐藏的、内部实现的细节设为私有`private`，仅供内部访问；
  * 允许子类访问的设为保护`protected`
  * 需要对外提供访问接口的设为共有`public`

* 成员函数的简单分类
  * 构造函数和析构函数
    * 构造函数用于对象的创建和初始化
    * 析构函数用于对象的释放
  * 针对成员变量的Set/Get、Add/Del函数
    * 大多数变量往往设为私有，通过共有的Set/Get函数可以访问私有成员
    * 针对数组类型的成员变量，往往有Add/Del函数。
  * 其他功能性函数
    * 与应用程序具体的功能、业务规则有关

通常，成员变量是私有的，对每个成员变量会对应有一对共有的Set/Get函数

## 2.4 this指针

* 类中每个对象的**数据成员**都占用独立空间，但**成员函数**是共享的，可是各个**对象调用相同的函数**时，显示的是对象**各自的信息**。
* `this`是C++中的一个关键字，也是一个**常量指针**，它指向当前对象，通过它可以访问当前对象的所有成员。
* `this`实际上是成员函数的一个**隐式**的形参，在调用成员函数时将对象的地址作为实参传递给`this`。所谓“隐式”，是说它并不出现在代码中，而是在编译阶段由编译器默默地将它添加到参数列表中。
* 三个作用：
  * 如果成员函数的形参与类的成员变量重名，可以用`this`指针解决。
  * 如果成员函数需要返回当前对象，应该写成`return *this;`
  * 可以在成员函数中，以`this`指针为实参，调用其他函数。
* 三点注意事项：
  * `this`只能在成员函数内部使用，用在其他地方没有意义，也是非法的。
  * `this`是指针常量，它的值是不能被修改的，一切企图修改该指针的操作，如复制、递增、递减等都是不允许的。
  * 只有当对象被创建后`this`才有意义，因此不能在`static`成员函数中使用

## 2.5 构造函数

### 2.5.1 自定义构造函数

在C++中，如何**自动进行对象初始化**，并在对象撤销时，**自动执行清理任务**

* 构造函数是类的特殊成员函数，用于初始化对象。
* 构造函数在创建对象时会**自动/隐式**调用。
* C++中的每个类至少要有一个构造函数
* 如果类中没有定义构造函数，系统会提供一个**默认构造函数**。
* 默认构造函数没有参数，也没有函数体，不具有实际的初始化意义。
* 构造函数有严格的接口形式，有四个特点：
  * 与类同名
  * 不能设置返回值类型，void也不写，不能使用return语句返回
  * 可以由参数，可以重载；
  * 一般设为`public`

#### 自定义有参构造函数

* 参数可以由默认值
* 参数默认值写在声明处
* 建议尽量使用初始化表。某些情况下，**必须使用**初始化表进行初始化！
* 常变量、引用必须初始化，所以常成员变量、引用类型的成员变量，只能通过初始化进行初始化！成员对象也需要通过初始化表初始化。

### 2.5.2 重载构造函数

* 函数重载：
  * 同一作用域内
  * 函数名相同
  * 但参数列表不同
* 三点注意：
  * 不以返回值不同来作为重载的条件；
  * 形参变量名不同不意味着参数列表不同；
  * 有参数默认值时，要防止二义性

### 2.5.3 含有成员对象的类的构造函数

* 什么是成员对象？
  * C++允许将一个对象作为另一个类的成员变量，即类中的成员变量可以是其他类的对象，这样的成员变量称为类的子对象或成员对象。
  * 创建含有成员对象的对象时，先执行成员对象的构造函数，再执行类的构造函数。

委托

### 2.5.4 三角形项目的分析与设计

1. 分析
   * 需求分析，开发人员经过深入细致的调研和分析，准确理解用户和项目的功能、性能、可靠性等具体要求，将用户非形式的需求表述转化为完整的希求定义，从而确定系统必须做什么的过程。
   * 在学习过程中，老师就是用户，main函数中的测试代码，以及预期的运行结果就是我们的需求。
2. 设计
   * 要把软件“做什么”转换为“怎么做”。即确定程序是由哪些模块组成的，以及模块之间的关系。
   * 在学习过层中，一个或若干个类就是一个模块。对应UML中的类图，也就是类的.h头文件。
3. 实现
   * 也就是编码的过程。也就是.cpp文件中每个成员函数具体是如何实现的。

#### 分析

1. 能够根据三个顶点的坐标，或者三条边的长度，构造三角形对象
2. 能够按照三个点的坐标显示三角形，其中每个顶点的x、y坐标能用方括号括起来，三个点用花括号括起来
3. 能够计算三角形的面积，如果三条边长不合理，则面积为零。

#### 设计

* 三类成员函数
  * 构造函数/析构函数
  * Set/Get函数
  * 功能函数
* 从调用者的角度来讲，应该把公有成员写在**前面**。但是在编码过程中，**首先**写成员变量。这二者不矛盾！

点类的设计：

```C++
class Point {
  public :
    Point(float xx = 0, float yy = 0);
    float Distance(const Point& other);
    void Show();
    void SetX(float xx);
    void SetY(float yy);
  private :
    float x;
    float y;

}
```

三角形类的设计：

```C++
class Triangle{
  public:
    Triangle(const Point& ppl,const Point& pp2, const Point& pp3);
    Triangle(float a, float b, float c);
    float Area();
    void Show();
  private:
    Point p1;
    Point p2;
    Point p3;
}
```

### 2.5.5 三角形项目的实现  

没听懂这里为什么float不用常引用而正常的要用

### 2.5.6 三角形项目的调试

形参是int类型，实参是float类型，变量赋值转换的时候0.9会被转成0！