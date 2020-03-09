## Confronting Partition Function

Motivation: Learning, evaluation

$x\in \mathbb{R}^p, \{0, 1\}^p$
$$P(x;\theta) = \frac{1}{z(\theta)}\hat P(x;\theta),\quad z(\theta) = \int \hat P(x; \theta)dx$$

ML Learing: Given $X = \{x_i\}_{i=1}^N$, estimate $\theta$

$$\begin{aligned}
\hat \theta & = \mathop{\arg\max}\limits_{\theta}P(X;\theta) = \mathop{\arg\max}\limits_{\theta}\prod_{i=1}^NP(x_i;\theta) \\
& = \mathop{\arg\max}\limits_{\theta}\log \prod_{i=1}^NP(x_i;\theta) \\
& = \mathop{\arg\max}\limits_{\theta}\sum_{i=1}^N\log P(x_i;\theta) \\
& = \mathop{\arg\max}\limits_{\theta}\sum_{i=1}^N\log \hat P(x_i;\theta) -\log z(\theta) \cdot N\\
& = \mathop{\arg\max}\limits_{\theta} 
\underbrace{\frac{1}{N} \sum_{i=1}^N\log \hat P(x_i;\theta) - \log z(\theta)}{l(\theta)} \\
\end{aligned}$$
$\nabla_\theta l(\theta)=\frac{1}{N}\nabla_\theta\log\hat P(x_i;\theta) - \underbrace{\nabla_\theta\log z(\theta)}_{\Delta}$
$$\begin{aligned}
\Delta & = \frac{1}{z(\theta)}\cdot \nabla_\theta z(\theta) = \frac{P(x;\theta)}{\hat P(x;\theta)}\cdot \nabla_\theta \cdot \int \hat P(x;\theta)dx \\
& = \int \frac{P(x;\theta)}{\hat P(x;\theta)}\cdot \nabla_\theta \hat P(x;\theta) dx \\
& = \int P(x; \theta) \cdot \nabla_\theta\log \hat P(x;\theta) dx \\
& = E_{P(x;\theta)}[\nabla_\theta\log\hat P(x;\theta)]
\end{aligned}$$