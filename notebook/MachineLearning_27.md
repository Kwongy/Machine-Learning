## Linear Dynamic Systeam

### Kalman Filter

Kalman Filter也叫Linear Gaussian Model,它是连续的动态模型

$z_t=A\cdot z_{(t-1)} + B + \epsilon$
$x_t=C\cdot z_{t} + D + \delta$
其中$z_t$与$z_{(t-1)}$成线性关系,$x_t$与$z_t$成线性关系，$\epsilon，\delta$都服从高斯分布

$\epsilon\sim N(0,Q),\delta\sim N(0,R)$
$P(z_t|z_{(t-1)})\sim N(A\cdot z_{(t-1)}+B,Q),P(x_t|z_{t})\sim N(C\cdot z_{t}+D,R)$
$z_1\sim N(\mu_1,\sigma_1)$
$\theta = (A,B,C,D,Q,R,\mu_1,\sigma_1)$

filtering: $P(z_t|x_1,x_2,\cdots,x_t)\rarr$marginal posterior

$$\begin{aligned}
& P(z_t|x_1,x_2,\cdots,x_t) \propto P(x_1,x_2,\cdots,x_t,z_t)\\ 
= &\overbrace{P(x_t|x_1,x_2,\cdots,x_{t-1},z_t)}^{P(x_t|z_t)}\cdot P(x_1,x_2,\cdots,x_{t-1},z_t) \\
= & P(x_t|z_t) \cdot \overbrace{P(z_t|x_1,\cdots,x_{(t-1)}) }^{\text{prediction}}\cdot P(x_1,\cdots,x_{(t-1)}) \\
\propto & P(x_t|z_t) \cdot P(z_t|x_1,\cdots,x_{(t-1)})
\end{aligned}$$

$$\begin{aligned}
& P(z_t|x_1,\cdots,x_{(t-1)}) \\
= & \int_{z_{(t-1)}} P(z_t,z_{(t-1)}|x_1,\cdots,x_{(t-1)})dz_{(t-1)} \\
= & \int_{z_{(t-1)}} \underbrace{P(z_t|z_{(t-1)},x_1,\cdots,x_{(t-1)})}_{P(z_t|z_{(t-1)})} \cdot \underbrace{P(z_{(t-1)}|x_1,\cdots,x_{(t-1)})}_{\text{迭代项}} dz_{(t-1)}
\end{aligned}$$

