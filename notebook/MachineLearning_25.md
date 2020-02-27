## Guassian Mixture Model

### Background

从几何角度来看：加权平均(由多个高斯分布叠加而成)
$$P(x) = \sum_{k=1}^K \alpha_k N(x|\mu_k,
\sigma_k), \quad s.t.\sum_{k=1}^K\alpha_k=1$$


从混合角度来看：
x： observed variable
z： latent variable

$z$|$C_1$|$C_2$|$\cdots$|$C_k$
-|-|-|-|-|
$P$|$P_1$|$P_2$|$\cdots$|$P_k$
$\sum_{k=1}^KP_k=1$
$$\begin{aligned} 
P(x) & = \sum_z P(x,z) \\
& = \sum_{k=1}^K P(x,z=C_k) \\
& =   \sum_{k=1}^K P(z=C_k) \cdot P(x|z = C_k) \\
& = \sum_{k=1}^K P_k\cdot N(x|\mu_K,\sigma_k)
\end{aligned}$$