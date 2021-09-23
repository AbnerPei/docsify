# CTMediator

![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/001.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/002.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/003.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/004.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/005.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/006.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/007.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/008.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/009.png)

![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/010.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/011.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/012.png)
![](https://gitee.com/abnerpei/ap_images/raw/master/iOS/OpenSourceLibs/CTMediator/013.png)

> **既然用runtime就可以解耦取消依赖，那还要`Mediator`做什么？**
> 
> 1. 调用者写起来很恶心，代码提示都没有，每次调用写一坨。
> 
> 2. runtime方法的参数个数和类型限制，导致只能每个接口都统一传一个 NSDictionary。这个 NSDictionary里的key value是什么不明确，需要找个地方写文档说明和查看。
> 
> 3. 编译器层面不依赖其他组件，实际上还是依赖了，直接在这里调用，没有引入调用的组件时就挂了。

> 使用`Mediator`后
>
> 1. 调用者写起来不恶心，代码提示也有了。
> 
> 2. 参数类型和个数无限制，由 Mediator 去转就行了，组件提供的还是一个 NSDictionary 参数的接口，但在Mediator 里可以提供任意类型和个数的参数，像上面的例子显式要求参数 NSString *bookId 和 NSInteger type。
> 3. Mediator可以做统一处理，**==调用某个组件方法时如果某个组件不存在，可以做相应操作==**，让调用者与组件间没有耦合。

> 总结起来就是，**==组件通过中间件通信，中间件通过 runtime 接口解耦，通过 target-action 简化写法，通过 category 感官上分离组件接口代码。==**
> 
> 
## 参考链接
- [iOS 组件化方案探索](http://blog.cnbang.net/tech/3080/)
- [iOS 组件间方案 -- MGJRouter& CTMediator](https://www.jianshu.com/p/ccaa2b0ac440)