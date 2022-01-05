## 线程

### 线程和进程比较

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104163423879.png" alt="image-20220104163423879" style="zoom:67%;" />

## 锁

### 自旋锁

#### Test and Set

利用硬件原语xchg实现：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105081726148.png" alt="image-20220105081726148" style="zoom:67%;" />

#### Compare and Swap

利用硬件原语CompareAndSwap实现

**以上实现存在公平性问题，可能会导致特定线程饥饿**

#### Ticket Locks

引入Ticket，解决饥饿问题：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105082303784.png" alt="image-20220105082303784" style="zoom:67%;" />

自旋锁的性能评价：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105082459941.png" alt="image-20220105082459941" style="zoom:50%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105082554994.png" alt="image-20220105082554994" style="zoom:50%;" />

### 使用队列阻塞时等待

![QQ录屏20220105083103](https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/QQ录屏20220105083103.gif)

与自旋锁的比较：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105085108855.png" alt="image-20220105085108855" style="zoom:67%;" />

### 两阶段锁

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105085315631.png" alt="image-20220105085315631" style="zoom:67%;" />

