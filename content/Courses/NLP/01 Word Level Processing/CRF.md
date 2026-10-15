>Conditional Random Field

Label Bias 解决方案：不局部归一化
而是全局归一化（global normalization）
从局部概率到局部势能（potentials）

potentials：某个标签转移与当前输入有多匹配的未归一化分数

CRF is discriminative model
建模 $\boxed{P(Y\mid X)}$


| 模型   | 建模对象           | 输入特征     | 归一化   |
| ---- | -------------- | -------- | ----- |
| HMM  | \(P(X,Y)\)     | 受独立性假设限制 | 生成式   |
| MEMM | \(P(Y\mid X)\) | 灵活       | 局部归一化 |
| CRF  | \(P(Y\mid X)\) | 灵活       | 全局归一化 |

$\boxed{ HMM \xrightarrow{\text{独立性假设太强}} MEMM \xrightarrow{\text{Label Bias}} CRF }$
