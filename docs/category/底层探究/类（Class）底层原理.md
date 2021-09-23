# 类（Class）底层原理
> other image

---

> **对象的isa指针指向它所在的类**
> 
> **对象所在类的isa指针指向元类**
> 
> **元类的isa指针指向根元类**
> 
> **根元类的isa指针指向了自己**

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0020f2c6932c479a9dfd61d83e58a1d8~tplv-k3u1fbpfcp-zoom-1.image)

```
@interface LGTeacher : LGPerson
@property (nonatomic, copy) NSString *name;

-(void)sayHello;
+(void)sayByby;
@end

```

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ecc5bba0b36e4974b55c0815001848ca~tplv-k3u1fbpfcp-zoom-1.image)

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/347c21e624c84fd7a7b557e0503a93ec~tplv-k3u1fbpfcp-zoom-1.image)

## 参考链接
* **[iOS底层原理之isa走位与类结构分析](https://juejin.cn/post/6872632668438315016)**