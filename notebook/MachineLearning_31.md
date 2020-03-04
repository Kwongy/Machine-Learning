## Gaussian Process

高斯过程是定义在连续域上的无限多个高维随机变量所组成的随机过程。

$\{\xi_t\}_{t\in T}$, T： continuous time/space
$\xi_t \sim \text{GP}(\underbrace{m(t)}_{\text{mean function}},\underbrace{k(t,t')}_{\text{covariance function}})$


Model:
$$\begin{cases}
f(x)=\phi(x)^Tw \\
y = f(x) + \epsilon
\end{cases}$$

Bayesian method: prior: $w\sim N(0,\sigma_p)$
$E[f(x)] = E[\phi(x)^Tw] = \phi(x)^TE[w]=0$
$\forall x, x' \in \mathbb{R}^p$
$$\begin{aligned}
Cov(f(x), f(x')) & = E[(f(x)-E[f(x)])((f(x')-E[f(x')])] \\
& = E[f(x)\cdot f(x')] \\
& = E[\phi(x)^Tw \cdot \phi(x')^Tw] \\
& = E[\phi(x)^T w\cdot w^T\phi(x)] \\
& = \phi(x)^T E[w\cdot w^T] \phi(x') \\
& = \underbrace{\phi(x)^T \sigma_p \phi(x')}_{\text{kernel function}}
\end{aligned}$$


weight-space view：
Gaussian process regression = Bayesian linear regression + kernel trick