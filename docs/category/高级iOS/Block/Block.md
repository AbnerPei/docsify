#【iOS面试】Block

## 什么是Block❓

##Block的分类
- 全局block
- 栈block
- 堆block

> 在 MRC下:只要没有访问外部变量，就是全局block。访问了外部变量，就是栈block。显示地调用[block copy]就是堆block。
> 
> 在 ARC下:只要没有访问外部变量，就是全局block。如果访问了外部变量，那么在访问外部变量之前存储在栈区，访问外部变量之后存储在堆区。
> > 笔记链接：[iOS面试珠玑](https://juejin.cn/post/6844903615157501965)

## `__block`

## 1、block为什么要用copy❓
> block创建时，默认分配内存在栈上，不在堆上。