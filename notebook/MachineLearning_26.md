## Gaussian Mixture Model

### EM求解

$\theta = \{P_1,P_2,\cdots,P_k,\mu_1,\mu_2,\cdots,\mu_k,\sigma_1,\sigma_2,\cdots,\sigma_k\}$
$x|z=C_k \sim N(x|\mu_k,\sigma_k)$

E-step
$$\begin{aligned}
Q(\theta,\theta^{(i)}) & = \int_z \log P(x,z|\theta)\cdot P(z|x,\theta^{(t)})dz \\
& = \sum_z\log\prod_{i=1}^NP(x_i,z_i|\theta)\prod_{i=1}^NP(z_i|x_i,\theta^{(t)}) \\
& = \sum_{z_1,z_2,\cdots,z_N}\sum_{i=1}^N P(x_i,z_i|\theta) \prod_{i=1}^N P(z_i,x_i|\theta) \\
& =  \sum_{z_1,z_2,\cdots,z_N}[\log P(x_1,z_1|\theta) + \log P(x_2,z_2|\theta) + \cdots + \log P(x_i,z_i|\theta)] \prod_{i=1}^N P(z_i,x_i|\theta) \\
& = \sum_{z_1}\log P(x_1,z_1|\theta) \cdot P(z_1|x_1,\theta^{(t)}) +\cdots + \sum_{z_N}\log P(x_N,z_N|\theta) \cdot P(z_N|x_N,\theta^{(t)}) \\
& = \sum_{i=1}^N\sum_{z_i}\log P(x_i,z_i|\theta)\cdot P(z_i|x_i,\theta^{(t)}) \\
& = \sum_{i=1}^N\sum_{z_i}\log P_{z_i}N(x_i|\mu_{z_i},\sigma_{z_i})\cdot \frac{P_{z_i}N(x_i|\mu_{z_i},\sigma_{z_i})}{\sum_{k=1}^KP_{k}N(x_i|\mu_{k},\sigma_{k})}
\end{aligned}$$

Q-step

$$\begin{aligned}
\theta^{(t+1)}& =\mathop{\arg\max}\limits_{\theta}Q(\theta,\theta^{(t)}) \\
& = \mathop{\arg\max}\limits_{\theta}\sum_{k=1}^K\sum_{i=1}^N[\log P_k + \log N(x_i|\mu_k,\sigma_k)]P(z_i=C_k|x_i,\theta^{(t)})
\end{aligned}$$


$P^{(t+1)}=(P_1^{(t+1)},P_2^{(t+1)},\cdots,P_k^{(t+1)})$

$$\begin{cases} 
\mathop{\max}\limits_{P}\sum_{i=1}^k\sum_{i=1}^N\log P_k P(z_i=C_k|x_i,\theta^{(t)}) \\
s.t. \quad \sum_{k=1}^K P_k=1
\end{cases}$$
使用Lagrange乘数法求解
$L(P,\lambda) = \sum_{k=1}^K\sum_{i=1}^N\log P_kP(z_i=C_k|x_i,\theta^{(t)} +\lambda(\sum_{k=1}^KP_k-1))$
$$\begin{aligned}
\frac{\partial L}{\partial P_k} & = sum_{i=1}^N\frac{1}{P_k}\cdot P(z_i=C_k|x_i,\theta^{(i)}) + \lambda =0 \\
& \Rightarrow \sum_{i=1}^NP(z_i=C_k|x_i,\theta^{(t)}) + P_k\lambda = 0 \\
& \Rightarrow \sum_{i=1}^N \underbrace{\sum_{k=1}^KP(z_i=C_k|x_i,\theta^{(t)})}_{\text{相当于密度函数积分，为1}} + \underbrace{\sum_{k=1}^KP_k}_{\text{已知条件,为1}}\lambda = 0 \\
& \Rightarrow N + \lambda = 0 \Rightarrow \lambda = -N \\
& \Rightarrow P_k^{(t+1)} = \frac{1}{N}\sum_{i=1}^NP(z_i=C_k|x_i,\theta^{(t)})
\end{aligned}$$