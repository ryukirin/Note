# 西瓜书学习笔记

## 绪论

### 引言

条件→结果

机器学习研究的主要内容是关于计算机上从数据中产生模型（model）的算法，即学习算法（learning algorithm）

### 基本术语

*只解释我自己不明白的

- 数据集data set
- 示例instance/样本sample
- 属性attribute/特征feature
- 属性值attribute value
- 属性空间attribute space/样本空间sample space/输入空间
- 特征向量feature vector：一个样本在属性形成的多维空间中所属于的点的坐标向量
- 维数dimensionality：数据集中属性个数
- 训练数据training data
- 训练样本training set
- 假设hypothesis：数据的某种潜在规律
- 真相/真实ground-truth：某种潜在规律本身
- 学习器learner：模型
- 标签/标记label：训练样本的结果信息
- 标记空间/输出空间label space：所有标记的集合，用$\Gamma$表示
- 样例example：拥有了label的instance，一般用$(x_i,y_i)$表示第i个样例，其中$y_i\in\Gamma$是示例$x_i$的标记
- 泛化generalization：学习得的模型适用于新样本的能力
- 分布distribution：假设样本空间中全体样本全部服从的未知规律，D
- 独立同分布independent and identically distributed（i.i.d）：我们获得的每个样本都是独立地从D上采样获取的

### 假设空间

#### 归纳induction

特殊→一般（泛化）

#### 演绎deduction

一般→特殊（特化）

### 归纳偏好

机器学习算法在学习的过程中对某种类型假设的偏好

原则：奥卡姆剃刀：选最简单的那个

### 习题

#### 1-1

```python
# 表1.1中若只包含编号为1和4的两个样例，试给出相应的版本空间。

import numpy
if __name__ == '__main__':
    # 用16进制表示西瓜的不同种类，共有三种属性，每种属性有三种不同可能情况，故有3*3*3种可能
    # 用二进制表示的话一种属性用00,01和10来表示，由于二进制较长，故转化为16进制表示
    # 其中乌黑：10，青绿：11；稍蜷：10，蜷缩：11：沉闷：10，浊响：11.
    # 下方列表为假设空间
    melon = (0x3f, 0x3d, 0x3e, 0x37, 0x3b, 0x1f, 0x2f, 0x35, 0x36, 0x39, 0x3a, 0x1d, 0x1e, 0x2d,
             0x2e, 0x17, 0x1b, 0x27, 0x2b, 0x15, 0x16, 0x19, 0x1a, 0x25, 0x26, 0x29, 0x2a)
    # 两个样例分别为青绿蜷缩浊响和乌黑稍蜷沉闷
    # 其中前者为正例，后者为反例
    sample = (0x15,0x2a)
    # sum为计数
    sum = 0
    for i in range(0,27):
        # 版本空间：在假设空间中删除与正例不一致的或者与反例一致的假设
        # 即版本空间为和假设空间中反例不一致并且与正例一致的假设
        if( (melon[i] | sample[1] ) != melon[i] and (melon[i] | sample[0]) == melon[i] ):
            sum = sum+1
            print(bin(melon[i]),i+1)
    print(sum)
```

#### 1-2

## 模型评估与选择

### 经验误差与过拟合

错误率：样本个数m中有a个错误样本，则错误率$E=$$a\over m$ ，精度为$1-{a\over m}$ 

误差：预测输出和真实输出之间的差异

经验误差：学习器在训练集上的误差，也称训练误差

过拟合：学习器把训练数据本身特性当成了所有潜在样本的一般特性，导致泛化性不高。

### 评估方法

测试集

- 留出法

  直接将数据集划分为两个互斥的集合

- K折交叉验证

- 自助法

  一个样本在m次采样中始终不被采到的概率为$(1-\frac{1}{m})^m$ 取极限：

  $$\lim_{m \to +\infty}(1-\frac{1}{m})^m=\frac{1}{e} \approx 0.368$$ 

### 验证集

训练集→验证集

​	↑	↓

​	调参

### 性能度量


