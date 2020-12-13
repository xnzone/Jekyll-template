---
layout: post 
title: "cpp-显式类型转换"
thumb: /img/in-post/thumbs/cpp.png
category: tech
tags:  "cpp 显式类型转换"
---
# 分类
c++存在四种显式类型转换，分别是
- static_cast 静态转换
- dynamic_cast 动态转换
- const_cast 常量转换
- reinterpret_cast 强制转换

# static_cast
## 简介
任何具有明确定义的类型转换，只要不包含底层const，都可以使用static_cast.如
>int i, j;    
double slope = static_cast<double>(j)/i   

## 使用场景
- 把较大的算术类型赋值给较小的类型时，static_cast非常有用。此情况下一般会损失精度，使用static_cast类型转换后，告警信息就会消失
- 对于编译器无法自动执行的类型转换也非常有用，如可以用static_cast找回存在于void*指针
>void *p = &d;    
double *dp = static_cast<double*>(p);    

转换的结果与原始地址相等，因此必须保证转换后的类型就是指针所指的类型

# dynamic_cast
## 简介
用于将基类的指针或引用安全的转换成派生类的指针活引用
使用形式如下:
>dynamic_cast<type*>(e);    
dynamic_cast<type&>(e);    
dynamic_cast<type&&>(e);    

## 使用场景
- 基类的函数不是虚函数，但是基类的指针需要执行派生类定义的函数时    

假设Base类至少包含一个虚函数，Derived是Base的公有派生类，如果有一个指向Base的指针bp，则我们可以在运行时将其转换成指向Derived的指针，具体代码如下:
>if(Derived *dp = dynamic_cast<Derived*>(bp))    
{    
    //使用dp指向的Derived对象    
}else{    
    //使用bp指向的Base对象    
}

# const_cast
## 简介
const_cast只能改变运算对象底层的const
>const char *pc;    
char *p = const_cast<char*>(pc);   

如果对象本身不是一个常量，使用强制类型转换获得读写权限是合法行为，如果对象是一个常量，再使用const_cast执行读写操作会产生未定义的后果 
## 使用场景
- 用户有函数重载的上下文中

# reinterpret
## 简介
通常为运算对象的位模式提供较低层次上的重新解释

## 使用场景
- 尽量不要使用，使用时必须对涉及的类型和编译器实现转换的过程都非常了解