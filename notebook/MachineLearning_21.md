## HMM

### Evaluation

Give $\lambda$ ,求$P(O|\lambda)$

$$P(O|\lambda) = \sum_IP(I,O|\lambda) = \sum_IP(O|I,\lambda)\cdot P(I|\lambda)$$

$\because P(I|\lambda) = P(i_1,\cdots,i_t|\lambda) = P(i_1,i_2,\cdots,i_{t-1},\lambda) = \pi(a_{i1})\cdot \prod_{t=2}^Ta_{i_{t-1}.i_t},P(O|I,\lambda)=\prod_{t=1}^Tb_{it}(O_t)$
$\therefore P(O|\lambda) = \sum_I\pi(a_{i1})\cdot \underbrace{\prod_{t=2}^Ta_{i_{t-1}.i_t}}_{\text{齐次Markov假设}}\prod_{t=1}^Tb_{it}(O_t)$
$=\overbrace{\sum_{i_1}\sum_{i_2}\cdots\sum_{i_T}}^{O(N^T)}\cdot\pi(a_{i1})\prod_{t=2}^Ta_{i_{t-1},i_t}\prod_{t=1}^Tb_{i1}(O_t)$


计算量为$O(N^T)$，很难求。

#### 前向算法Forward Algorithm

记
$$\alpha_t(i) = P(O_1,\cdots,O_t,i_t=q_i|\lambda),\alpha_T(i) = P(O,i_t=q_i|\lambda)$$
则$P(O|\lambda) = \sum_{i=1}^NP(O,i_t=q_i|\lambda) = \sum_{i=1}^N\alpha_T(i)$

$$\begin{aligned}
\alpha_{t+1}(j) & = P(O_1,\cdots,O_t,O_{t+1},i_{t+1}=q_j|\lambda) \\
& = \sum_{i=1}^N P(O_1,\cdots,O_t,O_{t+1},i_{t+1}=q_j,i_t=q_i|\lambda) \\
& =  \sum_{i=1}^N P(O_{t+1}|O_1\cdots,O_t,i_{t+1}=q_j,i_t=q_i,\lambda) \cdot P(O_1,\cdots,O_t,i_t=q_i,i_{t+1}=q_j|\lambda) \\
& = \sum_{i=1}^N P(O_{t+1}|i_{t+1}=q_j)\cdot P(O_1,\cdots,O_t,i_t=q_i,i_{t+1}=q_j) \\
& = \sum_{i=1}^N P(O_{t+1}|i_{t+1}=q_j)\cdot P(i_{t+1}=q_j|O_1,\cdots,O_t,i_t=q_i,\lambda)\cdot P(O_1,\cdots,O_t,i_t=q_i|\lambda) \\
& = \sum_{i=1}^N \underbrace{P(O_{t+1}|i_{t+1})}_{b_j(O_{t+1})}\cdot \underbrace{P(i_{t+1}=q_j|i_t=q_i,\lambda)}_{a_{ij}}\cdot \underbrace{\alpha_t(i)}_{\text{递推项}}
\end{aligned}$$
