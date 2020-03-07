## Spectral Clustering

$G=\{V,E\}$
$V={1,2,\cdots,N}, E: W=[w_{ij}]_{N\times N}$
$$\begin{cases}
V = \bigcup_{k=1}^KA_k\\
\forall i,j \in\{1,2,\cdots,K\},A_i\bigcap A_j=\emptyset
\end{cases}$$

$N_{cut}(v)=N_{cut}(A_1,\cdots,A_K)=\sum_{k=1}^K\frac{w(A_k,v)-w(A_k,A_k)}{\sum_{i\in A_k\sum_{j=1}^Nw_{ij}}}$

Model:
$$\{\hat A_k\}_{k=1}^K=\mathop{\arg\min}\limits_{\{A_k\}_{k=1}^K} N_{cut}(v)$$

