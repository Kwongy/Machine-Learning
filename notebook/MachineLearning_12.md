## 概率知识补充

### Exponential family distribution

指数族分布：
$$P(x|\eta) = h(x) \cdot \exp{(\eta^T\phi(x)-A(\eta))}$$

$\eta$:参数向量,$x\in \mathbb{R}^P$, $A(\eta)$：log partition function (log配分函数)，$\phi(x)$：充分统计量

属于指数族分布的有：Gauss, Bernoulli, Beta, Dirichlet, Gamma和泊松分布。

指数族分布的特点： 充分统计量，共轭，最大熵

涉及的模型和方法： 广义线性模型，概率图模型， 变分推断

Gauss分布的指数族分布形式：
$$\begin{aligned}
P(x|\theta) & =\frac{1}{\sqrt{2\pi}\sigma}\exp{-\frac{(x-\mu)^2}{2\sigma^2}} ,\theta = (\mu, \sigma^22) \\
    & = \underbrace{\exp \{ (\frac{\mu}{\sigma^2}-\frac{1}{2\sigma^2}) }_{\eta^T} 
    \underbrace{ \left( \begin{matrix}  x \\ x^2 \end{matrix}\right) }_{\phi(x)} - \underbrace{(\frac{\mu^2}{2\sigma^2}+\frac{1}{2}\log 2\pi\sigma^2) }_{A(\eta)}  \}
\end{aligned}$$

于是，有
$$\eta= \left( \begin{matrix}  \eta_1 \\ \eta_2 \end{matrix}\right) = \left( \begin{matrix}  \frac{\mu}{\sigma^2} \\ -\frac{1}{2\sigma^2} \end{matrix}\right) \Rightarrow  
\begin{cases} \mu = -\frac{\eta_1}{2\eta_2} \\ 
\sigma^2=-\frac{1}{2\eta_2}\end{cases}$$

最终：

$$\eta=\left( \begin{matrix}  \eta_1 \\ \eta_2 \end{matrix}\right), \phi(x)=\left( \begin{matrix}  x \\ x^2 \end{matrix}\right), A(\eta)= -\frac{\eta_1^2}{4\eta_2} + \frac{1}{2}\log{(-\frac{\pi}{\eta_2})}$$

结论：

$A'(\eta)=E_{P(x|\eta)}[\phi(x)], A''(\eta) = Var[\phi(x)]$, $A(\eta)$ is convex funtion.

