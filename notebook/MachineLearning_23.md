## HMM


### Learning


Learning问题就是求参数，HMM中的参数有

$\pi$：初始概率分布
$A:[a_{ij}] \rarr a_{ij} = P(i_{t+1}=q_j|i_t=q_i)$：转移矩阵
$B:[b_j(k)] \rarr b_j(k)=P(O_t=V_k|i_t=q_j)$: 发射矩阵
$\lambda = (\pi,A,B)$

用EM算法求解$\lambda$

$$\begin{aligned}
\theta^{(t+1)} & = \mathop{\arg\max}\limits_{\theta}\int_z\log P(x,z|\theta)\cdot P(z|x,\theta^{(t)})dz \\
\lambda^{(t+1)} & = \mathop{\arg\max}\limits_{\lambda}\sum_I\log P(O,I|\lambda)\cdot P(O,I|\lambda^{(t)})
\end{aligned}$$

$\lambda^{(t)}=(\pi^{(t)},A^{(t)},B^{(t)})$
$$\begin{aligned}
Q(\lambda,\lambda^{(t)})& =\sum_I\log P(O,I|\lambda)\cdot P(O,I|\lambda^{(t)}) \\
& = \sum_I\{[\log\pi_{i1}+\sum_{i=2}^T\log a_{i_{t+1},i_t}+\sum_{i=1}^T\log b_{it}(O_t)]\cdot P(O,I|\lambda^{(t)})\} 
\end{aligned}$$

$$\begin{aligned} 
\pi^{(t+1)} & = \mathop{\arg\max}\limits_{\pi}Q(\lambda,\lambda^{(t)}) \\
& = \mathop{\arg\max}\limits_{\pi} \sum_I[\log \pi_{i1}\cdot P(O,I|\lambda^{{(t)}})] \\
& = \mathop{\arg\max}\limits_{\pi} \sum_{i_1}\cdots\sum_{i_T}[\log \pi_{i1}\cdot P(O,i_1,\cdots,i_T|\lambda^{{(t)}})] \\
& =  \mathop{\arg\max}\limits_{\pi} \sum_{i=1}^N[\log \pi_{i}\cdot P(O,i_1=q_i|\lambda^{{(t)}})]\text{,s.t.}  \sum_{i=1}^N \pi_i=1
\end{aligned}$$

Lagrange乘数法：
$$L(\pi,\eta) = \sum_{i=1}^N\log\pi_i P(O,i_1=q_i|\lambda^{(i)})+\eta (\sum_{i=1}^N\pi_i-1)$$

$$\begin{aligned}
& \frac{\partial L}{\partial \pi_i} = \frac{1}{\pi_i}P(O,i_1=q_i|\lambda^{(t)}) +\eta = 0 \\
& \Rightarrow \sum_{i=1}^N[P(O, i_1=q_i|\lambda^{(t)})+\pi_i\eta=0] \\
& \Rightarrow P(O|\lambda^{(t)}) + \eta = 0 \\
& \Rightarrow \eta = -P(O|\lambda^{(t)}) \\
& \Rightarrow \pi_i^{(t+1)} = \frac{P(O,i_1=p_i|\lambda^{(t)})}{P(O|\lambda^{(t)})}
\end{aligned}$$