## HMM

### Decoding

求解Decoding:$\hat I = \arg\max P(I|O,\lambda)$，采用动态规划的思想。

$\delta_t(i)=\mathop{\max}\limits_{i_1,i_2,\cdot,i_{t-1}} P(O_1,\cdots,O_t, i_1,\cdots,i_{t-1},i_t=q_i)$

$\delta_{t+1}(j) = \mathop{\max}\limits_{i_1,i_2,\cdot,i_{t-1}} P(O_1,\cdots,O_{t+1}, i_1,\cdots,i_{t-1},i_{t+1}=q_j) = \mathop{\max}\limits_{1\leq i\leq N}\delta_t(i)a_{ij}b_j(O_{t+1})$


### Summarize

Task:
$$\begin{cases}
\mathop{\text{Learning:}}\limits^{\lambda\text{未知}} \quad\lambda_{MLE}= \mathop{\arg\max}\limits_{\lambda}P(z|\lambda) \rarr \text{Baum welch Algorithm(EM)}
\\
\mathop{\text{Inference}}\limits_{\lambda\text{已知}} \begin{cases}
\text{Decoding:} \quad z=  \mathop{\arg\max}\limits_{z} P(z|x) \rarr \text{Viterb Algorithm} \\
\text{Prob of evidence:} \quad P(x) \rarr \text{Forward/Backward Algorithm} \\
\mathop{\text{Filtering:}}\limits_{Online} \quad P(z_t|x_1,\cdots,x_t) \rarr \text{Forward Algorithm}\\
\mathop{\text{Smoothing:}}\limits_{Offline} \quad P(z_t|x_1,\cdots,x_T) \rarr \text{Forward-Backward Algorithm} \\
\text{Prediction:} \quad P(z_{t+1}|x_1,\cdots,x_t) \\
\quad\qquad\quad\qquad P(x_{t+1}|x_1,\cdots,x_t) \rarr \text{Forward Algorithm}
\end{cases}\end{cases}$$