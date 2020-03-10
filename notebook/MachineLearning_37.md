$l(\theta)=\frac{1}{N}\log\hat P(x_i;\theta) - \log z(\theta)$

$\nabla_\theta l(\theta)=\underbrace{E_{P_{data}}[\nabla_\theta\log\hat P(x_i;\theta)]}_{\text{Postive phase}}-\underbrace{E_{P_{model}}[\nabla_\theta\log\hat P(x_i;\theta)]}_{\text{Negative phase}}$

Gradient Ascend

$\theta^{(t+1)} = \theta^{(t)} +\eta\nabla_\theta l(\theta^{(t)})$

Gibbs Sampling from $P_{model} = P(x;\theta^{(t)})$

$$\theta^{(t+1)} = \theta^{(t)} +\eta(\sum_{i=1}^m\nabla_\theta\log\hat P(x_i;\theta^{(t)})-\sum_{i=1}^m\nabla_\theta\log\hat P(\hat x_i;\theta)) $$