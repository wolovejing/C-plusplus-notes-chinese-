# C++
C++笔记
## 1.默认初始化
### a.内置类型的变量初始化
如果定义变量时没有指定初始值，则变量被默认初始化。默认值由变量类型和定义变量的位置决定。
* 如果是内置类型的变量未被显示初始化，它的值由定义位置决定。定义于任何函数体外的变量被初始化为0。
```
//不在块中
int i;//正确，i会被值初始化为0，也称为零初始化
```
* 定义于函数体内部的内置类型变量将不被初始化（uninitialized）。一个未被初始化的内置类型变量的值是未定义的，如果试图拷贝或其他形式的访问此类型将引发错误
```
1 {//在一个块中
2 int i;//默认初始化，不可直接使用
3 int j=0;//值初始化
4 j=1;//赋值
5 }
```
### b.类类型的对象初始化
类通过一个或几个特殊的成员函数来控制其对象的初始化过程，这些函数叫做构造函数（constructor）。构造函数的任务是初始化类对象的数据成员。
由编译器提供的构造函数叫（合成的默认构造函数）。
合成的默认构造函数将按照如下规则初始化类的数据成员。
* 如果存在类内初始值（__C++11新特性__），用它来初始化成员。
```
class CC
{
public:
    CC() {}
    ~CC() {}
private:
    int a = 7; // 类内初始化，C++11 可用
}
```
* 否则，没有初始值的成员将被默认初始化。

## 2.C++为类自动提供了下面这些成员函数
* 默认构造函数，如果没有定义构造函数；记得自己定义了构造函数时，编译器不会再提供默认构造函数，记得自己再定义一个默认构造函数。
* 默认析构函数，如果没有定义；用于销毁对象
* 复制（拷贝）构造函数，如果没有定义；用于将一个对象赋值到**新创建**的对象中。用于初始化的过程中，而不是常规的赋值过程
* 赋值运算符，如果没有定义；将已有的对象赋值给另外一个对象时，使用赋值运算符。
* 地址运算符，如果没有定义；
* 移动构造函数(move construtor)，如果没有定义；
* 移动赋值运算符（move assignment operator）。
