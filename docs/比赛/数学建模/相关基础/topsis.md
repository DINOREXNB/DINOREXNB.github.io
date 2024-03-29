## 层次分析的局限
- 决策层不能太多，容易导致判断矩阵和一致矩阵差异可能很大
- 如果决策层的指标的数据是已知的，如何利用数据是的评价更加准确？
## 引例：给考高数的同学打分

- 一个比较好的想法，构造评分的公式
  
$$\frac{x-min}{max-min}\quad max：理论最高分，min：理论最低分$$

- 局限：许多指标不存在理论上的最大值和最小值（例如：GDP增速）
- max改为最高成绩，min改为最低成绩
### 增加指标个数
- 指标类型：
	- 极大性指标（效益型指标）
	- 极小性指标（成本型指标）
### 如何统一指标类型？

#### 极小值指标

指标正向化：$max-x$（将极小型转化为极大型）

#### 中间型指标

$$M=max\{|x_{i}-x_{best}|\}$$

$$x_{i}=1-\frac{|x_{i}-x_{best}|}{M}$$

#### 区间型指标
  
$$M=max\{a-min[x_{i}],max[x_{i}]-b\}$$

$$x_{i}=\begin{cases}1-\frac{a-x}{M}&x<a\\1&a≤x≤b\\1-\frac{x-b}{M}&x>b\end{cases}$$

### 标准化处理

对正向化的矩阵进行标准化处理

$$\left(\begin{matrix}z_{11}&z_{12}&...&z_{1m}\\z_{21}&z_{22}&...&z_{2m}\\z_{31}&z_{32}&...&z_{3m}\\...\end{matrix}\right)$$

将标准化后的矩阵记为A，则A中每个元素
  
$$a_{ij}=\frac{x_{ij}}{\sqrt{\sum_{i=1}^{n}x_{ij}^{2}}}$$

### 计算得分

- 构造计算的公式$\frac{x-min}{max-min}=\frac{x-min}{(max-x)+(x-min)}$
- 可以看作：$\frac{x与最小值的距离}{x与最大值的距离+x与最小值的距离}$

## 基于熵权法的TOPSIS

- 是一种客观赋权方式
- 原理：指标的变异程度越小，所反映的信息量越少，其对应权值越低

### 信息量如何度量？

- 越有可能发生的事情，信息量越少
- 用概率来衡量事情发生的可能性大小
- 使用一个函数构建
  
$$I(x)=-\ln\left(p(x)\right)$$

### 信息熵

- 假设x表示事件X发生的某种情况，p(x)表示这种情况的发生概率，可以定义$I(x)=-\ln{(p(x))}$，因为$0≤p(x)≤1$，所以$I(x)≥0$，如果事件X可能发生的情况分别为$x_{1},x_{2}\dots x_{n}$
- 可以定义事件X的信息熵为

$$H(X)=\sum_{i=1}^{n}\left[p(x_{i})I(x_{i})\right]=-\sum_{i=1}^{n}\left[p(x_{i})\ln(p(x_{i}))\right]$$

> 信息熵本质是对信息量的期望值
> 
> 定理：当所有事件发生可能性相等（所有样本指标相同）时，信息熵越大，最大值为$\ln n$
> 
> 信息熵越大，熵权值越小
### 熵权法计算步骤
- 假设有n个评价对象，m个评价指标（已经正向化）
### 标准化
- 判断矩阵中是否有负数
	- 若没有：使用$z_{ij}=\frac{x_{ij}}{\sqrt{\sum_{i=1}^{n}}{x_{ij}^{2}}}$
	- 若有负数：使用$z_{ij}=\frac{x_{ij}-min\{x_{1j},x_{2j},\dots,x_{nj}\}}{max\{x_{1j},x_{2j},\dots,x_{nj}\}-min\{x_{1j},x_{2j},\dots,x_{nj}\}}$
### 概率计算

$$p_{ij}=\frac{z_{ij}}{\sum_{i=1}^{n}z_{ij}}$$

### 计算信息熵
- 对于第j个指标，计算公式为

$$e_{j}=-\frac{1}{\ln n}\sum_{i=1}^{n}p(x_{i})\ln(p(x_{i}))$$

- 信息效用值$d_j=1-e_{j}$
- 对信息效用值进行归一化得到权重
  
$$W_{i}=\frac{d_{i}}{\sum_{j=1}^{m} d_{j}}(i=1,2\dots,m)$$