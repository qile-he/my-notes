Traditional tokenization has four disadvantages
1. 分词错误
2. OOV (Out of Vocabulary)
3. 低频词
4. 词型变换

---
## Subword tokenization
>不使用完整 word，也不拆到 character，而是在两者之间寻找粒度

Tokenizer 是：$\boxed{ text \leftrightarrow token\ sequence }$

主要算法
## 1. BPE

Byte Pair Encoding

GPT 系列主要使用。

---

## 2. WordPiece

BERT 使用。

---

## 3. Unigram

T5、mBART 使用。