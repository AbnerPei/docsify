# 【iOS面试】Runtime

## 你在项目中使用过runtime吗？如果使用了，你是怎么使用的？

## runtime是如何通过selector找到对应的IMP？IMP和SEL的关系是什么？

## 关联对象的原理是什么？
> 通过`runtime`源码可知
>
> * 关联属性并没有添加到category_t（分类）里面；
> * 运行时也不会合并到元类对象里面；
> * 存储在一个全局的AssociationManager里面