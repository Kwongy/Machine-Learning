## Generative Adversarial Network

$P_g(x;\theta_g)$生成数据的分布
$z\sim P_z(z)$  用来逼近上面的$P_g$
鉴别器$G(z;\theta_g)$, $x = G(z;\theta_g)$
$D(x;\theta_d)$ 代表$x$为真的概率

$$\begin{aligned}
P_{data} \rarr \\
z\rarr \text{NN(Generate)} \rarr
\end{aligned} \quad \text{NN(Discriminator)} \rarr \text{Y/N}$$

Aim: 高生成器，高判别器


高生成器:
$\mathop{\max}\limits_{D}\text{E}_{x\sim P_{data}}[\log D(x)] + \text{E}_{z\sim P_z}[\log (1-D(G(z)))]$

高判别器:
$\mathop{\min}\limits_{G}\text{E}_{z\sim P_z}[\log(1-D(G(z)))]$

总目标:
$\mathop{\min}\limits_{G}\mathop{\max}\limits_{D}\text{E}_{x\sim P_{data}}[\log D(x)] + \text{E}_{z\sim P_z}[\log (1-D(G(z)))]$

记$V(D,G)=\text{E}_{x\sim P_{data}}[\log D(x)] + \text{E}_{z\sim P_z}[\log (1-D(G(z)))]$
For fixed $G$, 求$\mathop{\max}\limits_{D}V(D,G)$
$$\begin{aligned}
\mathop{\max}\limits_{D}V(D,G) & = \int P_{data}\log D dx + \int P_g \log(1-D)dx \\
& = \int [P_{data} \log D + P_g\log (1-D)]dx
\end{aligned}$$


$$\begin{aligned}
\frac{\partial}{\partial D}\mathop{\max}\limits_{D}V(D,G) & = \int \frac{\partial}{\partial D}[P_{data} \log D + P_g\log(1-D) ]dx   \\
& = \int[ P_{data} \frac{1}{D} + P_g \frac{-1}{1-D}]dx = 0\\
& \Rightarrow D_G^*=\frac{P_d}{P_d + P_g}
\end{aligned}$$


将$D_G^*$代入，则有
$$\begin{aligned}
& \quad \mathop{\min}\limits_{G}\mathop{\max}\limits_{D} V(G,D)= \mathop{\min}\limits_{G} V(D_G^*,G)\\
& = \mathop{\min}\limits_{G} E_{x\sim P_d}[\log\frac{P_d}{P_d+P_g}] + E_{x\sim P_g}[\log\frac{P_g}{P_d+P_g}] \\
& = \mathop{\min}\limits_{G} \text{KL}(P_d||\frac{P_d+P_g}{2} )+ \text{KL}(P_g || \frac{P_d+P_g}{2}) - \log 4 \geq -\log 4
\end{aligned}$$

当$P_d = \frac{P_d+P_g}{2} = P_g$时， 等号成立。
$P_g^*=P_d, D^*_G = \frac{1}{2}$