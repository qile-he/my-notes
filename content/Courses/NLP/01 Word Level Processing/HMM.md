>Hidden Markov Model & Viterbi Algorithm

Assumption
1. The current state depends only on the previous state
	$P(q_i\mid q_1,q_2,\ldots,q_{i-1})=p(q_i\mid q_{i-1})$  当前状态只依赖前一个状态
2. Independent Observation
	$P(o_i\mid q_1,\ldots,q_T,o_1,\ldots) = P(o_i\mid q_i)$  当前位置观察到什么词，只由当前位置的隐藏状态决定

Paraments
- $\lambda=(A,B,\pi)$
- 初始概率 $\pi_i=P(q_1=s_i)$ 第一个词的词性是 $s_i$ 的概率
- 状态转移概率 $a_{ij}=P(q_{t+1}=s_j\mid q_t=s_i)$ 当前词性是 $i$，下一个词性是 $j$ 的概率
- 发射概率 $b_j(k)=P(o_t=v_k\mid q_t=s_j)$ 当词性是 $j$ 时，生成某个词的概率

Three Core Issues
1. 观测概率 (Observation Likelihood)
	给定 $\lambda=(A,B,\pi)$ 和 $O$ 求 $P(O\mid\lambda)$
2. 解码问题 (Decoding)
	求 $Q^* = \arg\max_QP(Q,O\mid\lambda)$
3. 最大似然的参数训练，学习问题 (Learning)
	学习 $A, B, \pi$ 

---
## Viterbi Algorithm
>Core: dp

$v_t(j)$ 表示：在第 $t$ 个位置处于状态 $j$，并且已经观察到 $o_1,\ldots,o_t$ 时，所有可能路径中概率最大的那一条路径的概率
$v_1(j)=\pi_jb_j(o_1)$
$v_t(j) = \max_i [ v_{t-1}(i)a_{ij} ] b_j(o_t)$

optimal substructure 最优子结构

HMM 的独立性假设限制了模型使用多重、相关的观察特征；同时 HMM 属于建模联合概率 $P(O,q)$ 的生成模型。