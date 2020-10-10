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

