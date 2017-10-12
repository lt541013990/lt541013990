## Welcome
[TOC]

## 2017-7-15 BIGO
### 1. UTF-8编码与Unicode编码的区别
UTF-8是传出存储规范 Unicode编码是世界通用编码规范


### 2. emoji编码
### 3. AFNetWorking怎么封装的get post请求
### 4. gcd能手动停止队列么
不行，只能暂挂，一般不推荐使用暂挂，如果需要去控制队列建议使用NSOperation
### 5. tcp是通过三次握手来确保数据稳定完整性么
TCP通过数据分段中的序列号保证所有传输的数据可以在接收端按照正常的次序进行重组，而且通过确认保证数据传输的完整性。

三次握手的最主要目的是保证连接是双工的，可靠更多的是通过重传机制来保证的。
### 6. 怎么向sqlite的一个表添加一个字段
alter table info add phone varchar(20);
### 7. 翻转一个单向链表
### 8. view layer关系
1. UIView 继承UIResponder  CALayer继承NSObject   前者能响应事件
2. 每个 UIView 内部都有一个 CALayer 在背后提供内容的绘制和显示，并且 UIView 的尺寸样式都由内部的 Layer 所提供。两者都有树状层级结构，layer 内部有 SubLayers，View 内部有 SubViews.但是 Layer 比 View 多了个AnchorPoint
3. 在 View显示的时候，UIView 做为 Layer 的 CALayerDelegate,View 的显示内容由内部的 CALayer 的 display
4. CALayer 是默认修改属性支持隐式动画的，在给 UIView 的 Layer 做动画的时候，View 作为 Layer 的代理，Layer 通过 actionForLayer:forKey:向 View请求相应的 action(动画行为)
5. layer 内部维护着三分 layer tree,分别是 presentLayer Tree(动画树),modeLayer Tree(模型树), Render Tree (渲染树),在做 iOS动画的时候，我们修改动画的属性，在动画的其实是 Layer 的 presentLayer的属性值,而最终展示在界面上的其实是提供 View的modelLayer
6. 两者最明显的区别是 View可以接受并处理事件，而 Layer 不可以


### 9. 给一个button扩展点击区域怎么实现
重写
``` Objective-C

- (UIView*) hitTest:(CGPoint) point withEvent:(UIEvent*) event
     
- (BOOL)pointInside:(CGPoint)point withEvent:(UIEvent*)event
```
### 10. runloop的什么唤醒，涉及到底层硬件

### 11. 做了方法交换后，运行到这个方法crash了，堆栈给的方法地址是原先的还是交换之后的
交换之后的


### 12. dispatch_barrier的使用场景
dispatch_barrier_async是在前面的任务执行结束后它才执行，而且它后面的任务等它执行完成之后才会执行.

在如下场景：

在访问数据操作时，可以并行读取，因此这种操作应该放到concurrent Dispatch Queue中，写入操作是在任何读取操作执行之前，放到serial Dispatch Queue，在写入处理结束之前，读取处理操作不可进行。

此时使用dispatch_barrier_async和dispatch_group配合可以很好的解决这个问题。

### 13. NSString 进行mutableCopy得到的是可变还是不可变字符串
可变

### 14. 贝塞尔曲线的常用函数 以及 core graphics的常用函数，举例一个饼图的绘制通过这两种方式是怎么来实现的
### 15. NSTimer会遇到哪些问题
### 16. 遇到过NSDate有哪些性能问题么
首先，过度的创建NSDateFormatter用于NSDate与NSString之间转换，会导致App卡顿，打开Profile工具查一下性能，你会发现这种操作占CPU比例是非常高的。据官方说法，创建NSDateFormatter代价是比较高的，如果你使用的非常频繁，那么建议你缓存起来，缓存NSDateFormatter一定能提高效率。
### 17. KVO一般什么场景会去手动触发，会执行两次回调么 为什么
### 18. 分类中通过associateSetObject的属性生命周期是什么样的
个人猜测 和在自己类中创建的属性的生命周期一样

### 19. 堆栈的介绍，对象的处理是在堆还是在栈中

![image](http://img.blog.csdn.net/20141023204049718?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhb3l1YW56aGl5aW5n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

### 20. 怎么创建一个对象 让其存储在栈中
### 21. 怎么利用kvo去监听集合对象的增删改查
### 22. sqlite unique key 与 primary key的区别 与联查效率
### 23. 怎么手动实现一个NSTimmer
