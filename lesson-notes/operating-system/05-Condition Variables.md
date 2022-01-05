## 条件变量

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105085849176.png" alt="image-20220105085849176" style="zoom:67%;" />

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105090132619.png" alt="image-20220105090132619" style="zoom:50%;" />

## 生产者消费者模型

### 单条件变量

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105090716718.png" alt="image-20220105090716718" style="zoom:50%;" />

> 注意：如果使用if而非while会导致竞争问题

此时仍然存在唤醒线程问题，最后一个`signal`需要唤醒生产者才正确，否则可能会带来较多性能损耗。

### 双条件变量

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20220105091145667.png" alt="image-20220105091145667" style="zoom: 50%;" />

