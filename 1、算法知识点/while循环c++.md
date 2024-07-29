# 一、跳出while循环的几种办法

[知乎](https://zhuanlan.zhihu.com/p/163823345)
## 1、break

`break`用于跳出最接近 `break` 的语句；

## 2、continue

`continue` 用于多层嵌套的 while、for 循环语句时，用来忽略循环语句块内位于它后面的代码而继续开始一次新的循环。

## 3、goto

`goto`语句用于将控制转移到由标签标记的语句。

当多层 while、for 循环语句嵌套时， `break` 语句只应用于最里层的语句，如果要穿越多个嵌套层，可以使用 `goto` 语句。

## 4、return

直接跳出。

如果函数没有返回类型，可以直接return，否则，return语句必须返回这个函数类型的值。