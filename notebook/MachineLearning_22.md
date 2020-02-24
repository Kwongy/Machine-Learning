## HMM

### Evaluation

#### Backward Algorithm

记

$\beta_t(i)=P(O_{t+1},\cdots,O_T|i_t=q_i,\lambda)$

$$\begin{aligned}
P(O|\lambda) & = P(O_1,\cdots,O_T|\lambda) \\
& = \sum_{i=1}^N P(O_1,\cdots,O_T|i_t=q_i)\cdot \overbrace{P(i_t=q_i)}^{\pi(i)} \\
& = \sum_{i=1}^NP(O_1|O_2,\cdots,O_T,i_t=q_i)\cdot P(O_1,\cdots,O_T|i_t=q_i)\cdot\pi_i \\
&= \sum_{i=1}^N P(O_1 | i_t=q_i) \cdot \beta_t(i) \cdot \pi_i \\
& = \sum_{i=1}^Nb_i(O_1)\pi_i\beta_t(i)
\end{aligned}$$

推导递推关系

$$\begin{aligned}
\beta_t(i) & =P(O_{t+1},\cdots,O_T|i_t=q_i) \\
& = \sum_{j=1}^N P(O_{t+1},\cdots,O_T,i_{t+1}=q_j|i_t=q_i)  \\
& = \sum_{j=1}^N P(O_{t+1},\cdots,O_T|i_{t+1} =q_j,i_t=q_i)\cdot P(i_{t+1=q_j|i_t=q_i}) \\
& = \sum_{j=1}^N P(O_{t+1},\cdot,O_T|i_{t+1}=q_j) \cdot a_{ij} \\
& = \sum_{j=1}^N \underbrace{P(O_{t+1}|O_{t+1},\cdots,O_T,i_{t+1}=q_j)}_{P(O_{t+1}|i_{t+1}=q_j)} \cdot \underbrace{P(O_{t+1},\cdots,O_T|i_{t+1}=q_j)}_{\beta_{t+1}(j)} \cdot a_{ij} \\
& = \sum_{j=1}^N b_j(O_{t+1}) \cdot a_{ij} \cdot \beta_{t+1}(j)
\end{aligned}$$

#### Summarize

前向后向算法的时间复杂度都为$O(TN^2)$

$\alpha_t(i)=P(O_1,\cdot,O_t,i_t=q_i|\lambda)$
$\beta_t(i)=P(O_{t+1},\cdot,O_T|i_t=q_i,\lambda)$
$\alpha_T(i)=P(O,i_T=q_i|\lambda) \rarr P(O|\lambda) = \sum_{t=1}^N \alpha_T(i)$
$\beta_1(i)=P(O_2,\cdots,O_T|i_t=q_i,\lambda)\rarr P(O|\lambda) = \sum_{i=1}^N\pi_ib_i(O_1)\beta_1(i)$