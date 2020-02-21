# Variatioanl Inference


## 推导

$x$: observed variable $\rarr X = \{x^{(i)}\}_{i=1}^N$
$z$: latent variable $\rarr Z = \{z^{(i)}\}_{i=1}^N$
$(X,Z)$: complete data
$\theta$: model parameter

$$\log P_\theta(x) = \log\prod_{i=1}^N P_\theta(x^{(i)}) = \sum_{i=1}^N\log P_\theta(x^{(i)})$$
$$\log P_\theta(x^{(i)}) = \underbrace{\text{ELBO}}_{L(q)} + \text{KL}(q||p) \geq L(q)$$

$$\text{ELBO} = E_{q(z)}[\log \frac{P_\theta(x^{(i)},z)}{q(z)}] = E_{q(z)}[\log P_\theta(x^{(i)}, z)] + H[q(z)]$$

$$\text{KL}(q||p) = \int q(z)\log \frac{q(z)}{P_\theta(z|x^{(i)})}dz$$

目标函数:  $\hat q = \mathop{\arg\min}\limits_{q} \text{KL}(q||p) = \mathop{\arg\max L(q)}\limits_{q}$


VI(mean field): $\rarr$ classical VI
Assumption: $q(z) = \prod_{i=1}^Mq_i(z_i)$

$$\begin{aligned}
\log q_j(z_j) & = E_{\prod_{i\neq j}q_i(z_i)}[\log P_\theta(x^{(i)}, z)] + \text{const} \\
& = \int_{q_1}\cdots\int_{q_{j-1}}\int_{q_{j+1}}\cdots   \int_{q_M} q_1\cdots q_{j-1}q_{j+1}\cdots q_M[\log P_\theta (x^{(i)}, z)] dq_1\cdots dq_{j-1}dq_{j+1}\cdots dq_M
\end{aligned}$$