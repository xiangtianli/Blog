---
  title: js执行上下文，作用域，作用域链
  tags: 
    - 编译
    - javascript
  date: 2020-6-18
  author: 迷
  location: 北京
---
# js执行上下文，作用域，作用域链

## 1.总览

​	js引擎执行过程 分为： 语法分析阶段→ 预编译阶段→ 执行阶段

​	js代码块通过语法分析阶段之后，语法都正确的下回进入预编译阶段。

​		在分析预编译阶段之前，我们先来了解一下js的**运行环境**，运行环境主要由三种：

​			1、全局环境（js代码加载完毕后，进入到预编译也就是进入到全局环境）

​			2、函数环境（函数调用的时候，进入到该函数环境，不同的函数，函数环境不同）

​			3、eval环境（不建议使用，存在安全、性能问题）

每进入到一个不同的运行环境都会创建 一个相应的**执行上下文（execution context）**，那么在一段js程序中一般都会创建多个执行上下文，js引擎会以栈的数据结构对这些执行进行处理，形成**函数调用栈（call stack），**栈底永远是**全局执行上下文（global execution context）**，栈顶则永远时当前的执行上下文。

> 以下涉及到的都是发生在预编译阶段



------



## 2.执行上下文  （运行环境 ）

1. 全局上下文
2. 函数执行上下文
3. eval执行上下文

执行上下文的周期包括三个阶段：创建阶段→执行阶段→回收阶段。

1. 创建阶段（当函数被调用，但未执行任何其内部代码之前）会做以下三件事：
   - 创建变量对象：首先初始化函数的参数arguments，提升函数声明和变量声明。
   - 创建作用域链（闭包）
   - 确定this指向（动态）
2. 执行阶段   执行变量赋值、代码执行
3. 回收阶段     执行上下文出栈等待虚拟机回收执行上下文

## 3.作用域



作用域就是一个独立的地盘，让变量不会外泄、暴露出去。也就是说作用域最大的用处就是隔离变量，不同作用域下同名变量不会有冲突。

1. 全局作用域
2. 函数作用域
3. 块级作用域（let）

## 4.作用域链

当前作用域向父级作用域 (创建该函数的那个父级作用域)寻找，一层一层向上寻找，直到找到全局作用域还是没找到，就宣布放弃。这种一层一层的关系，就是作用域链。

