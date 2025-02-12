---
title: 'Review of Probability and Statistics'
date: 2024-07-02
permalink: /posts/2024/07/Review of Probability and Statistics/
tags:
  - probability
  - statistics
---

去年保研复习阶段做的一点总结(纯总结，没有细节)


## 大数定律
一般的，若随机变量序列$\{X_n\}$满足：

$$
对于\forall \epsilon>0,有\lim _{n\rightarrow \infty}P(|\frac{1}{n}\sum_{i=1}^nX_i-\frac{1}{n}\sum_{i=1}^nE(X_i)|<\epsilon)=1
$$

则称随机变量序列${X_n}$服从大数定律





### 方差存在的大数定律

#### 伯努利大数定律

设$S_n$为$n$重伯努利实验中事件A发生的次数，p为每次实验中A出现的概率。则对与任意的$\epsilon>0$，有

$$
\lim _{n\rightarrow \infty}P(|\frac{S_n}{n}-p|<\epsilon)=1
$$


上述也可以写成大数定律的一般形式，因为$S_n=\frac{1}{n}\sum_{i=1}^nX_i,p=\frac{1}{n}\sum_{i=1}^nE(X_i)$,其中$X_i$为一系列独立的伯努利分布的随机变量

伯努利大数定律为用**频率估计概率**提供了理论依据

#### 切比雪夫大数定律

设${X_n}$为一系列**两两不相关**的随机变量序列，若每个$X_i$的方差存在，并且有共同的上界，即$Var(X_i)<=c(i=1,2,....)$,则${X_n}$服从上述大数定律

切比雪夫只要求$X_n$两两相关，并且方差有共同上界即可，因此伯努利大数定律是切比雪夫大数定律的**特例**。




#### 马尔科夫（markov）大数定律

在切比雪夫大数定律证明中，我们注意到只要$Var(\frac{1}{n}\sum_{i=1}^nX_i)=\frac{1}{n^2}Var(\sum_{i=1}^nX_i)趋于0即可$，此时$\{X_n\}$服从大数定律。(注意求和在里面，Var在外面)

这里不需要任何随机变量之间的独立，相关性，同分布的假定了，切比雪夫大数定律显然为马尔科夫大数定律的特例。上述条件称为**马尔科夫条件**



### 无方差存在假设的大数定律

若随机变量的方差存在，数学期望一定存在，反之则不一定。上述几个大数定律都假定了方差存在，而下面定律去掉了这一假设。

#### 辛钦大数定律

设${X_n}$为一系列**独立同分布**的随机变量序列，若每个$X_i$的数学期望存在，并且有共同的上界，则${X_n}$服从上述大数定律

辛钦大数定律的证明用到了特征函数，此处不再过多细述。

该多数定律的用途是提供了求一个随机变量的期望$E(X)$的方法。对于一个随机变量，第i次的观测值是$X_i$，则我们可以将$\frac{1}
{n}\sum_{i=1}^nX_i$作为$E(X)$的近似值。

显然，伯努利大数定律也是辛钦大数定律的特例。



## 中心极限定理

大数定律讨论的是什么条件下，**随机变量的序列的算术平均值一概率收敛到其均值的算术平均值**。下面我们来讨论下，什么时候**随机变量的序列的和的分布函数会收敛于正态分布**。



### 独立同分布下的中心极限定理

#### 林德波格-列维中心极限定理

设$\{X_n\}$是**独立同分布**的随机变量序列，且${E(X_i)=\mu_i,Var(X_i)=\sigma^2>0}$存在，若记

$$
Y_n^*=\frac{X_1+X_2+....X_n-n\mu}{\sigma\sqrt{n}},(即Y_n=\frac{1}{n}\sum_{i=1}^nX_i的标准化随机变量)
$$

则对于任意的实数y,有

$$
\lim_{n \to \infty} P(Y_n^*\leq y) = \Phi(y)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^ye^{-\frac{t^2}{2}}dt
$$


#### 棣莫弗-拉普拉斯中心极限定理

设$S_n$为n重伯努利实验中事件A发生的次数，$p$为每次实验中A出现的概率,记

$$
Y_n^*=\frac{S_n-np}{\sqrt{npq}}
$$

则有

$$
\lim_{n \to \infty} P(Y_n^*\leq y) = \Phi(y)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^ye^{-\frac{t^2}{2}}dt
$$
该中心极限定理是历史上第一个中心极限定理，是专门针对二项分布的，因此称为**二项分布的正态近似**

当$p$比较小，二项分布用泊松分布作近似比较好，而$np$较大时，用正态分布近似较好



### 独立不同分布下的中心极限定理

不要求掌握，有林德伯格中心极限定理和李雅普诺夫中心极限定理。



## 统计量及其分布



### 总体和样本

研究对象的全体称为**总体**，每个成员称为个体。为了了解总体分布，从总体抽取n个个体$x_1,x_2,...x_n$,称为总体的一个**样本**,n称为样本容量。其中，在抽取之前，我们无法知道某个个体的取值。因此其值为随机变量。因此我们用大写的$X_1,X_2...X_n$表示样本，小写表示其取值。



### 统计量及其分布

**定义：**设$x_1,x_2....x_n$为来自总体的样本，若样本函数$T(x_1,x_2...x_n)$**不含有任何未知的参数**，则称为T为**统计量**，统计量的分布称为**抽样分布。**



常见统计量：

**样本均值**
$$
\overline{x}=\frac{1}{n}\sum_{i=1}^nx_i
$$
**样本方差**
$$
s_n^2=\frac{1}{n}\sum_{i=1}^n(x_i-\overline{x}^2),
$$
常用$
s^2=\frac{1}{n-1}\sum_{i=1}^n(x_i-\overline{x}^2)$作为方差，也称为无偏方差。其中n-1称为**偏差平方和的自由度**，其含义是：在$\overline{x}$确定后。n个偏差$x_1-\overline{x},x_2-\overline{x}...x_n-\overline{x}$中只有n-1个可以自由变动，而另一个则不能自由取值，这是因为有$\sum_{i=1}^n(x_i-\overline{x})=0$成立



**样本矩**

设$x_1,x_2,...x_k$是一组样本，

$$
a_k=\frac{1}{n}\sum_{i=1}^nx_i^k，称为样本的k阶原点距\\
b_k=\frac{1}{n}\sum_{i=1}^n(x_i-\overline{x})^k称为样本的k阶中心矩
$$

### 三大抽样分布

介绍卡方分布前，先介绍伽马分布

若随机变量的分布函数为：

$$
p(x)= \begin{cases}
\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\lambda x}, &x\ge0 \\
0, &x<0
\end{cases} 
$$

则称$X$服从伽马分布，记作$X$~$Ga(\alpha,\lambda)$.,数学期望和方差分别为$\frac{\alpha}{\lambda}$,和$\frac{\alpha}{\lambda^2}$



**卡方分布**

设随机变量$X_1,X_2,X_3....X_n$独立同分布于标准正态分布$N(0,1)$,则$\chi^2$=$X_1^2+X_2^2....+X_n^2$额分布称为自由度为n的$\chi^2$分布，记作$\chi^2$~$\chi^2(n)$且有 $\chi^2$~$Ga(n/2,1/2)$，$E(X)=n,Var(X)=2n$

关于卡方分布的一个**重要定理**：

设$x_1,x_2,....x_n$是来自正态总体$N(\mu,\sigma^2)$的样本，其样本均值和方差分别为

$$
\overline{x}=\frac{1}{n}\sum_{i=1}^nx_i,\ \ s^2=\frac{1}{n-1}\sum_{i=1}^n(x_i-\overline{x}^2)
$$

则有以下性质成立：

$$
\begin{aligned}
&(1)\ \ \overline{x}与s^2相互独立\\
&(2)\ \ \overline{x} \sim N(\mu,\sigma/n)\\
&(3)\ \ \frac{(n-1)s^2}{\sigma^2}\sim \chi^2(n-1)
\end{aligned}
$$




**F分布**

设随机变量$X_1\sim\chi^2(m),X_2\sim\chi^2(n)$且$X_1,X_2$独立，则称$F=\frac{X_1/m}{X_2/n}$服从自由度为m,n的F分布，记作$F\sim F(m,n)$







**t分布**

设随机变量$X_1$与$X_2$独立，且$X_1\sim N(0,1),X_2\sim\chi^2(n)$,则$t=\frac{X_1}{\sqrt{X_2/n}}$服从自由度为n的t分布，记作$t\sim t(n)$

## 参数估计

参数估计问题就是根据样本构造合适的统计量来对各种参数进行估计。

参数估计分为两种，一种是点估计，一种是区间估计。



### 点估计的概念和无偏性

**定义：**设$x_1,x_2....x_n$是来自总体的一个样本，用于估计未知参数$\theta$的统计量$\hat{\theta}=\hat{\theta}(x_1,x_2.....x_n)$称为$\theta$的**点估计。**，简称**估计**。

**无偏性：** 设$\hat{\theta}=\hat{\theta}(x_1,x_2.....x_n)$是$\theta$的一个估计。$\theta$的参数空间为$H$.若对于任意的$\theta\in H$.有
$$
E_{\theta}(\hat{\theta})=\theta
$$
则称$\hat{\theta}$是$\theta$的一个无偏估计，否则称为有偏估计。

之前的样本均值$\overline {x}$和样本方差$s^2$（除以n-1那个），就是总体均值和方差的偏估计 



#### 矩估计

矩估计的基本思路：

- 用样本矩估计总体矩
- 样本矩的函数估计相应总体矩的函数



方法就是，利用密度函数计算出样本的各种各种矩，$a_1,a_2....a_k$,假设参数$\theta_1,\theta_2.....\theta_k$能表示成$a_1,a_2...a_k$的函数,即$\theta_j=\theta_j(a_1,a_2,...a_k)$。则$\hat{\theta_j}=$$\theta_j(a_1,a_2,...a_k)$,若要估计$\eta=g(\theta_1,\theta_2....\theta_k)$,则$\eta$的矩估计$\hat{\eta}=g(\hat{\theta_1},\hat{\theta_2},...\hat{\theta_k})$



例如，$X\sim U(a,b),E(X)=\frac{a+b}{2},Var(X)=\frac{(b-a)^2}{12}$,则$a=E(X)-\sqrt{3Var(X)},b=E(X)+\sqrt{3Var(X)}$,a,b矩估计分别为
$$
\hat{a}=\overline{x}-\sqrt{3}s,\hat{b}=\overline{x}+\sqrt{3}s
$$




#### 极大似然估计



对于离散情况，似然函数
$$
L(\theta)=P(X_1=x_1,X_2=x_2....,X_k=x_k;\theta)
$$
求最大似然估计就是找$\theta$的估计值$\hat{\theta}=\hat{\theta}(x_1,x_2..x_k)$，使得$L(\theta)$最大

对于连续情况，似然函数
$$
L(\theta)=p(x_1;\theta)p(x_2;\theta).....p(x_k;\theta)
$$
$p(x_i;\theta)$是密度函数，是$\theta$的函数。



### 区间估计
pending...









