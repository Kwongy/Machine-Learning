## Support vector machine

### hard-margin svm

Data: $\{(x_i, y_i)\}_{i=1}^N, x_i \in \mathbb{R}^P, y_i \in \{+1, -1\}$

带约束的SVM

$$\begin{cases} \mathop{\min}\limits_{w, b}\frac{1}{2}w^Tw \\ s.t. \quad 
\mathop{y_i(w^Tx_i+b) \geq 1}\limits_{\text{for i =1,2,...,N} } \iff 1-y_i(w^Tx_i+b) \leq 0 \end{cases}  $$

Lagrange乘数法求w,b：
$$L(w,b,\lambda)=\frac{1}{2}w^Tw+\sum_{i=1}^N\lambda_i(1-y_i(w^Tx_i+b))$$


无约束的SVM

$$\begin{cases} \mathop{\min}\limits_{w, b}\mathop{\max}\limits_{\lambda} L(w,b,\lambda) \\ s.t. \quad 
\lambda_i \geq 0 \end{cases}  $$

(强对偶关系得到)无约束SVM对偶问题

$$\begin{cases} \mathop{\max}\limits_{\lambda}\mathop{\min}\limits_{w, b} L(w,b,\lambda) \\ s.t. \quad 
\lambda_i \geq 0 \end{cases}  $$

求解 $\min L(w,b,\lambda)$


$$\begin{cases} \frac{\partial L}{\partial b} = 0 \Rightarrow b=\sum_{i=1}^N\lambda_iy_i=0
 \\ \frac{\partial L}{\partial w} = 0 \Rightarrow w = \sum_{i=1}^N\lambda_iy_ix_i=0 \end{cases}  $$

等价于

$$\begin{cases} \mathop{\min}\limits_{\lambda} \frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N\lambda_i\lambda_jy_iy_jx_i^Tx_j-\sum_{i=1}^N\lambda_i
 \\ s.t. \quad \lambda_i \geq 0,  \sum_{i=1}^N \lambda_iy_i = 0\end{cases}  $$

原，对偶问题具有强对偶关系 $\iff$ 满足KTT条件

KTT条件：
$$
\begin{cases}
 \frac{\partial L}{\partial w} = 0, \frac{\partial L}{\partial b} = 0,  \frac{\partial L}{\partial \lambda} = 0 \\
\lambda_i (1-y_i(w^Tx_i+b)) = 0 \\
\lambda_i \geq 0 \\
 1-y_i(w^Tx_i+b) \leq 0
\end{cases}
$$

解得
$$w^*=\sum_{i=1}^N\lambda_iy_ix_i $$

$$b^*=y_k-\sum_{i=1}^N\lambda_iy_ix_i^Tx_k $$
$$f(x) = \text{sign}({w^*}^Tx + b^*)$$