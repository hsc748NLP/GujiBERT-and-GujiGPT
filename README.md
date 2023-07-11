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

## Data and Models
The data used in this model training comes from the website of Daizhige , which contains about 1.7 billion words of classical texts, and divides them into ten categories, such as Confucianism, Buddhism, History, and so on, with some of them in simplified Chinese characters and the others in traditional Chinese characters. In this study, the traditional and simplified data in the Daizhige corpus were firstly converted into traditional and simplified Chinese characters respectively, and this process was carried out by using the Chinese Character Simplified-Traditional Conversion Text Intelligence System  developed by Xiamen University, which provides three forms of online conversion, Word plug-in, and stand-alone software to realize the conversion of traditional and simplified Chinese characters, and in view of the large scale of the data, the data were converted into traditional and simplified Chinese characters by using the stand-alone software in the present study. Secondly, the converted data were cleaned to remove special symbols and invalid characters. Finally, the traditional and simplified data of Daizhige corpus are obtained respectively, and the two data are merged to form the mixed data of traditional and simplified, and the model is trained using the traditional, simplified and mixed data respectively.

In terms of baseline model selection, different baseline models are chosen according to the training corpus and pre-training tasks. Specifically, SikuBERT, SikuRoBERTa, and SikuGPT are used as baseline models for the traditional Chinese classics corpus and the mixed traditional and simple classics corpus, respectively, which are all trained by our group based on the traditional Chinese corpus of the Siku Quanshu. For the Simplified Chinese classics corpus, BERT-base-Chinese , Chinese-Roberta-wwm-ext  and GPT2-Chinese-cluecorpussmall  are used as baseline models.


## Downstream tasks
### Named Entity Identification
Through the recognition of words with specific meanings, such as human-named entities, place-named entities and time-word entities in ancient books, a finer-grained slicing of the ancient classics can be realized, which in turn helps the construction of the knowledge graph of classical texts and the application of classical text retrieval and translation.

In this study, we utilize the named entity recognition corpus of the Shiji to fine-tune the training of each base model, and on the basis of this, we realize the model construction and testing for the named entity recognition task. The Shiji is a detailed narrative, in which the characters, places and times recorded have great research value for named entity recognition in the field of ancient books. In this study, the corpus is divided into training set and test set according to the ratio of 9:1. The test results are shown in Table 1, from which it can be seen that the “Siku” and “Guji” series models developed by our group are better in the task of recognizing named entities in traditional Chinese ancient texts, with the F1 value about 4% higher than that of the baseline model RoBERTa; and in the task of sentence breaks in simplified Chinese ancient texts, the F1 value of Guji is about 4% higher than that of the baseline model RoBERTa. On the task of sentence breaking in simplified Chinese, GuwenBERT achieves the best performance, with an F1 value of 93.73%; on the mixed corpus of traditional Chinese and simplified Chinese, GujiBERT_jian_fan achieves the best performance, with an F1 value of 97.02%.

| training corpus | models | P(%) | R(%) | F1(%) |
| :----------------: | :----------: | :---------: | :---------: | :---------: |
| traditional | GujiBERT_fan | 92.8 | 94.28 | 93.53 | 
| traditional	| GujiRoBERTa_fan | 92.71 | 93.92 | 93.3 | 
| traditional	| SikuBERT | 92.5 | 93.92 | 93.2 | 
| traditional	| SikuRoBERTa | 92.43 | 93.73 | 93.07 | 
| traditional	| BERT-base-Chinese | 90.16 | 92.12 | 91.12 | 
| traditional	| Chinese-Roberta-wwm-ext | 88.86 | 90.65 | 89.75 | 
| simplified	| GujiBERT_jian | 91.93 | 93.55 | 92.73 | 
| simplified	| GujiRoBERTa_jian | 91.7 | 93.39 | 92.53 | 
| simplified	| BERT-base-Chinese | 87.36	89.82	88.57 | 
| simplified	| Chinese-Roberta-wwm-ext | 88.37	90.39	89.37 | 
| simplified	| GuwenBERT | 92.84 | 94.66 | 93.73 | 
| simplified + traditional | GujiBERT_jian_fan | 97.65 | 97.29 | 97.02 | 
| simplified + traditional | GujiRoBERTa_jian_fan | 95.91 | 96.78 | 96.34 | 
| simplified + traditional | BERT-base-Chinese | 95.75 | 96.53 | 96.14 | 
| simplified + traditional | Chinese-Roberta-wwm-ext | 94 | 95.33 | 94.66 | 
| simplified + traditional | RoBERTa-classical-Chinese-base-char | 94.76 | 94.83 | 94.76 | 

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
