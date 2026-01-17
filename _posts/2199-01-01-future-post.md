---
title: 'BPE Tokenizer'
date: 2026-01-10
permalink: /posts/2026/01/bpe-tokenizer/
tags:
  - stanford-cs336
  - LLM
  - NLP
---

This is a placeholder for a blog post about BPE Tokenizer. To disable scheduling of future posts, edit `config.yml` and set `future: false`. 


# Questions before we start

- How are text represented in a computer?
- What is Unicode?
- What is UTF-8?
- What does it mean to train a tokenizer based on utf-8 bytes?

# Fundamentals

_Tokenization_ is the process of converting raw text (stored as sequence of bytes in computer memory) into a sequence of integer ids. How are text represented in a computer? The answer is Unicode. 

Tokenization: strings <-> tokens (indices).
```python
list("hello".encode("utf-8")) # [104, 101, 108, 108, 111]
list('你好'.encode('utf-8')) # [228, 189, 160, 229, 165, 189]
# Each integer represents a byte value in the UTF-8 encoding (0-255).
# A character is represented by 1-4 bytes in UTF-8. 

bytes([97,98,99]).decode('utf-8') # 'abc'
```

Design considerations behind tokenization:
- Working with raw bytes is elegant, but compute-inefficient with today's model architectures.
- Character-based, byte-based, word-based tokenization are highly suboptimal.


## Unicode


