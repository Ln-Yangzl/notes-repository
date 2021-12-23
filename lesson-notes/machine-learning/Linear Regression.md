# 线性回归模型

## 机器学习基础

### 机器学习常规组成部分

![image-20211223145759632](https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223145759632.png)

### 监督学习

![image-20211223145855856](https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223145855856.png)

## 多项式拟合

### 映射函数

$$
y(x,w)=w_0+w_1x+w_2x+...+w_mx^m=\sum_{j=0}^{m}w_jx^j
$$

对x而言是非线性函数

对w而言是线性函数

**对于此类（对未知参数而言的）线性函数，被称为线性回归模型**

### 目标函数

$$
\text{Min}\ E(w)=\frac{1}{2}\sum_{n=1}^{N}(y(x_n,w)-t_n)^2
$$

在高斯分布下，均方误差就是最大似然法求解w

### 正则化

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223151417863.png" alt="image-20211223151417863" style="zoom:50%;" />

## 线性回归模型

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223152300545.png" alt="image-20211223152300545" style="zoom:50%;" />

对输入进行非线性映射：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223152518686.png" alt="image-20211223152518686" style="zoom:50%;" />

损失函数：

<img src="https://ln-markdown-image-bucket.oss-cn-beijing.aliyuncs.com/img/image-20211223152738814.png" alt="image-20211223152738814" style="zoom:50%;" />

