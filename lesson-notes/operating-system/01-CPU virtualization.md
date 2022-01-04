## 进程和线程

进程：一个程序的运行实例。

线程：一个共享地址空间的执行流。

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104093600075.png" alt="image-20220104093600075" style="zoom:67%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104093719159.png" alt="image-20220104093719159" style="zoom:50%;" />

## CPU虚拟化

直接在硬件上运行程序可能会带来一些问题：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104094121836.png" alt="image-20220104094121836" style="zoom:67%;" />

所以我们需要限制执行并进行虚拟化。

### 限制操作

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104094243247.png" alt="image-20220104094243247" style="zoom:67%;" />

### 抢占CPU

#### 协作模式

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104094757001.png" alt="image-20220104094757001" style="zoom:67%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104094837711.png" alt="image-20220104094837711" style="zoom:67%;" />

#### 多任务模式

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104095023407.png" alt="image-20220104095023407" style="zoom:67%;" />

进程切换时需要保存的信息：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104095129503.png" alt="image-20220104095129503" style="zoom:67%;" />

### 慢操作

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104095423335.png" alt="image-20220104095423335" style="zoom: 50%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104095511918.png" alt="image-20220104095511918" style="zoom:67%;" />

## 进程创建

创建进程的两种方式：

- 创建一个全新的空进程
- 从现有进程中拷贝，修改其属性

### 创建一个新进程

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104100000067.png" alt="image-20220104100000067" style="zoom:67%;" />

### 拷贝现有进程

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104100018056.png" alt="image-20220104100018056" style="zoom:67%;" />

## 进程调度

- Turaround Time = Completion Time - Arrival Time
- Response Time = First Run Time - Arrival Time

### FIFO

短任务可能会因大任务而等待过长时间：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104100804216.png" alt="image-20220104100804216" style="zoom:67%;" />

### SJF

短任务优先(Short Job First)，解决了长任务带来的堵塞问题，但仍然对不同时间到来的任务无法较好处理：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104101113737.png" alt="image-20220104101113737" style="zoom: 50%;" />

**以上两种调用方式是非抢占式的**

### STCF

最短完成时间优先(Shortest Time-to-Completion First)

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104101344538.png" alt="image-20220104101344538" style="zoom:50%;" />

**FIFO, SJF, STCF的响应时间表现很糟糕**

### RR

轮转调度(Round-Robin)

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104101825971.png" alt="image-20220104101825971" style="zoom:50%;" />

轮转调度在等长任务的调度中的周转时间表现是最差的；

但在不知道任务耗时的情况下，轮转调度给了短任务先完成的机会。

### MLFQ

多级反馈队列(Multi-level Feedback Queue)

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104102827690.png" alt="image-20220104102827690" style="zoom:50%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104102849690.png" alt="image-20220104102849690" style="zoom:50%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104103033612.png" alt="image-20220104103033612" style="zoom:50%;" />

