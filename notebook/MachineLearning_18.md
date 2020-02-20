# Variational Inference

##  Background

$$
\text{频率角度} \rarr \text{优化问题}
\begin{cases}
\text{回归： }f(w)=w^Tx  \\
\qquad\quad \text{loss function: } 
\begin{cases} 
    L(w) = \sum_{i=1}^N||w^Tx_i-y_i||^2 \\
    \hat w = \arg\min L(w) 
\end{cases} \\
\qquad\quad \text{解法:} 
    \begin{cases} 
        \text{解析解：} 
        \frac{\partial L(w)}{\partial w} = 0 \Rightarrow w^*=(X^TX)^{-1}X^TY \\
        \text{数值解: Gradient Descent} 
    \end{cases} \\
\text{分类: SVM(约束优化问题)}\quad f(w) = sign(w^Tx+b) \\
\qquad\quad \text{loss function: } 
\begin{cases} 
    \min \frac{1}{2}w^Tw \\
    \text{s.t.}\quad y_i(w^Tx_i+b) \geq 1
\end{cases} \\
\qquad\quad \text{解法:} 
    \begin{cases} 
        \text{QP} \\
        \text{Lagrange 对偶} 
    \end{cases} \\
\text{EM: } \quad \hat \theta =\arg\max\log P(x|\theta) \\
\quad \qquad \theta^{(i+1)} = \arg\max\int_z P(x,z|\theta) \cdot P(z|x,\theta^{(i)})dz
\end{cases}$$


$$
\text{贝叶斯角度} \rarr \text{积分问题} 
\begin{cases}
\underbrace{P(\theta)}_{\text{后验}} = 
\frac{\overbrace{P(x|\theta)}^{\text{似然}} \cdot 
\overbrace{P(\theta)}^{\text{先验}}}{\underbrace{P(x)}_{\int_\theta P(x|\theta)\cdot P(\theta) d\theta}}
\end{cases}
$$

