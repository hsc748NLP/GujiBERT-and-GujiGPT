# GujiBERT-and-GujiGPT
## Introduction
With the rapid development of artificial intelligence, large language models are increasingly playing a key role. The combination of natural language processing comprehensive and generative language models such as BERT and GPT with datasets of vertical domains has generated numerous domainized language models. The domainized language models have greatly contributed to the development of intelligence in the corresponding domains, such as mathematics, chemistry, finance, law, and so on. As the main carrier of Chinese civilization, Chinese classics have a large span of history in time, massive data scale, and multiple categories in data types. The above characteristics of Chinese classics data have the basis for constructing a domainized Pedestal Language Model (DPLM). Some studies have constructed the corresponding domainized base language model for Chinese classics, but the constructed model has the following shortcomings. Firstly, some models use relatively small datasets and are either simplified or traditional in terms of characters, without considering the coexistence of simplified and traditional characters. Secondly, the constructed models are mainly based on the understanding of natural language processing and lack the construction of natural language processing generative models. Finally, the determination and validation of the model performance is relatively single, not comprehensive and lacks validation on public datasets. Against this background, based on the currently available datasets of ancient books, taking into account both traditional and simplified character sets, and oriented to the two tasks of comprehension and generation of natural language processing, and with the goal of intelligent information processing of ancient books, this paper constructs the base language models for comprehension and generation of natural language processing of Chinese classics, which are named GujiBERT and GujiGPT.

## Pretrain-models
[GujiBERT_fan](https://huggingface.co/hsc748NLP/GujiBERT_fan)
[GujiRoBERTa_fan](https://huggingface.co/hsc748NLP/GujiRoBERTa_fan)
[GujiGPT_fan](https://huggingface.co/hsc748NLP/GujiGPT_fan)

[GujiBERT_jian](https://huggingface.co/hsc748NLP/GujiBERT_jian)
[GujiRoBERTa_jian](https://huggingface.co/hsc748NLP/GujiRoBERTa_jian)
[GujiGPT_jian](https://huggingface.co/hsc748NLP/GujiGPT_jian)

[GujiBERT_jian_fan](https://huggingface.co/hsc748NLP/GujiBERT_jian_fan)
[GujiRoBERTa_jian_fan](https://huggingface.co/hsc748NLP/GujiRoBERTa_jian_fan)
[GujiGPT_jian_fan](https://huggingface.co/hsc748NLP/GujiGPT_jian_fan)

## Baselines
[SikuBERT](https://github.com/hsc748NLP/SikuBERT-for-digital-humanities-and-classical-Chinese-information-processing)

[SikuRoBERTa](https://github.com/hsc748NLP/SikuBERT-for-digital-humanities-and-classical-Chinese-information-processing)

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
| GujiGPT | 0.765 | 0.593 | 0.489 | 0.413 |

## How to use

### Huggingface Transformers

```python

from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("hsc748NLP/GujiGPT")

model = AutoModelForCausalLM.from_pretrained("hsc748NLP/GujiGPT")

```
