# KVO

## KVO总结

* KVO在监听属性后，runtime会根据对象的类型生成一个`NSKVONotifying_XXX`（XXX是原来的类）的派生类，该派生类NSKVONotifying_XXX继承于原来的类

* NSKVONotifying_XXX重写被监听属性的setter方法，但是赋值的时候通过重写的setter内部消息转发还是通过原来类的setter方法来实现

* KVO在移除监听时将isa指针指向地址由NSKVONotifying_XXX派生类重新指向原来类

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/417e76ff86204f9f86407ead7c4e01c1~tplv-k3u1fbpfcp-watermark.image)

> 在进行KVO监听后，对象的class即isa指向发生了改变，由IFPerson变成了NSKVONotifying_IFPerson，但是对象的地址没有改变。

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be8c694780454bcb91b13338edcb1cce~tplv-k3u1fbpfcp-watermark.image)


![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3848de411f704d8fa3d6de035a0277c6~tplv-k3u1fbpfcp-watermark.image)

从打印监听前后方法列表我们可以看到NSKVONotifying_IFPerson类有如下变化:

* 重写了被监听属性的setter方法，如setName:

* 修改了isa指针指向的地址，由原来的IFPerson指向了NSKVONotifying_IFPerson

* 实现了dealloc方法

* 增加了一个_isKOA标识符

#### 何时重新指向IFPerson呢？答案是在移除监听的时候。
![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d099ef2b75ff4b42b346290e5992b094~tplv-k3u1fbpfcp-watermark.image)