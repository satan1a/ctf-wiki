### 基本栈介绍

栈本身是一种典型的先进后出(First in Last Out)的数据结构，其操作主要有压栈(push)与出栈(pop)两种操作，如下图所示（来自维基百科）。两种操作都是操作栈顶，当然，它也有相应的栈底。

![基本栈操作](/pwn/stackoverflow/figure/Data_stack.png)

在计算机的汇编程序运行过程中，也充分利用了这一数据结构。每个程序都有自己的进程地址空间，进程地址空间中的某一部分就是该程序对应的栈，用于保存函数调用信息和局部变量。此外，常见的操作也同样是压栈与出栈。需要注意的是，与一般我们理解不同的是，**程序的栈是从进程地址空间的高地址向低地址增长的**。

### 函数调用栈

请参考

- [C语言函数调用栈(一)](http://www.cnblogs.com/clover-toeic/p/3755401.html)
- [C语言函数调用栈(二)](http://www.cnblogs.com/clover-toeic/p/3756668.html)

这里，再给另外一张寄存器的图

![](/pwn/stackoverflow/figure/register.png)

需要注意的是，32位程序与64位程序有以下简单的区别

- **x86**
  - **函数参数**在**函数返回地址**的上方
- **x64**
  - x64中前六个参数依次保存在**RDI, RSI, RDX, RCX, R8和 R9寄存器**里，如果还有更多的参数的话才会保存在栈上。
  - 内存地址不能大于0x00007FFFFFFFFFFF，**6个字节长度**，否则会抛出异常。

**参考阅读**

- csapp​
