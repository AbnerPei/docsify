# alloc、init、new底层原理
> other_images

## alloc
![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ba48609d6511428f8d9653e1761727c0~tplv-k3u1fbpfcp-zoom-1.image)

> calloc: 开辟内存
> 
> initInstanceIsa：将内存跟类关联

## init
> init方法是工厂方法，它没有实际的意义，主要是为了方便我们自定义初始化方法的，比如定义initWithXXX的方法

## new
![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5ca61a93c46c4a7b885186c72e725489~tplv-k3u1fbpfcp-zoom-1.image)

### new能一步到位，那为什么它却使用的很少？

原因有两点：

1、因为new能一步到位，但它只能init，而alloc init却有更多五花八门又实用或者定制的初始化方法。

2、alloc ,init分配的内存会和相关联的对象在内存地址中相靠近，利于内存读取,调用时消耗很少的内存，提升了程序处理速度

## 参考链接
* **[iOS底层之alloc探索](https://juejin.cn/post/6870377657910394888)**
* **[【IOS】关于alloc 、init和new，你真懂了吗？](https://blog.csdn.net/qq_36793206/article/details/81106064)**