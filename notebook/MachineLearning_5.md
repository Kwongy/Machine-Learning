## 线性分类

### 线性判别分析

$$X=\left(\begin{matrix}x_1^T \\x_2^T  \\\vdots \\x_p^T \end{matrix} \right)_{N \times p}, Y=\left(\begin{matrix}y_1 \\y_2  \\\vdots \\y_N \end{matrix} \right)_{N\times 1}$$

$$\{(x_i, y_i)\}^N_{i=1}, x \in \mathbb{R^p}, y_i\in \{+1,-1\}$$
样本空间内有两类
$$x_{c_1}=\{x_i|y_i=+1\},x_{c_2}=\{x_i|y_i=-1\},|x_{c_1}|=N_1,|x_{c_2}|=N_2,N_1+N_2=N$$


思想: 类内小, 类间大

每一类的均值和方差:
$$\begin{aligned}
    C_k: \bar{z_k} & =\frac{1}{N_k}\sum_{i=1}^{N_k}w^Tx_i \\
               s_k & = \frac{1}{N_k}\sum_{i=1}^{N_k}(w^Tx_i-\bar{z_k})(w^Tx_i-\bar{z_k})^T
\end{aligned}, k=1,2$$

目标函数: $J(w)=\frac{(\bar{z_1} - \bar{z_2})^2}{s_1 + s_2}=\frac{w^T(\bar{x_{c_1}} - \bar{x_{c_2}})(\bar{x_{c_1}} - \bar{x_{c_2}})^Tw}{w^T(s_{c_1}+s_{c_2})w}$

$$\hat w=argmax(J(w))$$

令$s_b=(\bar{x_{c_1}} - \bar{x_{c_2}})(\bar{x_{c_1}} - \bar{x_{c_2}})^T, s_w=(s_{c_1}+s_{c_2})$

$J(w) = w^Ts_bw(w^Ts_ww)^{-1}$

$$\frac{\partial J(w)}{w}=s_bw(w^Ts_ww)^{-1}+w^Ts_bw(-1)(w^Ts_ww)^{-2}s_ww=0$$

$$s_bw(w^Ts_ww) = w^Ts_bws_ww $$
其中$w^Ts_bw, w^Ts_ww$均为$1\times 1$的标量
$$s_ww = \frac{w^Ts_ww}{w^Ts_bw}s_bw $$
$$ w = \frac{w^Ts_ww}{w^Ts_bw}s_w^{-1}s_bw$$

$\therefore w \propto s_w^{-1}s_bw=s_w^{-1}(\bar{x_{c_1}} - \bar{x_{c_2}})(\bar{x_{c_1}} - \bar{x_{c_2}})^Tw$
其中$(\bar{x_{c_1}} - \bar{x_{c_2}})^Tw$为标量

$\therefore w \propto s_w^{-1}(\bar{x_{c_1}} - \bar{x_{c_2}})$