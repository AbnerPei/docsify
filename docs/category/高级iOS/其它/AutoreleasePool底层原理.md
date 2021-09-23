# AutoreleasePool底层原理

> other images

---
> AutoreleasePool创建是在一个RunLoop事件开始之前(push)，AutoreleasePool释放是在一个RunLoop事件即将结束之前(pop)。

![](https://img-blog.csdnimg.cn/20190418214623329.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly94aW5kaXpoaXlpbjIwMTQuYmxvZy5jc2RuLm5ldA==,size_16,color_FFFFFF,t_70)

> AutoreleasePool并没有单独的结构，而是由若干个AutoreleasePoolPage以双向链表的形式组合而成（分别对应结构中的parent指针和child指针）。

## 参考链接
- [iOS AutoreleasePool 实现原理](https://blog.csdn.net/hanhailong18/article/details/89348510)