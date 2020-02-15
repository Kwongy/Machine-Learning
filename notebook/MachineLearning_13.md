## 概率知识补充

### 最大熵

信息量: $-\log p$
熵：对可能性的一种衡量：
$E_{p(x)}[-\log p]= \int - p(x) \log p(x) dx = -\sum p(x)\log p(x) $

x | 1 | 2 | $\cdots$ | k | 
-|-| - | - | -|
P|$p_1$| $p_2$ | $\cdots$ | $p_k$|
$\sum_{i=1}^kp_i=1$
令$H(p)=-\sum p(x)\log p(x)$

$$\begin{cases}
\max H(p) = \max -\sum p(x)\log p(x) = \min \sum p(x)\log p(x) \\
s.t. \quad \sum_{i=1}^kp_i=1
\end{cases}$$

求 $p$，可使用Lagrange乘数法：
$$\begin{aligned}
L(p, \lambda) & = \sum_{i=1}^k p_i\log p_i + \lambda(1 - \sum_{i=1}^kp_i) \\
\frac{\partial L}{\partial p_i} & = \log p_i + 1 - \lambda = 0 \\
\hat p_i & = \exp(\lambda - 1)
\end{aligned}$$

$\therefore \hat p_1 = \hat p_2 = \cdots = \hat p_k = \frac{1}{k}$

$p(x)$ 是均匀分布

结论： 在没有先验的情况下，熵最大的概率分布为均匀分布。


**在存在先验的情况下，既存在某些约束的情况下求最大熵概率分布**

$\text{Data} = \{{x_1, x_2, \cdots, x_N}\}$, 经验分布：$\hat p(X=x) = \frac{\text{count(x)}}{N}$

由数据和经验分布可求得$E_p[x],Var_p[x]$， 假设$f(x)$是任意关于x的函数$E_{\hat p}[f(x)] = \Delta$， 由上述条件$\Delta$ 可求得， 为已知量。

那么，原问题变为

$$\begin{cases}
 \min \sum p(x)\log p(x) \\
s.t. \quad \sum_{i=1}^kp_i=1， E_p[f(x)] = \Delta
\end{cases}$$

同样， 使用Lagrange乘数法:

$$\begin{aligned}
L(p, \lambda_\theta, \lambda) & = \sum_x p(x)\log p(x) + \lambda_\theta(1 - \sum_xp(x)) + \lambda^T(\Delta - E_p[f(x)]) \\
\frac{\partial L}{\partial p(x)} & = \sum_x(\log p(x)+1) - \sum_x \lambda_\theta - \sum_x \lambda^T f(x) = 0 \\ & \Rightarrow \sum_x(\log p(x) + 1 - \lambda_\theta - \lambda^Tf(x)) = 0  \\
p(x) & = \exp\{ \underbrace{\lambda^T}_{\eta^T}  \underbrace{f(x)}_{\phi(x)} -  \underbrace{(\lambda_\theta + 1)}_{A(\eta)}\}
\end{aligned}$$

因此， 在存在先验的情况下，使得熵最大的概率分布是指数族分布。