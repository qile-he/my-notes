>Singular Value Decomposition

## SVD
$\boxed{A=U\Sigma V^T}$

SVD 的几何直觉：旋转 → 缩放 → 旋转
可以把奇异值理解为：数据沿不同重要方向的尺度
如果一个方向对应的奇异值特别大，就意味着这个方向在重构矩阵时起到更重要的作用

### Truncated SVD
假设原矩阵：$A\in\mathbb R^{10000\times5000}$
其中 10,000 是词汇表大小，5,000 是文档数量。
如果我们只想保留最重要的 300 个语义维度，可以构造：
$\boxed{A_{300}=U_{300}\Sigma_{300}V_{300}^T}$
