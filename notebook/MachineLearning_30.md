## Bayesian Linear Regression

Data = $\{(x_i,y_i)\}_{i=1}^N$

Model:
$$\begin{cases}
f(x)=w^Tx=x^Tw \\
y = f(x) + \epsilon
\end{cases}$$

Bayesian Method；w不是一个未知的常量，而是一个概率分布
$$\begin{cases}
\text{Inference: Posterior}(w) \\
\text{Prediction: }x^* \rarr y^*
\end{cases}$$

Inference：
$$P(w|Data)=P(w|X,Y)=\frac{P(w,Y|X)}{P(Y|X)}=\frac{P(Y|X,w)\cdot P(w|X)}{\int P(Y|w,X)P(w|X)dw}$$

$P(w|Data) \propto \text{Likelihood} \times \text{prior}$

Predition: Give $x^* \rarr y^*$
$P(y^*|Data,x^*)=\int P(y^*|w,Data,x^*)\cdot P(w|data,x^*)dw$

