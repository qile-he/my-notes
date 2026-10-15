>Global Vectors for Word Representation

出发点：共现概率
共现矩阵：$X_{ij}=\text{词 }j\text{ 出现在词 }i\text{ 上下文中的次数}$

GloVe 关注：
$\boxed{R_{ijk}=\frac{P(k\mid i)}{P(k\mid j)}}$

利用向量差表达词语之间的关系

$\boxed{ F((w_i-w_j)^T\tilde w_k) =\frac{P_{ik}}{P_{jk}} }$

最终损失为：
$\boxed{ J=\sum_{i,k}f(X_{ik}) \left( w_i^T\tilde w_k+b_i+\tilde b_k-\log X_{ik} \right)^2 }$

权重函数：
$\boxed{ f(x)= \begin{cases} (x/x_{\max})^\alpha,&x<x_{\max}\\ 1,&x\ge x_{\max} \end{cases} }$
