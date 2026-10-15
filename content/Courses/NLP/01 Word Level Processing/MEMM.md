>Maximum Entropy Markov Model

从生成模型转向判别模型(discriminative model)
它不再建模：$P(O,Q)$  而直接建模：$P(Q\mid O)$
建模条件概率 $P(q\mid O)$、忽略 $P(O)$、允许灵活使用特征
HMM：“标签和句子一起，是怎么产生出来的？”（生成模型）
MEMM：“既然句子已经给我了，那么标签是什么？”（判别模型）

---
## Label Bias
MEMM是局部归一化 (local normalization)
$\sum_j P(y_t=j\mid y_{t-1},x)=1$
那么问题来了，假设状态A只有`2`个出口，而状态B有`5`个出口，此时A分到的平均概率一般会大于B，于是模型可能偏爱出口少的出口，这不符合我们的预期