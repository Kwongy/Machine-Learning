## 线性分类

### 高斯判别分析

$$X=\left(\begin{matrix}x_1^T \\x_2^T  \\\vdots \\x_p^T \end{matrix} \right)_{N \times p}, Y=\left(\begin{matrix}y_1 \\y_2  \\\vdots \\y_N \end{matrix} \right)_{N\times 1}$$

$$\{(x_i, y_i)\}^N_{i=1}, x \in \mathbb{R^p}, y_i\in \{0,1\}$$

$$\underbrace{P(y|x)}_{posterior} \propto \underbrace{P(x|y)}_{likelihood} \underbrace{P(y|x)}_{prior}$$

假设
$y \sim Bernoulli(\phi) \Rightarrow \phi^y(1-\phi)^{1-y}$
$$\begin{matrix}
    x|y=1 \sim N(\mu_1, \sum) \\
    x|y=0 \sim N(\mu_2, \sum)
\end{matrix}\left.\rule{0mm}{5mm}\right\}
\Rightarrow N(\mu_1, \sum)^yN(\mu_2, \sum)^{1-y}$$

$\hat \theta=argmaxL(\theta),\theta=(\mu_1,\mu_2,\sum,\phi)$
$$\begin{matrix}
    y=1, \quad N_1 \\
    y=0 ,\quad N_2
\end{matrix}, \quad N_1 + N_2 = N$$

log-likelihood : 

$$\begin{aligned}
    L(\theta) & =\log \prod_{i=1}^NP(x_i, y_i) \\
              & = \sum_{i=1}^N[
    \underbrace{\log N(\mu_1, \sum)^y_i}_{(1)} + \underbrace{\log N(\mu_2, \sum)^{1-y_i}}_{(2)} + \underbrace{\log \phi^y(1-\phi)^{1-y}}_{(3)}]
\end{aligned}$$

求$\phi$:
$$\begin{aligned}
    \frac{\partial (3)}{\partial \phi} & = \sum_{i=1}^Ny_i\frac{1}{\phi} - (1-y_i)\frac{1}{1-\phi} = 0
    \\ & \Rightarrow \sum_{i=1}^Ny_i(1-\phi)-(1-y_i)\phi = 0
    \\ & \Rightarrow \sum_{i=1}^N (y_i - \phi) = 0
    \\ & \Rightarrow \sum_{i=1}^N y_i - N\phi = 0
\end{aligned}$$

$\therefore \hat \phi = \frac{1}{N}\sum_{i=1}^Ny_i=\frac{N_1}{N}$

求$\mu_1$

$$\begin{aligned}
    (1) & = \sum_{i=1}^N\log N(\mu_1, \sum)^{y_i}
    \\  & = \sum_{i=1}^N y_i\log\frac{1}{(2\pi)^{p/2}|\sum|^{1/2}}
    \exp(-\frac{1}{2}(x_i-\mu_1)^T|\sum|^{-1}(x_i-\mu_1))
    \\ \Rightarrow \mu_1& = argmax[\sum_{i=1}^Ny_i(-\frac{1}{2}(x_i-\mu_1)^T|\sum|^{-1}(x_i-\mu_1))]
    \\ & = argmax[-\frac{1}{2}\sum_{i=1}^Ny_i(x_i^T|\sum|^{-1}x_i-2\mu_1^T|\sum|^{-1}x_i + \mu_1^T|\sum|^{-1}\mu_1)]
\end{aligned}$$

$$\begin{aligned}
    \frac{\partial (1)}{\partial \mu_1}  = \sum_{i=1}^Ny_i(|\sum|^{-1}\mu_1 - |\sum|^{-1}x_i) & = 0
    \\ \sum_{i=1}^Ny_i(\mu_1 -x_i) & = 0
    \\ \sum_{i=1}^Ny_i\mu_1 &=\sum_{i=1}^Ny_ix_i
    \\ \Rightarrow\hat \mu_1 & = \frac{\sum_{i=1}^Ny_ix_i}{N_1}
\end{aligned}$$

关于$\sum$,不推了, 结论为:$\sum = \frac{1}{N}(N_1S_1+N_2S_2)$