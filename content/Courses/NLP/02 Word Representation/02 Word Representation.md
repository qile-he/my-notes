## Overview
- [[SVD]]
- [[Topic Model]]
- [[Word2Vec]]
- [[GloVe]]
- [[Word Embedding Evaluation]]

---

### 基于词典的方法
- WordNet
### 基于计数的方法
- 点互信息
- 基于SVD的降维
### 基于神经网络的方法：Word2Vec
- CBOW
- Skip-ngram
- 负采样
Glove
评测

## Distributional Hypothesis（分布式假设）
>You should know a word by the company it keeps.

出现在相似上下文中的词语，往往具有相似的含义

## 如何用数学方法表示词的上下文？

### Term Document Matrix
>通过一个词出现在哪个文档中，来刻画这个词的含义

### TF-IDF
TF (Term Frequency): 衡量词在文档中出现得有多频繁
$\boxed{TF(w,d)=\frac{n_{w,d}}{N_d}}$
其中$n_{w,d}$ 是词 $w$ 在文档 $d$ 中出现的次数，$N_d$ 是文档总词数

IDF (Inverse Document Frequency): 衡量词在整个语料库中有多罕见
$\boxed{IDF(w)=\log_{10}\frac{D}{1+d_w}}$

### Word-Word Co-occurrence Matrix
>统计两个词在一定距离内共同出现的次数

### PMI: Pointwise Mutual Information、
>两个词联合出现的概率，相比它们独立出现时的预期概率，高出了多少

$\boxed{PMI(x,y)=\log_2\frac{P(x,y)}{P(x)P(y)}}$
整数：比独立情况是更容易共现
0：与独立情况相符
负数：比独立情况更不容易共现
