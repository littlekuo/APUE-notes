# UNIX标准及实现

## UNIX标准化
1.ISO C：意图是提供C程序的可移植性，使得它能够适合于大量不同的操作系统，而不只是UNIX操作系统。
  * 该标准不仅定义了C程序设计语言的语法和语义，还定义了标准库，因而十分重要。

  
2.POSIX(Portable Operating System Interface): 可移植操作系统接口。该标准的目的是提升应用程序在各种UNIX系统环境之间的可移植性。它定义了“符合POSIX”的操作系统必须提供的各种服务。  
3.SUS(Single Unix Specification)：POSIX 标准的一个超集，其定义了一些附加接口扩展了 POSIX 规范提供的功能。

## UNIX系统实现
> SVR4(UNIX System V Release 4)  
> 4.4 BSD(Berkeley Software Distribution)  
> FreeBSD  
> Linux  
> Mac OS X  
> Solaris

## 标准与实现的关系

### 限制
1.UNIX 系统的实现定义了很多magic number和常量。有两种类型的限制是必须的。
  * 编译时限制，如 short int 最大值是多少
  * 运行时限制，如文件名最长多少个字符

通常编译时限制可以在头文件中定义；运行时限制则要求进程调用一个函数获得限制值。

2.某些限制在一个 UNIX 实现中可能是固定的（由头文件定义），在另一个 UNIX 实现中可能是动态的（需要由进程调用一个函数获得限制值）。如文件名的最大字符数在不同的操作系统中提供了三种限制：
  * 编译时限制（由头文件给定）
  * 与文件或者目录无关的运行时限制（由 sysconf函数给定）
  * 与文件或者目录相关的运行时限制（由 pathconf函数以及fpathconf函数给定）

  
3.ISO C 限制：ISO C 所有编译时限制都在头文件 <limits.h> 中。  
4.POSIX 限制：POSIX定义了很多涉及操作系统实现限制的常量。其中某些常量可能定义在<limits.h>中，其余的则按具体条件可定义或者可不定义。

5.运行时限制：
  







