## 线性分类

### 逻辑回归

$$X=\left(\begin{matrix}x_1^T \\x_2^T  \\\vdots \\x_p^T \end{matrix} \right)_{N \times p}, Y=\left(\begin{matrix}y_1 \\y_2  \\\vdots \\y_N \end{matrix} \right)_{N\times 1}$$

$$\{(x_i, y_i)\}^N_{i=1}, x \in \mathbb{R^p}, y_i\in \{+1,-1\}$$

sigmoid function:
$$\sigma(z)=\frac{1}{1+\exp(-z)}$$

$$P_1=P(y=1|x)=\sigma(w^Tx)=\frac{1}{1+\exp(-w^Tx)}$$

$$P_2=P(y=0|x)=1-\sigma(w^Tx)=\frac{w^Tx}{1+\exp(-w^Tx)}$$


$$\begin{aligned}
    MLE: \hat w & = argmax(\log P(Y|X))
             \\ & = argmax(\log \prod_{i=1}^N P(y_i|x_i))
             \\ & = argmax(\sum_{i=1}^N\log P(y_i|x_i))
             \\ & = argmax(\sum_{i=1}^N(y_i\log P_1+(1-y_i)\log P_2))
\end{aligned}$$

$MLE(max) \Rightarrow loss \quad function(Cross entropy,\quad min)$