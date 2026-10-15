之前的基本路线是：

$\text{语料库}\rightarrow\text{共现矩阵}\rightarrow\text{SVD}\rightarrow\text{词向量}$

但这种方法存在一些局限：
- 共现矩阵非常高维、稀疏。
- 随着词表增大，矩阵分解的计算代价也会增大。
- 每次需要从共现统计中提取低维结构，而不是直接根据预测错误学习词向量。

**So, 不要先构造完整的共现矩阵并分解，而是设计一个预测任务，让模型在不断预测上下文的过程中学习词向量**
Prediction-based methods

## CBOW
>上下文->中心词

- 词表大小为 $V$。
- 词向量维度为 $d$。
- 输入词向量矩阵为 $W\in\mathbb R^{V\times d}$。
每个单词最初都由一个 $V$ 维 $One-hot$ 向量表示

$h=\frac{1}{|C|}\sum_{w\in C}v_w$
$z=W'^Th$
$P(w\mid C)= \frac{\exp(u_w^Th)} {\sum_{j=1}^{V}\exp(u_j^Th)}$
最小化：$\boxed{\mathcal L=-\log P(w_{\text{target}}\mid C)}$

We must learn W and W'

### 前向传播（Foward Propagation）

### Softmax 和 Cross-Entropy 求导
$\boxed{ \frac{\partial\mathcal L}{\partial z_k}=p_k-t_k }$
Softmax 与 Cross-Entropy 结合之后，对 logits 的梯度恰好等于预测概率减去真实标签
$\boxed{ \frac{\partial\mathcal L}{\partial U} =(p-t)h^T }$
$\boxed{ \frac{\partial\mathcal L}{\partial h} =U^T(p-t) }$
$\boxed{ \frac{\partial\mathcal L}{\partial v_{\text{cat}}} = \frac{\partial\mathcal L}{\partial v_{\text{on}}} = \frac12 U^T(p-t) }$
两个上下文词都会获得梯度，并且在这一次训练样本中，它们获得的梯度相同
## Skip-gram
>中心词->上下文


## Negative Sampling
>把对整个词表的多分类预测，替换为少量正负样本上的二分类训练。

从 Softmax 转向 Sigmoid

$\sigma(x)=\frac{1}{1+e^{-x}}$
$1-\sigma(x)=\sigma(-x)$

最大化：$\boxed{ J= \log\sigma(u_o^Tv_c) + \sum_{i=1}^{K}\log\sigma(-u_{n_i}^Tv_c) }$

损失：$\boxed{ \mathcal L_{\mathrm{NS}} = -\log\sigma(u_o^Tv_c) -\sum_{i=1}^{K}\log\sigma(-u_{n_i}^Tv_c) }$
记得加负号

采样策略：$\boxed{ P_n(w)=\frac{f(w)^{3/4}}{\sum_{w'\in V}f(w')^{3/4}} }$
相对降低极高频词的采样优势，提高低频词相对于高频词的采样机会，但高频词通常仍然更容易被采到

梯度：$\boxed{ \frac{\partial L}{\partial v_c} = (\sigma(u_o^Tv_c)-1)u_o + \sum_{i=1}^{K}\sigma(u_{n_i}^Tv_c)u_{n_i} }$

$\boxed{L_+=-\log\sigma(u_o^Tv_c)}$

$\boxed{\nabla_{v_c}L_+=(\sigma(u_o^Tv_c)-1)u_o}$

$\boxed{v_c^{\text{new}}=v_c-\eta\nabla_{v_c}L_+}$
