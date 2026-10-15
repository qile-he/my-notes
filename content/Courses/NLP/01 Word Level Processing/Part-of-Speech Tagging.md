## Word Segmentation

Chinese word segmentation is, in itself, an NLP problem
 - 交集型歧义 Intersection-Type Ambiguity (ABC-->AB/C or A/BC)
	`eg.从小学-->从小/学 or 从/小学`
- 组合型歧义 Combination-Type Ambiguity (AB or A, B)
	`eg.中将`

## Two Main Approaches of Word Segmentation
1.Dictionary Match
  - Forward Maximum Matching
	  `From left to right, find the longest word each time`
  - Reverse Maximum Matching
2.Sequence Annotation
	Four labels
 - B - Begin
 - M - Middle
 - E - End
 - S - Single
```
英伟达 违反 反垄断法 被 进一步 调查
英/B 伟/M 达/E 违/B 反/E 反/B 垄/M 断/M 法/E 被/S 调/B 查/E
```
分词问题 → 预测标签问题

---
## 词类 (Part-of-Speech)
- 形态分布 (Morphological Distribution)
  >根据词语所接词缀的相似功能（即其形态属性），划分为不同的类别（中文无法这么分）
- 句法分布 (Syntactic Distribution)
  >根据在相邻语境中的功能相似性，可将词语划分为不同类别。