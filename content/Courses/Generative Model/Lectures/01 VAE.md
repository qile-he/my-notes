>Variational Autoencoder

An autoencoder is a feed-forward neural network whose job is to take an input `x` and predict `x`

$x \longrightarrow \text{network} \longrightarrow x'$
Training goal: $x' \approx x$
Reconstruction Loss: $L=\|x-x'\|_2^2$

identity mapping(恒等映射) is trivial/short-cut solution

## Bottleneck: key point of autoencoder
>The autoencoder will deliberately place a very small layer in the middle of the network 

$x \rightarrow \boxed{h} \rightarrow x'$
`h: code / representation / latent variable / latent representation`
$\boxed{x\xrightarrow{encoder}h\xrightarrow{decoder}x'}$

Deterministic function

representation learning: learning the most important thing
$\boxed{k\ll d}$

Linear Autoencoder: U and V are not the only ones (eg. ... )
### PCA
>Principal Component Analysis

Vanilla autoencoder is not a generative model, because we don't know the probability distribution of the latent space.

$x\in\mathbb R^{7841},\qquad h\in\mathbb R^{32}$
$\mathbb R^{32\times784}$

### VAE
>$x\xrightarrow{encoder}distribution\xrightarrow{sample}h\xrightarrow{decoder}x'$

Stochastic latent representation

At this moment, it's not $h=g(x)$, but rather $h\sim g(x)$   ( $g(x)$ is a probability distribution)

First, predefine a parametric distribution family, then have the encoder predict the mean and standard deviation, and finally sample from that distribution.

$\boxed{ x \xrightarrow{encoder} (\mu,\sigma) \xrightarrow{sample} h \xrightarrow{decoder} x' }$


### Reparameterization Trick
>$\epsilon \sim N(0,1)$
>$h = \mu + \sigma \epsilon$

The key is not to eliminating randomness, but to move the randomness to an $\epsilon$ that is independent of the model paraments.

Whenever we train the model, we treat $\epsilon$ as a constant.


### KL divergence

Regularization loss: $L_r = KL\bigl(N(\mu(x),\sigma(x))\|N(0,I)\bigr)$
$\boxed {L_{total}=L_{recon}+\lambda L_{r}}$

Reconstruction tends to promote dispersion, while regularization tends to promote concentration.

$KL(q\|p)=KL(N(\mu, \sigma ^ 2)\|N(0,1))$
$KL(q\|p)=\int q(h)\log\frac{q(h)}{p(h)}dh.$
$KL(q\|p)=E_{h\sim q}[\log q(h)-\log p(h)]$
$KL(q\|p)=\frac{1}{2}(\mu ^2+\sigma ^2-\log \sigma ^2-1)$

$\boxed{L_{\text{KL}}=\frac{1}{2}\sum _{i=1}^{d}(\mu _{i}^2+\sigma _{i}^2-\log \sigma _{i}^2-1)}$


$p(z) \quad\text{prior}$
$p(x|z) \quad\text{decoder / generation}$
$p(z|x) \quad\text{true posterior}$
$q(z|x) \quad\text{approximate posterior / encoder}$

