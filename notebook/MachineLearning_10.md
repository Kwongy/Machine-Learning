## Dimensionality reduction

### Principal component analysis

思想： 优化问题

* 最小化重构代价
* 最大化投影方差

Data:
$$X=\left(\begin{matrix}x_1^T \\x_2^T  \\ \vdots \\x_p^T \end{matrix} \right)_{N \times p}= \left(\begin{matrix}x_{11} & x_{12} & \cdots & x_{1p} \\x_{21} & x_{22} & \cdots & x_{2p}  \\ \vdots & \vdots & \vdots & \vdots \\x_{n1} & x_{n2} & \cdots & x_{np} \end{matrix} \right)$$

样本均值：
$$Mean: \bar x = \frac{1}{N}\sum_{i=1}^N x_i= \frac{1}{N} X^T 1_N$$
样本方差
$$Covariance： S =  \frac{1}{N}\sum_{i=1}^N(x_i-\bar x)(x_i-\bar x)^T= \frac{1}{N} X^THX$$

其中：
$$1_N=\left(\begin{matrix}1 \\1  \\ \vdots \\1 \end{matrix} \right)_{N \times 1}, H_N=I_N -\frac{1}{N}1_N 1_N^T,H_N = H_N^T,H_N \cdot H_N^T= H_N$$

假设需要求得的方向向量为$u_1$,则最大投影方差为
$$J=\frac{1}{N}\sum_{i=1}^Nu_1^T(x_i - \bar x)(x_i - \bar x)^Tu_1 = u_1^TSu_1$$

$$\begin{cases}
\hat u = argmax(u_1^TSu_1)\\
s.t. \quad \ u_1^Tu_1=1
\end{cases}$$

求$u_1$可使用拉格朗日乘数法

$$L(u_1,\lambda) = u_1^TSu_1 + \lambda(1-u_1^Tu_1)$$
$$\frac{\partial L}{\partial u_1} = 2Su_1-\lambda 2 u_1 = 0 \Rightarrow Su_1=\lambda u_1$$

$\lambda$: eigen-value 特征值
$S$：eigen-vector   特征向量
