## Intrinsic Evaluation：内在评估
### Word Analogies (词类比)

$v_{\text{king}}-v_{\text{man}} \approx v_{\text{queen}}-v_{\text{woman}}$

### Word Similarities (词语相似度)

常用指标 $\boxed{ \cos(\theta)= \frac{v_a^Tv_b}{\|v_a\|\|v_b\|} }$

## Extrinsic Evaluation：外在评估

放进实际任务

### Intrinsic 和 Extrinsic 的区别

| |Intrinsic|Extrinsic|
|---|---|---|
|评估对象|词向量自身的性质|词向量在下游任务中的效果|
|典型任务|Word Similarity、Analogy|NER|
|计算成本|通常较低|通常较高|
|优点|快速诊断语义结构|更接近实际应用|
|局限|不一定代表下游效果|容易受到其他模型组件影响|