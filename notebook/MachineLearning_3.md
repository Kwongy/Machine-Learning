## 线性回归

### 正则化

由于最小二乘估计中$\hat w=(X^TX)^{-1}X^TY$, 由于数据量过少, 或者维度空间$p$过大, $X^TX$可能不存在逆. 因此需要使用正则化.

正则化框架
$$argmin[\underbrace{L(w)}_{Loss}+\lambda \underbrace{P(w)}_{Penalty}]$$

* $L_1: Lacso, P(w)=||w||_1$ 
* $L_2: Ridge, P(w)=||w||_2^2=w^Tw$,岭回归

$$\begin{aligned}
    J(w) & = \sum_{i=1}^N||w^Tx_i-y_i||^2 + \lambda w^Tw\\
         & = (w^TX^T-Y)(Xw-Y) + \lambda w^Tw \\
         & = w^T(X^TX + \lambda I)w-2w^TX^TY+Y^TY
\end{aligned} $$

$\hat w=argmin[J(w)]$

$$\frac{\partial J(w)}{w}=2(X^TX+\lambda I)w-2X^TY=0 $$
$$\Rightarrow \hat w=(X^TX+\lambda I)^{-1}X^TY$$
由于$X^TX$为半正定矩阵, $\lambda I$为对角矩阵, 两者相加必为可逆矩阵.

### 贝叶斯角度看正则化

假设噪声$\epsilon \sim N(0, \sigma^2), y=f(w) + \epsilon=w^TX+\epsilon$

则有$Y|X,w \sim N(w^TX, \sigma^2) \Rightarrow P(Y|X,w)=\frac{1}{\sqrt{2\pi}\sigma}\exp\{-\frac{(Y-w^TX)^2}{2\sigma^2}\}$

假设$w \sim N(0, \sigma_0^2), P(w)=\frac{1}{\sqrt{2\pi}\sigma_0}\exp\{-\frac{||w||^2}{2\sigma_0^2}\}$

$$P(w|Y)=\frac{P(Y|w)P(w)}{P(Y)}$$

则最大后验概率MAP为
$$\begin{aligned} \hat w & =argmax[P(w|Y)] \\
& = argmax [P(Y|w)\cdot P(w)] \\ & = argmax(\log[P(Y|w)\cdot P(w)])\\ & = argmax [\log(\frac{1}{2\pi\sigma\sigma_0}) + \log\exp\{-\frac{\sum_{i=1}^N||w^Tx_i-y_i||^2}{2\sigma^2}-\frac{||w||^2}{2\sigma_0^2} \}]
\\ & = argmin(\frac{\sum_{i=1}^N||w^Tx_i-y_i||^2}{2\sigma^2}+\frac{||w||^2}{2\sigma_0^2}) \\ & = \sum_{i=1}^N||w^Tx_i-y_i||^2+\frac{\sigma^2}{\sigma^2_0}||w||^2 = (w^TX^T-Y)(Xw-Y) + \frac{\sigma^2}{\sigma^2_0} w^Tw\end{aligned}$$


 因此, 有结论:

 当噪声$\epsilon \sim N(0, \sigma^2)$时, 最小二乘估计(LSE)等价于最大似然估计(MLE)

 当先验prior也是高斯分布时, 正则化最小二乘估计Regularized LSE等价于最大后验估计MAP