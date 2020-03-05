## Conditional Random Field

$\text{HMM} \rarr \text{MEMM} \rarr \text{CRF}$
HMM: 齐次Markov假设，观测独立性假设
MEMM: 打破了观测独立性假设
CRF: 将MEMM改为无向图，同时打破齐次Markov假设和观测独立性假设。


MRF 因子分解：
$$\begin{aligned}
p(x) & = \frac{1}{z}\prod_{i=1}^K\underbrace{\phi_i(\overbrace{x_{c_i}}^{最大团})}_{\text{势函数}} \\
& = \frac{1}{z}\prod_{i=1}^K\exp[\underbrace{-E_i(x_{c_i})}_{\text{能量函数} }] \\
& = \frac{1}{z} \exp\sum_{i=1}^KF_i(x_{c_i})
\end{aligned}$$

CRF PDF:

$$\begin{aligned}
P(Y|X) & = \frac{1}{z}\exp\sum_{i=1}^KF_i(x_{c_i})\\
&=\frac{1}{z}\exp\sum_{t=1}F(y_{t-1},y_t,x_{1:T}) \\
& = \frac{1}{z}\exp\sum_{t=1}^T[\sum_{k=1}^K \lambda_k f_k(y_{t-1},y_t,x_{1:T}) + \sum_{l=1}^L\eta_lg_l(y_t,x_{1:T})]
\end{aligned}$$

其中.$\lambda_k,\eta_l$为参数,$f_k(),g_l()$为特征函数，已知，给定。

Learning问题： parameter estimation
Given training data: $\{(x^{(i)},y^{(i)})\}_{i=1}^N$
$\hat \theta = \arg\max \prod_{i=1}^NP(y^{(i)}|x^{(i)})$

Inference问题: marginal problem：$P(y_t|x)$

Given $P(Y=y|X=x)$求$P(y_t=i|x)$

$$\begin{aligned}
P(y_t=i|x) & = \sum_{y_1\cdots y_{t-1}y_{t+1}\cdots y_T}P(y|x) \\ 
\end{aligned}$$

