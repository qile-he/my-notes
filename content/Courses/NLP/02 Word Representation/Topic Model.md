## LSA (Latent Semantic Model)
>潜在语义分析

## Probabilistic Topic Model
>概率模型

1. 文档是主题上的概率分布
2. 主题是词汇表上的概率分布
主题模型是生成模型，文档是主题模型规定的概率过程的产物

在已知文档 $d$ 的情况下，生成某个词 $w$ 的概率是多少？
$\boxed{ P(w\mid d)=\sum_{z=1}^{K}P(w\mid z)P(z\mid d) }$

定义三个矩阵：
$C_{w,d}=P(w\mid d)$
$\Phi_{w,z}=P(w\mid z)$
$\Theta_{z,d}=P(z\mid d)$
$\boxed{C=\Phi\Theta}$
实际上也是一种低维矩阵分解

| 比较   | LSA（SVD）      | 概率主题模型        |
| ---- | ------------- | ------------- |
| 分解形式 | $U\Sigma V^T$ | $\Phi\Theta$  |
| 矩阵值  | 允许负数          | 非负概率          |
| 隐含维度 | 潜在语义方向        | 潜在主题          |
| 可解释性 | 不一定直观         | 主题-词分布通常更容易解释 |
| 主要依据 | 低秩矩阵近似        | 概率生成假设        |

## PLSA (Probabilistic Latent Semantic Model)
$P(d,w,z)=P(d)P(z\mid d)P(w\mid z)$
它需要学习：
- 每篇文档的主题分布 $P(z\mid d)$
- 每个主题的词分布 $P(w\mid z)$
通常通过EM(Expectation-Maximization)算法进行参数估计

## LDA (Latent Dirichlet Allocation)