# EM 期望最大

## EM 推导

一般情况下极大似然估计MLE可以求得解析解(通过求导)：
$$\theta_{MLE} = \mathop{\arg\max}\limits_{\theta}\log P(x|\theta)$$

EM算法：
$$\theta^{(i+1)} =  \mathop{\arg\max}\limits_{\theta}\int_z \underbrace{\log P(x,z|\theta)}_{E_{z|x,\theta^{(t)}}[\log P(x,z|\theta)]} \cdot P(z|x,\theta^{(i)})$$

EM为迭代算法，下证明迭代收敛性。
$$\begin{aligned} 
\log P(x|\theta) & = \log \frac{P(x,z|\theta)}{P(z|x,\theta)} = \log P(x,z|\theta) - \log P(z|x,\theta) \\
\int_z \log P(x|\theta) \cdot P(z|x,\theta^{(t)}) & = \int_z [\log P(x,z|\theta) - \log P(z|x,\theta)]P(z|x,\theta^{(t)})  \\
\log P(x|\theta) \underbrace{\int_z P(z|x,\theta^{(t)}) dz}_{\text{概率密度函数,积分为1}} & = \underbrace{\int_z P(z|x,\theta^{(t)}) \cdot \log P(x,z|\theta) dz}_{Q(\theta,\theta^{(t)})} - \underbrace{\int_z P(z|x,\theta^{(t)}) \cdot \log P(z|x,\theta) dz}_{H(\theta,\theta^{(t)})}
\end{aligned}$$

其中，$H(\theta,\theta^{(t)})$为KL散度，恒非负。

先求期望，再求最大。

