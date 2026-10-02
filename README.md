# Khmer NLP — KCC Testing Script

A testing script for the [`khmer-nlp-kcc`](https://pypi.org/project/khmer-nlp-kcc/) library (v0.2.8).  
Runs **word segmentation**, **POS tagging**, and **sentiment polarity** on Khmer text from a CSV file.


[`Github khmer-nlp-kcc`](https://github.com/rinabuoy/khmer-nlp-kcc)
|
[`library kcc (v0.2.8)`](https://pypi.org/project/khmer-nlp-kcc/)
---

## Features

- Word segmentation (splits Khmer text into individual words)
- POS tagging — standard tag set (NN, VB, PRO, JJ, IN, ...)
- Nova POS tagging — extended tag set (n, v, a, o, ...)
- Sentiment polarity — `positive`, `neutral`, or `negative` with confidence scores
- Reads input from `input.csv`, writes all results to `result_1.csv`

---

## Requirements

Python 3.8 or higher.  
Install the library with:

```bash
pip install khmer-nlp-kcc==0.2.8
```

This will automatically install all dependencies:
- `torch`
- `transformers`
- `sentencepiece`
- `huggingface_hub`

> **Note:** On the first run, the model checkpoint (~400 MB) is downloaded automatically from HuggingFace and cached locally. An internet connection is required only for this first run.

---

## Project Structure

```
.
├── kcc.py          # Main script
├── input.csv       # Your input Khmer sentences (edit this)
├── result_1.csv    # Output results (auto-generated after running)
└── README.md
```

---



## Usage

```bash
python kcc.py
```



## POS Tag Reference

### Standard POS Labels

| Tag | Meaning |
|---|---|
| `NN` | Noun |
| `VB` | Verb |
| `PRO` | Pronoun |
| `JJ` | Adjective |
| `RB` | Adverb |
| `IN` | Preposition |
| `CC` | Conjunction |
| `DT` | Determiner |
| `CD` | Number |
| `SYM` | Symbol |
| `PN` | Proper noun |

### Nova POS Labels

| Tag | Meaning |
|---|---|
| `n` | Noun |
| `v` | Verb |
| `a` | Adjective |
| `o` | Other |
| `n-` | Noun (modifier) |
| `v-` | Verb (modifier) |
| `a-` | Adjective (modifier) |

---

## Language Support

This model is trained on **Khmer language only**.  
It does not support English or other languages for segmentation or POS tagging.

---

## Model Info

- Library: [`khmer-nlp-kcc`](https://pypi.org/project/khmer-nlp-kcc/0.2.8/)
- Author: [Rina Buoy](https://github.com/rinabuoy)
- Model checkpoint: [`rinabuoy/khmer-nlp-kcc`](https://huggingface.co/rinabuoy/khmer-nlp-kcc) on HuggingFace
- Tokenizer: [`rinabuoy/khmer-latin-tokenizer-kcc`](https://huggingface.co/rinabuoy/khmer-latin-tokenizer-kcc)
