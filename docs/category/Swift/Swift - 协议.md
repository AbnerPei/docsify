# Swift - 协议

协议总是用 **`var`** 关键字来声明变量属性，在类型声明后加上 `{ set get }` 来表示属性是**可读可写**的，加上 `{ get }` 表示属性是**可读**的。

<img src="https://gitee.com/abnerpei/ap_images/raw/master/iOS/Swift/SwiftLearn/Protocol/001.png" style="zoom:50%;" />



如果一个**子类重写了父类的指定构造器**，**并且该构造器满足了某个协议的要求**，那么该构造器的实现需要同时标注 **`required`** 和 **`override`** 修饰符：

<img src="https://gitee.com/abnerpei/ap_images/raw/master/iOS/Swift/SwiftLearn/Protocol/002.png" style="zoom:50%;" />

<img src="https://gitee.com/abnerpei/ap_images/raw/master/iOS/Swift/SwiftLearn/Protocol/003.png" style="zoom:50%;" />