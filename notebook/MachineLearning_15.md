## 概率图模型

### 贝叶斯网络

条件独立性：$x_a\perp x_c|x_b$

因子分解: $P(x_1,x_2,\cdots, x_n) = \prod_{i=1}^nP(x_i|x_{pa(i)})$


任意有向图可有下列三种形式组成

1. tail-to-tail, $b \Leftarrow a \Rightarrow c, c\perp b| a$
2. head-to-tail, $a \Rightarrow b \Rightarrow c, a\perp c| b$ 
3. head-to-head, $a \Rightarrow c \Leftarrow b$ ，默认情况下a和b相互独立， 当c被观测到时，a和b不独立。



$$
\text{Bayesian Network}
\begin{cases}
\text{单一: Naive Bayes} \quad P(x|y) = \prod_{i=1}^nP(x_i|y=1)
\\ 
\text{混合: GMM}
\\
\text{时间:}
\begin{cases}
    \text{Markov Chain} \\
    \text{Gaussian Process(无限维高斯分布)}
\end{cases}
\\
\text{连续： Gaussian Bayesian Network}
\end{cases}
$$

$$
\text{动态模型}
\begin{cases}
\text{HMM(离散)}
\\ 
\text{LDS(线性动态系统，Kalman Filter, 连续，线性)}
\\
\text{Particle Filter，非高斯非线性}\end{cases}
$$

