# MisInfoShort-22K

## A Short-Text Multi-Domain Misinformation Detection Benchmark

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

---

## What is this dataset?

MisInfoShort-22K is a research dataset for training AI models to detect
misinformation in short texts. It contains 20,000 short text samples
(between 5 and 40 words each), simulating the kind of content shared on
social media, WhatsApp, forums, and comment sections.

Each sample is labelled and annotated with rich metadata to support
multiple research tasks.

---

## Why is it useful?

Most existing misinformation datasets use long news articles.
This dataset focuses on SHORT texts — exactly how misinformation
actually spreads online (tweets, forwards, captions, comments).

| Dataset      | Short Text | 5 Domains | Emotion Labels | Satire Class |
|--------------|-----------|-----------|---------------|-------------|
| LIAR         | ✗         | ✗         | ✗             | ✗           |
| FakeNewsNet  | ✗         | Partial   | ✗             | ✗           |
| PHEME        | Partial   | ✗         | ✗             | ✗           |
| **MisInfoShort-22K** | **✓** | **✓** | **✓**     | **✓**       |

---

## Dataset Numbers

| Property              | Value        |
|-----------------------|-------------|
| Total samples         | 20,000       |
| Training samples      | 16,000       |
| Validation samples    | 2,000        |
| Test samples          | 2,000        |
| Domains               | 5            |
| Label classes         | 4            |
| Average text length   | ~18 words    |
| Language              | English      |
| License               | CC BY 4.0    |

---

## Label Distribution

| Label           | Count  | Percentage |
|-----------------|--------|-----------|
| misinformation  | ~5,400 | ~27%      |
| factual         | ~4,900 | ~24.5%    |
| satire          | ~4,900 | ~24.5%    |
| opinion         | ~4,800 | ~24%      |

---

## Domain Distribution

| Domain     | Count  | Percentage |
|------------|--------|-----------|
| health     | ~4,800 | ~24%      |
| science    | ~4,100 | ~20.5%    |
| technology | ~4,000 | ~20%      |
| politics   | ~3,900 | ~19.5%    |
| finance    | ~3,200 | ~16%      |

---

## Column Descriptions

| Column               | What it means                                              |
|----------------------|------------------------------------------------------------|
| `id`                 | Unique ID for each sample (e.g. MIS-3F2A1B)               |
| `text`               | The short text sample (5–40 words)                         |
| `label`              | Main label: misinformation, factual, opinion, satire       |
| `misinformation_type`| Sub-type: conspiracy, medical_claim, propaganda, scam, rumor, myth, none |
| `domain`             | Topic: health, politics, finance, technology, science      |
| `semantic_focus`     | Fine topic: cure_claim, election_fraud, investment_promise, technology_fear, scientific_misinterpretation, policy_claim, economic_prediction |
| `emotion_trigger`    | Primary emotion: fear, anger, urgency, curiosity, hope, neutral |
| `emotion_secondary`  | Second emotion for multi-label modeling (or "none")        |
| `source_type`        | Where it came from: social_media, blog, messaging_app, forum, comment |
| `text_length`        | Number of words in the text                                |

---

## Files in this Dataset

| File              | Description                  | Rows   |
|-------------------|------------------------------|--------|
| dataset.csv       | Complete dataset              | 20,000 |
| train.csv         | Training split (80%)          | 16,000 |
| validation.csv    | Validation split (10%)        | 2,000  |
| test.csv          | Test split (10%)              | 2,000  |

---

## How to Load
```python
import pandas as pd

# Load full dataset
df = pd.read_csv("dataset.csv")
print(df.shape)
print(df.head())

# Load splits
train = pd.read_csv("train.csv")
val   = pd.read_csv("validation.csv")
test  = pd.read_csv("test.csv")
```

---

## Suggested Research Tasks

1. Binary: misinformation vs. not misinformation
2. 4-class: misinformation / factual / opinion / satire
3. 7-class: misinfo subtype detection
4. Emotion trigger prediction
5. Multi-label emotion modeling
6. Domain classification
7. Multi-task learning

---

## Recommended Models to Fine-tune

- `bert-base-uncased`
- `roberta-base`
- `distilbert-base-uncased`
- `microsoft/deberta-v3-base`

---

## How was it created?

This dataset was synthetically generated using a slot-based template
pipeline in Python. Templates were filled with large vocabulary banks
across 20 domain/label combinations. After generation, it went through
multi-stage deduplication, validation, and stratified splitting.

Reproducible with `random_seed = 42`.

---

## License

Creative Commons Attribution 4.0 (CC BY 4.0)
You can use, share, and adapt this dataset for any purpose
as long as you give credit.

---

## Citation
```bibtex
@dataset{misinfoshort22k_2024,
  title   = {MisInfoShort-22K: A Short-Text Multi-Domain Misinformation
             Detection Benchmark with Emotional and Semantic Metadata},
  year    = {2024},
  version = {1.0.0},
  doi   = {10.5281/zenodo.19019703},
  license = {CC BY 4.0}
}
```
```

---

