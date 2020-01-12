## 线性回归

### 最小二乘法

$$D=\{(x_1, y_1), (x_1, y_1), \cdots, (x_N, y_N)\}, x_i \in \mathbb{R^p}, y_i \in \mathbb{R^p}$$

$$X = (x_1, x_2, \cdots, x_N)^T = \left(\begin{matrix}x_1^T \\ x_2^T  \\ \vdots \\ x_p^T \end{matrix} \right)=\left(\begin{matrix}
   x_{11} & x_{12} & \cdots & x_{1p}\\
   x_{21} & x_{22} & \cdots & x_{2p}  \\
   \vdots & \vdots & \ddots & \vdots \\
    x_{n1} & x_{n2} & \cdots & x_{np} \end{matrix} \right), Y = \left(\begin{matrix}y_1^T \\ y_2^T  \\ \vdots \\ y_p^T \end{matrix} \right)$$

最小二乘估计, 损失为:
$$\begin{aligned} L(w) & = \sum_{i=1}^N||w^Tx_i-y_i||^2 
            \\ & = (w^Tx_1-y_1, w^Tx_2-y_2, \cdots, w^Tx_n-y_n)
            \left(\begin{matrix}w^Tx_1-y_1 \\ w^Tx_2-y_2  \\ \vdots \\ w^Tx_n-y_n \end{matrix} \right)\end{aligned}$$
其中
$$\qquad(w^Tx_1-y_1, w^Tx_2-y_2, \cdots, w^Tx_n-y_n)\\ = w^T(x_1,x_2,\cdots,x_n)-(y_1, y_2, \cdots, y_3)\\ =w^TX^T-Y^T \quad\quad\quad\quad\quad\quad\quad\quad\quad\quad $$

$\therefore L(w)=(w^TX^T-Y^T)(Xw-Y)=w^TX^Tw-2w^TX^TY+Y^TY$
$$\hat{w}=argmin(L(w))=argmin(\sum_{i=1}^N||w^Tx_i-y_i||^2 )\\=argmin(w^TX^Tw-2w^TX^TY+Y^TY) \qquad$$
$$\frac{\partial L}{\partial w}=2X^TXw-2X^TY=0 \Rightarrow X^TXw=X^TY$$
$\therefore w=(X^TX)^{-1}X^TY$

### 概率视角看最小二乘法

假设噪声$\epsilon \sim N(0, \sigma^2), y=f(w) + \epsilon$

则有$Y|X,w \sim N(w^TX, \sigma^2) \Rightarrow P(Y|X,w)=\frac{1}{\sqrt{2\pi}\sigma}\exp\{-\frac{(Y-w^TX)^2}{2\sigma^2}\}$

则对数似然估计为
$$\begin{aligned} L(w)=\log P(Y|X,w) & =\log \prod_{i=1}^{N}P(y_i|x_i,w) \\ & = \sum_{i=1}^N\log P(y_i|x_i,w) 
\\ & = \sum_{i=1}^N(\log \frac{1}{\sqrt{2\pi}\sigma} - \frac{1}{\sqrt{2\pi}\sigma}(y_i-w^Tx_i)^2)\end{aligned}$$

由最大似然估计, 有

$$\begin{aligned} \hat{w} & = argmax(L(w))
\\ & = argmax(\sum_{i=1}^N - (y_i-w^Tx_i)^2)
\\ & = argmin(\sum_{i=1}^N (y_i-w^Tx_i)^2)
 \end{aligned}$$

 因此, 有结论:

 当噪声$\epsilon \sim N(0, \sigma^2)$时, 最小二乘估计(LSE)等价于最大似然估计(MLE)