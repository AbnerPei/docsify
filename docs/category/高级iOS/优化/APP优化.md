# APP优化

## 启动优化
- 冷启动（Cold Lanuch）
- 热启动（Hot Lanuch）

### 冷启动
冷启动可以概括为以下3个阶段：

1. dyld
2. runtime
3. main

#### dyld
**dyld**（dynamic link editor），Apple的动态连接器，可以用来装载Mach-O文件（可执行文件、动态库等）

启动APP时，dyld所做的事情有：

- **装载APP的可执行文件，同时会递归加载所有依赖的动态库**
- **当（dyld）把可执行文件、动态库都装载完毕后，会通知runtime进行下一步处理**

#### runtime

启动APP时，runtime所做的事情有：
- 调用map_images进行可执行文件内容的解析和处理
- 在load_images中调用call_load_methods，调用所有Class和Category的+load方法
- 进行各种objc结构的初始化（注册Objc类、初始化类对象等等）
- 调用C++静态初始化器和`__attribute__((constructor))`修饰的函数

到此为止，可执行文件和动态库所有的符号(Class、Protocol、Selector、IMP，...)都已经按格式成功加载到内存中，被runtime所管理。

#### main

- APP的启动是由dyld主导，将可执行文件加载到内存，顺便加载所有依赖的动态库
- 并由runtime负责加载成objc定义的结构
- 所以初始化工作结束后，dyld就会调用main函数
- 接下来就是UIApplicationMain函数，AppDelegate的application: didFinishLaunchingWithOptions:方法

#### APP启动优化
dyld：

- 减少动态库、合并一些动态库、定期清理不必要的动态库
- 减少Objc类、分类的数量、减少Selector数量、定期清理不必要的类、分类
- 减少C++虚函数数量
- Swift尽量使用struct

runtime:
- 用+initialize方法和dispatch_once取代所有`__attribute__((constructor))`、C++静态构造器、Objcc的+load

main:
- 在不影响用户体验的前提下，尽可能将一些操作延迟，不要全部放在didFinishLaunchingWithOptions方法中（按需加载）

### 热启动

## 安装包瘦身
 安装包（IPA）主要有可执行文件 、 资源组成
 
 资源：
 - 采取无损压缩
 - 去除没用的资源

 可执行文件瘦身：
 - 编译器优化（新版Xcode已经处理了）

 其它：
 - 利用AppCode检测未使用的代码
 - 编写LLVM插件检测出重复代码、未被调用的代码

 ### LinkMap
 生成LinkMap文件，可以查看可执行文件的具体组成
 可借助第三方工具解析LinkMap文件：huanxsd/LinkMap
 
 
 ## 参考链接
 - [iOS性能优化](https://www.jianshu.com/p/4e9c6a048f6f)
 - [iOS App 启动性能优化](https://mp.weixin.qq.com/s/Kf3EbDIUuf0aWVT-UCEmbA)
 


