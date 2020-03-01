## Particle Filter

### Import Sampling

N个样本$z^{(i)}\sim P(z),i=1,\cdots,N$

$$\begin{aligned}
&E[f(x)] = \int f(z)p(z)dz = \int f(z)\frac{p(z)}{q(z)}q(z)dz \\
= & \frac{1}{N}\sum_{i=1}^Nf(z^{(i)})\underbrace{\frac{p(z)^{(i)}}{q(z)^{(i)}}}_{\text{weight,}w^{(i)}}
\end{aligned}$$

其中$q(z)$为提议分布propsal dist


### Sequential Importance Sampling

$w_t^{(i)}\propto\frac{p(z_{1:t}|x_{1:t})}{q(z_{1:t}|x_{1:t})}$

$$\begin{aligned}
& p(z_{1:t}|x_{1:t}) = \frac{p(z_{1:t},x_{1:t})}{\underbrace{p(x_{1:t})}_{C}}\\
= & \frac{1}{C}\cdotp(z_{1:t},x_{1:t}) \\
= & \frac{1}{C}\cdot p(x_t|z_{1:t},x_{1:t-1})\cdot p(z_{1:t},x_{1:t-1}) \\
= & \frac{1}{C} \cdot p(x_t|z_t)\cdot p(z_{1:t},x_{1:t-1}) \\
= & \frac{1}{C} \cdot p(x_t|z_t)\cdot p(z_{t}|z_{1:t-1},x_{1:t-1})\cdot p(z_{1:t-1},x_{1:t-1}) \\
= & \frac{1}{C} \cdot p(x_t|z_t)\cdot p(z_{t}|z_{1:t-1}) \cdot p(z_{1:t-1},x_{1:t-1}) \\
= & \frac{1}{C} \cdot p(x_t|z_t)\cdot p(z_{t}|z_{1:t-1}) \cdot p(z_{1:t-1}|x_{1:t-1}) \cdot \underbrace{p(x_{1:t-1})}_{D}\\
= & \frac{D}{C}\cdot p(x_{t}|z_t)\cdot p(z_t|z_{t-1})\cdot p(z_{1:t-1}|x_{1:t-1})
\end{aligned}$$

假设:
$q(z_{1:t}|x_{1:t})=q(z_t|z_{1:t-1},x_{1:t})\cdot q(z_{1:t}|x_{1:t-1})$

$$\begin{aligned}
& w_t^{(i)} \propto \frac{p(z_{1:t}|x_{1:t})}{q(z_{1:t}|x_{1:t})} \propto \frac{p(x_t|z_t)\cdot p(z_t|z_{t-1})\cdot p(z_{1:t-1}|x_{1:t-1})}{q(z_t|z_{1:t-1},x_{1:t})\cdot q(z_{1:t-1}|x_{1:t-1})} \\
= & \frac{p(x_t|z_t)\cdot p(z_t|z_{t-1})}{q(z_t|z_{1:t-1},x_{1:t})} \cdot w_{t-1}^{(i)}
\end{aligned}$$