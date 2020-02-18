## 概率图模型

### Markov Network

条件独立性：
1. Global Markov Property
    $x_A \perp x_C|x_B$
2. Local Markov Property
    $x_i\perp x_{-i-nb(i)} | x_{nb(i)}$
    $nb(i):$ neigborhour of node $i$
3. Pair Markov Property
    $x_i \perp x_j | x_{-i-j}$


$1\iff 2 \iff 3 \iff \text{因子分解(Hammesley-Clifford定理)}$

因子分解：
$$P(x) = \frac{1}{z} \prod_{i=1}^K\Phi(x_{c_i})$$
$c_i: \text{最大团}$
$x_{c_i}: \text{最大团随机变量集合}$
$\Phi(x): \text{势函数， 必须为正}$
$z = \sum_x \prod_{i=1}^k \Phi (x_{c_i})=\sum_{x_1}\sum_{x_2}\cdots\sum_{x_p}\prod_{i=1}^K\Phi(x_{c_i})$


$P(x)$称为Gibbs Distribution(Boltzman Distribution), $P(x)$可看作指数族分布。


### Inference

Inference就是求概率

边缘概率: $P(x_i) = \sum_{x_1}\sum_{x_2}\cdots\sum_{x_p}P(x)$
条件概率: $P(x_A|x_B), x = x_A \cup x_B$
MAP Inference: $\hat z = \mathop{\arg\max}\limits_{z}P(z|x) \propto \arg\max P(z|x)$



$$
\text{Inference}
\begin{cases}
\text{精确推断}
    \begin{cases} 
        \text{Variable Eliminatation(VE)} \\
        \text{Belief Propagation(BP)} \rarr \text{Sum-Prodcut Algorithm} \\
        \text{Junction Tree Algorithm(普通图结构)} 
    \end{cases} \\
\text{近似推断}     
    \begin{cases} 
        \text{Loop Belief Propagation(有环图)} \\
        \text{Mante Carlo Inference: Importance Sampling, MCMC} \\
        \text{Variational Inference}
    \end{cases} 
\end{cases}
$$
