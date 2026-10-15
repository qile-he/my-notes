>Byte Pair Encoding

BPE = 不断合并最常出现的相邻token

## BPE Training（训练阶段）

`</w>` 表示word end
`<|endoftext|>` 表示一端文本结束了

先将训练语料拆成字符，添加词尾标记
然后统计相邻字符，pair frequency，merge出现频率最多的
合并之后继续统计、合并

BPE本质是贪心算法：$\boxed{merge当前最高频pair}$

Vocabulary Size = Base vocabulary + Numbers of merges

Byte-Level：先转UTF-8 byte
基础词表数固定为256
理论上任何文本都可以表示

---
## BPE Encoding（推理阶段）

严格按照训练时得到的merge顺序进行

BPE 没有显式学习 morphology，但频率统计可能让它自动得到一些与形态结构相似的 token

要遵循训练期间学到的 merge 顺序，直到没有更多可执行的合并

$\boxed{ \text{大词表} \Longleftrightarrow \text{短序列} }$
