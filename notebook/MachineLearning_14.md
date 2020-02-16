## 概率图模型

### Overview

$$
\text{概率图}
\begin{cases}
\mathop{\text{Reprensation}}\limits_{\text{表示}}
    \begin{cases} 
        \text{有向图, Bayesian Network} \\
        \text{无向图, Markov Network} 
    \end{cases} \\
\mathop{\text{Inference} }\limits_{\text{推断}}
    \begin{cases} 
        \text{精确推断} \\
        \text{近似推断} 
            \begin{cases}
                \text{精确推断(变分推理)} \\
                \text{随机近似(MCMC)} 
            \end{cases}
    \end{cases} \\
\mathop{\text{Learning} }\limits_{\text{学习}}
\begin{cases} 
    \text{参数学习} 
            \begin{cases}
                \text{完备数据} \\
                \text{隐变量} \Rightarrow EM 
            \end{cases}
            \\
    \text{结构学习} 
\end{cases} 
\end{cases}
$$

概率图模型可有加法法则和乘法法则组成

$$
\begin{cases}
\text{Sum Rule: } P(x_1) = \int P(x_1, x_2) dx_2 \\
\text{Product Rule: } P(x_1,x_2)=P(x_1)\cdot P(x_2|x_1) = P(x_2)\cdot P(x_1|x_2) 
\end{cases} 
$$

$$
\begin{matrix}
\Rightarrow & \text{Chain Rule:} P(x_1,x_2,\cdots,x_n) = \prod_{i=1}^nP(x_i|x_1, x_2, \cdots, x_{i-1}) \\
\Rightarrow & \text{Bayesian Rule:} P(x_2|x_1) = \frac{P(x_1, x_2)}{P(x_1)} = \frac{P(x_1, x_2)}{\int P(x_1,x_2)dx_2} = \frac{P(x_2)P(x_1| x_2)}{\int P(x_2)P(x_1 | x_2)dx_2}
\end{matrix}
$$

遇到的困难是： 维度高，计算复杂， 计算量太大。

因此需要进行简化。

1. 假设各个特征之间相互独立 $\Rightarrow$ Naive Bayes: $P(x|y) = \prod_{i=1}^nP(x_i|y)$
2. Markov properly(HMM,齐次Markov假设) $\Rightarrow$ 条件独立性