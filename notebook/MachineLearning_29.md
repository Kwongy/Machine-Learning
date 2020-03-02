## Markov Chain & Monte Carlo

### Monte Carlo Method

采样的动机:

1. 采样本身就是常见的任务
2. 简化求和和求积分任务

采样方法：

1. 基于概率分布采样
2. Adjection Sampling
3. Importance Sampling


Markov chain在某一时刻后，服从平稳分布

Metropolis-Hastings

$u \sim U(0,1)$
$z^*\sim Q(z|z^{t-1})$
$\alpha\sim \min(1,\frac{p(z^*)Q(z^*\rarr z)}{p(z)Q(z\rarr z^*)})$
$\text{if}\quad u\leq \alpha,z^i=z^*,\text{else} \quad z^i=z^{i-1}$

Gibbs采样，它是特殊的MH算法，接受域$\alpha=1$，效率大于MH