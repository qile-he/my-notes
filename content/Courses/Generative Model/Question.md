
如果训练之后 `h` 能服从一个已知分布，例如标准高斯，就很好；这时用随机噪声替换 encoder, decoder 就可以成为生成模型。why?

为什么 sampling 不可直接求导?

Vanilla AE 中是$h=g(x)$,
VAE 中为什么改成$h\sim g(x)?$

How to make \(h\) to be a known distribution after training?

1. 为什么只有 reconstruction loss 时，不能保证生成阶段从$N(0,I)$采到的 $h$ 是 decoder 熟悉的？
2. KL divergence 在 VAE 里的作用是什么？
3. 如果把 KL loss 权重 $\lambda$ 调得特别特别大，你觉得 latent space 和 reconstruction 分别会发生什么

A:
1. 只有 reconstruction loss 时，只要求 decoder 能从 $q(h|x)$ 中采到的 $h$ 重建 $x$，并不会约束 $q(h|x)$ 接近 $N(0,I)$。因此训练得到的 latent distributions 可能分布在任意区域，生成阶段从$N(0,I)$ 采出的 $h$ 可能落在 decoder 没训练过的区域。 
2. KL divergence 作为 regularization，惩罚 $q(h|x)$ 与标准高斯 $N(0,I)$ 的差异，使 latent space 具有已知、规整的概率结构，从而生成阶段可以从 $N(0,I)$ 直接采样。
3. 当 $\lambda$ 非常大时，KL loss 会主导训练，使不同输入对应的 $q(h|x)$ 都强烈趋近 $N(0,I)$，即 $\mu(x)\to0,\sigma(x)\to1$。这样 latent variable 中关于输入 $x$ 的信息会减少，因此 reconstruction performance 会下降。

