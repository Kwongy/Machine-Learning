## Restricted Boltzmann Machine

Boltzmann Machine: Markov Random Field with hidden nodes

$x=\{x_1,x_2,\cdots,x_p\}= \{h,v\}$
$h=\{h_1,h_2,\cdots,h_n\}, v=\{v_1,v_2,\cdots,v_m\},n+m=p$

任意的无向图模型都可以看作是Boltzmann machine

Restricted Boltzmann machine: h, v之间有连接，h, v内部认为是独立的(无连接)。

$p(x)=\frac{1}{z}\exp\{-E(x)\}=p(h,v)=\frac{1}{z}\exp\{-E(h,v)\}$

$$\begin{aligned}
E(h,v) & = -(h^Twv + \alpha^Tv + \beta^Th) \\
& = -(\sum_{i=1}^m\sum_{j=1}^nh_iw_{ij}v_j+\sum_{j=1}^h\alpha_jv_j+\sum_{i=1}^m\beta_ih_i)
\end{aligned}$$