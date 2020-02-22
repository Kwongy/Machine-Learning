## Hiddien Markov Model

### Background

Dynamic Model根据状态的不同

$$
\text{state} 
\begin{cases}
\text{离散} \rarr \text{HMM}\\
\text{连续} \begin{cases}\text{线性} \rarr \text{Kalman Filter} \\ \text{非线性} \rarr \text{Particle Filter} \end{cases}
\end{cases}
$$

HMM:

$\lambda=\{\pi,A,B\}$
$\pi:\text{初始prob dist}$
$A:\text{状态转移矩阵}$
$B:\text{发射矩阵}$
观测变量$O:O_1,O_2,\cdots,O_t \rarr V=\{v_1,v_2,\cdots, v_M\}$
状态变量$i:i_1,i_2,\cdots,i_t \rarr Q=\{q_1,q_2,\cdots, q_N\}$
$A=[a_{ij}],a_{ij}=P(i_{t+1}=q_j|i_t=q_i)$
$B=[b_j(k)],b_j(k)=P(O_t=V_k|i_t=q_j)$

两个假设:
1. 齐次Markov假设
2. 观察独立假设

三个问题
1. Evaluation(求值)$\rarr P(O|\lambda)\rarr$前向后向算法
2. Learning(参数估计)$\rarr$ EM
3. Decoding$\rarr I=\arg\max P(I|O)
\begin{cases}
\text{预测} \rarr P(i_{t+1}|O_1,O_2,\cdots,O_t) \\
\text{滤波} \rarr P(i_{t}|O_1,O_2,\cdots,O_t)
\end{cases}$
