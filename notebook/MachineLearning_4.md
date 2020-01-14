## 线性分类

### 感知机

思想: 错误驱动

模型:
$$f(x) = sign(w^Tx), x \in \mathbb{R^p}, w \in \mathbb{R^p}$$
$$sign(a)=\begin{cases}
+1,a \geq0 \\ -1, a< 0 \end{cases}$$

策略: Loss function

$$L(w)=\sum_{i=1}^N I\{y_iw^Tx_i < 0\}$$
该损失函数不可导, 且因为
$$\begin{matrix}
    w^Tx_i>0, y_i=+1 \\
    w^Tx_i<0, y_i=-1
\end{matrix}\left.\rule{0mm}{5mm}\right\}
\Rightarrow \begin{cases}
y_iw^Tx_i>0, Correct \\ y_iw^Tx_i<0, Error \end{cases}
$$

有等价的可导的loss function
$$L(w)=\sum_{x_i \in D}-y_iw^Tx_i$$
其中D:{被错误分类的样本}
$$\nabla_wL=-y_ix_i$$

算法:SGD求解
