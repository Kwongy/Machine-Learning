## 高斯分布求边缘概率和条件概率

$$x\sim N(\mu, \sigma^2)=\frac{1}{(2\pi)^{(\mu/2)}\sigma}
\exp{(-\frac{1}{2}(x-\mu)(\sigma^2)^{-1}(x-\mu)^T)}$$
$$x \in \mathbb{R^p}, x = \left(\begin{matrix}x_1 \\x_2  \\\vdots \\x_p \end{matrix} \right),    \mu = \left(\begin{matrix}\mu_1 \\\mu_2  \\ \vdots \\\mu_p \end{matrix} \right),
   \sigma=\left(\begin{matrix}
   \sigma_{11} & \sigma_{12} & \cdots & \sigma_{1p}\\
   \sigma_{21} & \sigma_{22} & \cdots & \sigma_{2p}  \\
   \vdots & \vdots & \ddots & \vdots \\
    \sigma_{p1} & \sigma_{p2} & \cdots & \sigma_{pp} \end{matrix} \right)$$

令
$$\alpha = \mu,  \beta = \sigma^2$$

定理: 若
$$x \sim N(\alpha,\beta),x \in \mathbb{R}^p \\ y = Ax + B, y \in \mathbb{R}^q $$
则有:
$y\sim N(A\alpha+B, A\beta A^T)$

证明:
$$\begin{aligned} 
E[y]  = E(Ax+B) = & AE[x]+B \\ = & A\alpha + B
\end{aligned}$$
$$\begin{aligned}
    Var(y) & = Var(Ax+B) \\
 & = Var[Ax] + Var[B] \\ & = A\cdot Var[x] \cdot A^T \\ & = A\cdot \beta \cdot A^T
\end{aligned}$$

已知
$$x = \left(\begin{matrix}x^m_a \\x^n_b\end{matrix} \right),
m + n = p, \alpha=\mu=\left(\begin{matrix}\mu_a \\ \mu_b \end{matrix} \right),\beta=\left(\begin{matrix}\beta_{aa} & \beta_{ab} \\ \beta_{ba} & \beta_{bb} \end{matrix} \right)$$

求: $P(x_a),P(x_b|x_a)$

$P(x_a)$:

$$\begin{aligned}
    E[x_a] = E[\left(\begin{matrix}I_a & 0 \end{matrix} \right) \left(\begin{matrix}x_a \\ x_b \end{matrix} \right)]=
    \left(\begin{matrix}I_a & 0 \end{matrix} \right) \left(\begin{matrix}\alpha_a \\ \alpha_b \end{matrix} \right) = \alpha_a
\end{aligned}$$

$$Var[x_a]=Var[\left(\begin{matrix}I_a & 0 \end{matrix} \right) \left(\begin{matrix}x_a \\ x_b \end{matrix} \right)]=
    \left(\begin{matrix}I_a & 0 \end{matrix} \right) 
    \left(\begin{matrix}\beta_{aa} & \beta_{ab} \\ \beta_{ba} & \beta_{bb} \end{matrix} \right)
    \left(\begin{matrix}I_a \\ 0 \end{matrix} \right) = \beta_{aa}$$

$\therefore x_a\sim N(\alpha_a, \beta_{aa}), x_b\sim N(\alpha_b, \beta_{bb})$

$P(x_b|x_a)$:

令$x_{b\cdot a}=x_b|x_a$, 则有(具体原因见Schur complement)
$$\begin{cases}
x_{b\cdot a}=x_b-\beta_{ba}\beta_{aa}^{-1}x_a\\
\alpha_{b\cdot a}=\alpha_b-\beta_{ba}\beta_{aa}^{-1}\alpha_a\\
\beta_{bb\cdot a}=\beta_{bb}-\beta_{ba}\beta_{aa}^{-1}\beta_{ab}\\
\end{cases}$$
于是有,
$$\begin{aligned}
    E[x_{b\cdot a}] & = E[\left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} & I_n \end{matrix} \right) \left(\begin{matrix}x_a \\ x_b \end{matrix} \right)] \\ & = 
    \left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} & I_n \end{matrix} \right) \left(\begin{matrix}\alpha_a \\ \alpha_b \end{matrix} \right) \\ & = \alpha_b -\beta_{ba}\beta_{aa}^{-1}\alpha_a
    = \alpha_{b\cdot a}
\end{aligned}$$

$$\begin{aligned}
    Var[x_{b\cdot a}] & = Var[\left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} & I_n \end{matrix} \right) \left(\begin{matrix}x_a \\ x_b \end{matrix} \right)] \\ & = 
    \left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} & I_n \end{matrix} \right) \left(\begin{matrix}\beta_{aa} & \beta_{ab} \\ \beta_{ba} & \beta_{bb} \end{matrix} \right) 
    \left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} \\ I_n \end{matrix} \right)
     \\ & = \left(\begin{matrix} 0 & \beta_{bb}-\beta_{ba}\beta_{aa}^{-1}\beta_{ab} \end{matrix} \right) \left(\begin{matrix}-\beta_{ba}\beta_{aa}^{-1} \\ I_n \end{matrix} \right)
     \\ & = \beta_{bb}-\beta_{ba}\beta_{aa}^{-1}\beta_{ab} = \beta_{bb\cdot a}
\end{aligned}$$


$\therefore x_{b\cdot a}\sim N(\alpha_{b\cdot a}, \beta_{bb\cdot a})$

$$E[x_b|x_a] = E[x_{b\cdot a}]= \alpha_b -\beta_{ba}\beta_{aa}^{-1}\alpha_a$$
$$Var[x_b|x_a] = Var[x_{b\cdot a}] =  \beta_{bb}-\beta_{ba}\beta_{aa}^{-1}\beta_{ab}$$

$\therefore x_b|x_a \sim N(\alpha_b -\beta_{ba}\beta_{aa}^{-1}\alpha_a,  \beta_{bb}-\beta_{ba}\beta_{aa}^{-1}\beta_{ab})$

 
## 高斯分布求联合概率

已知:
$$P(x)=N(x|\mu, \Lambda^{-1}) \\ P(y|x)=N(y|Ax+b, L^{-1})$$
求:$P(y), P(x|y)$

解: 由已知得
$$y=Ax+b+ \epsilon, \epsilon\sim N(0, L^{-1})$$
则有,
$$E[y] = E[Ax+b+\epsilon]=AE[x]+b+\epsilon=A\mu+b$$
$$\begin{aligned} Var[y] & =  Var[Ax+b+\epsilon] \\ & = A\cdot Var[x]\cdot A^T+Var[\epsilon] \\ & = A\cdot \Lambda^{-1}\cdot A^T + L^{-1}\end{aligned}$$

$\therefore y\sim N(A\mu+b,  A\cdot \Lambda^{-1}\cdot A^T + L^{-1})$

令$z = \left(\begin{matrix}x \\ y \end{matrix} \right)$,则$z\sim 
N(\left(\begin{matrix} \mu \\ A\mu+b \end{matrix} \right),
\left(\begin{matrix} \Lambda^{-1} & \Delta \\ \Delta & A\cdot \Lambda^{-1}\cdot A^T + L^{-1} \end{matrix} \right) )$

$$\begin{aligned} 
    \Delta & =  Cov(x, y) \\
    & =  E[(x-E[x])\cdot (y-E[y])^T] \\
    & = E[(x-\mu)\cdot (y-A\mu-b)^T] \\
    & = E[(x-\mu)\cdot (Ax+b+\epsilon-A\mu-b)^T] \\
    & = E[(x-\mu)\cdot (A(x-\mu)+\epsilon)^T] \\
    & = E[(x-\mu)\cdot (A(x-\mu))^T + (x-\mu)\cdot \epsilon^T] \\
    & = E[(x-\mu)\cdot (A(x-\mu))^T] + E[(x-\mu)\cdot \epsilon^T] \\
    & = E[(x-\mu)\cdot (A(x-\mu))^T] + E[(x-\mu)]\cdot \underbrace{E[\epsilon^T]}_{0} \\
    & = E[(x-\mu)\cdot (x-\mu)^T \cdot A^T]\\
    & = Var[x]\cdot A^T\\
    & = \Lambda^{-1} \cdot A^T
\end{aligned}$$

根据上一节公式代入,则$P(x|y) \sim N(\mu-\Delta\Lambda (A\mu + b), 
A \Lambda^{-1} A^T + L^{-1}- \Delta\Lambda\Delta^T$
