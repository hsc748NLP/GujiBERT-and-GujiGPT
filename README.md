# GujiBERT-and-GujiGPT

## Pretrain-models
[GujiBERT](https://huggingface.co/hsc748NLP/GujiBERT)

[GujiGPT](https://huggingface.co/hsc748NLP/GujiGPT)

## Baselines
[SikuBERT](https://github.com/hsc748NLP/SikuBERT-for-digital-humanities-and-classical-Chinese-information-processing)

[SikuGPT](https://github.com/hsc748NLP/SikuGPT)

## Data
All ancient classic corpus of Yin Zhige

## Downstream tasks
### Part-of-speech tagging
|  pretrained models  | P(%) | R(%) | F1-score(%) |
| :----------------: | :----------: | :---------: | :---------: |
| SikuBERT | 90.52 | 90.93 | 90.69 |
| GujiBERT | 90.68 | 91.10 | 90.85 |

### Broken sentences
|  pretrained models  | P(%) | R(%) | F1-score(%) |
| :----------------: | :----------: | :---------: | :---------: |
| SikuBERT | 75.00 | 75.59 | 75.29 |
| GujiBERT | 76.39 | 77.73 | 77.06 |

### Named entity recognition
|  pretrained models  | P(%) | R(%) | F1-score(%) |
| :----------------: | :----------: | :---------: | :---------: |
| SikuBERT | 89.35 | 89.94 | 89.63 |
| GujiBERT | 90.44 | 90.42 | 90.34 |

### Machine translation
|  pretrained models  | BLEU-1 | BLEU-2 | BLEU-3 | BLEU-4 |
| :----------------: | :----------: | :---------: | :---------: | :---------: |
| SikuGPT | 0.765 | 0.593 | 0.488 | 0.413 |
| GujiGPT | 9.765 | 0.593 | 0.489 | 0.413 |

## How to use

### Huggingface Transformers

```python

from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("hsc748NLP/GujiGPT")

model = AutoModelForCausalLM.from_pretrained("hsc748NLP/GujiGPT")

```
