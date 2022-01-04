## 内存共享

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104104111803.png" alt="image-20220104104111803" style="zoom:50%;" />

### 分时共享

与CPU虚拟化类似，效率低下。

### 静态重定位

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104104625470.png" alt="image-20220104104625470" style="zoom: 67%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104104704930.png" alt="image-20220104104704930" style="zoom:50%;" />

缺点：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104104732263.png" alt="image-20220104104732263" style="zoom:50%;" />

### 动态重定位

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104104910351.png" alt="image-20220104104910351" style="zoom:50%;" />

两种操作模式：

- 保护模式（OS运行状态，可访问所有内存空间）
- 用户模式（用户程序运行状态，通过虚拟地址访问物理地址）

### 分段(Segmentation)

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104105454544.png" alt="image-20220104105454544" style="zoom:67%;" />

#### 实现示例

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104105643560.png" alt="image-20220104105643560" style="zoom:67%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104105653982.png" alt="image-20220104105653982" style="zoom:50%;" />

#### 分段优点

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220104110059255.png" alt="image-20220104110059255" style="zoom:67%;" />

