# Khmer NLP — KCC Testing Script

A testing script for the [`khmer-nlp-kcc`](https://pypi.org/project/khmer-nlp-kcc/) library (v0.2.8).  
Runs **word segmentation**, **POS tagging**, and **sentiment polarity** on Khmer text from a CSV file.

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

## Input Format

`input.csv` requires only one column: `text`.  
Add one Khmer sentence per row. No `id` column needed — it is auto-generated.

```csv
text
ខ្ញុំចូលចិត្តញ៉ាំបាយជាមួយគ្រួសារ
គាត់ទៅផ្សារទិញបន្លែនិងត្រី
ប្រទេសកម្ពុជាមានប្រវត្តិសាស្ត្រដ៏វែងឆ្ងាយ
```

---

## Usage

```bash
python kcc.py
```

---

## Output Format

Results are saved to `result_1.csv` with the following columns:

| Column | Description |
|---|---|
| `id` | Auto-generated row number |
| `original_text` | The original input sentence |
| `segmented` | Words split by spaces |
| `pos_tags` | POS tag per word — e.g. `ខ្ញុំ(PRO) \| ចូលចិត្ត(VB)` |
| `nova_pos` | Nova POS tag per word — e.g. `ខ្ញុំ(n-) \| ចូលចិត្ត(v)` |
| `polarity` | Sentiment label: `positive`, `neutral`, or `negative` |
| `confidence` | Confidence score for the predicted sentiment (0–1) |
| `all_scores` | Full probability breakdown for all 3 sentiment classes |

### Example output

| id | original_text | segmented | pos_tags | polarity | confidence |
|---|---|---|---|---|---|
| 1 | ខ្ញុំចូលចិត្តញ៉ាំបាយជាមួយគ្រួសារ | ខ្ញុំ ចូលចិត្ត ញ៉ាំ បាយ ជាមួយ គ្រួសារ | ខ្ញុំ(PRO) \| ចូលចិត្ត(VB) \| ញ៉ាំ(VB) \| បាយ(NN) | positive | 0.524 |
| 2 | គាត់ទៅផ្សារទិញបន្លែនិងត្រី | គាត់ ទៅ ផ្សារ ទិញ បន្លែ និង ត្រី | គាត់(PRO) \| ទៅ(VB) \| ផ្សារ(NN) \| ទិញ(VB_JJ) | neutral | 0.894 |

---

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
