## 线程进程

### 多线程模型

#### 用户态线程(User-Level Threads)

- 完全用户态线程：
  - 所有ULT管理都由应用自己完成
  - 操作系统不知道线程存在
- 线程库：
  - 线程创建和销毁
  - 线程间通信
  - 线程调度
  - 线程上下文save and restore
- 每个进程有自己的线程table
- 追踪线程所有状态

##### 线程状态与进程状态

- 线程2调用一个blocking系统调用：进程被block
- 线程2运行到时间了：进程变为ready
- 线程2请求线程1的运行结果：线程库block线程2，运行线程1

##### ULT的优点

- 线程切换不需要进入内核态进行context switch
- 不同应用可以有不同线程调度
- 可以在任何OS运行

##### ULT的缺点

- 线程系统调用导致被阻塞会使整个进程被阻塞
- 页错误问题：一个线程页错误，其他线程可能还能运行
- 不能利用到CPU多核心的多进程：每次只能运行自己的一个线程

###### Blocking系统调用的解决——Jacketing

- 将阻塞系统调用转为不阻塞的
- 线程调用Jacket而非直接调用系统I/O调用
- Jacket检查I/O是否在被使用
  - 如果是则让这个线程进入Ready状态，调度另一个线程
  - 这个线程重新获得控制时再次检查I/O状态

#### 内核态线程(Kernel-Level Threads)

- 完全内核态线程：所有线程管理由内核完成
- 内核维护进程线程的上下文（进程自己不维护线程表
- 调度在线程尺度上完成

##### KLT的优点

- 在多处理器上同时运行一个进程的多线程
- 一个线程阻塞可以调度同进程的其他线程
- 内核自己可以是多线程的

##### KLT缺点

- 所有可能阻塞线程的调用都以SysCall形式实现
  - 相比ULT，开销高
- 线程间控制权切换需要先有**mode switch**进kernel

#### ULT和KLT的联系

- Many-to-One：多个ULT映射一个kernel线程
- One-to-One：一个用户线程对应一个内核线程
- Many-to-Many：许多ULT对应更少或相同数量KLT

![image-20220105185720508](https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105185720508.png)

## 虚拟内存

### 页表

#### 页表替换策略Clock Policy

![QQ录屏20220106083856](https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/QQ录屏20220106083856.gif)

#### 页表分配：工作集策略

- **Working Set：The set of pages that a process is currently using，进程正在使用的一系列内存页**
- working set $w(\Delta, t)$：在任意时间$t$，进程最近$\Delta$次page reference内被引用过的内存页集合
- 只有working set在主存中（在驻留集）进程才能工作

