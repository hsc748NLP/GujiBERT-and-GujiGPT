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
| traditional | GujiBERT_fan | 90.49 | 91.03 | 90.74 | 
| traditional | GujiRoberta_fan | 90.47 | 91.02 | 90.73 | 
| traditional | SikuBERT | 90.48 | 90.98 | 90.68 | 
| traditional | SikuRoBERTa | 90.21 | 90.87 | 90.52 | 
| traditional | Bert-base-Chinese | 89.62	90.36	89.93 | 
| traditional | Chinese-RoBERTa-wwm-ext | 88.96 | 89.95 | 89.43 | 
| simplified | GujiBERT_jian | 90.66 | 91.25 | 90.94 | 
| simplified | GujiRoberta_jian | 90.04 | 90.72 | 90.36 | 
| simplified | Bert-base-Chinese | 89.75 | 90.49 | 90.07 | 
| simplified | Chinese-Roberta-wwm-ext | 89.17 | 90.07 | 89.6 | 
| simplified | GuwenBERT | 90.56 | 91.27 | 90.89 | 
| simplified + traditional | GujiBERT_jian_fan | 93.76 | 93.83 | 93.76 | 
| simplified + traditional | GujiRoberta_jian_fan | 93.22 | 93.48 | 93.3 | 
| simplified + traditional | Bert-base-Chinese | 93.05 | 93.36 | 93.16 | 
| simplified + traditional | Chinese-Roberta-wwm-ext | 92.37 | 92.76 | 92.54 | 
| simplified + traditional | RoBERTa-classical-Chinese-base-char | 92.56 | 92.64 | 92.58 | 

### Segmentation and Lexical Labeling
In the process of constructing the base language model for intelligent information processing of ancient books, the quality of participle and lexical annotation has a key impact on text mining, knowledge graph presentation, and named entity recognition of classics. In this study, based on the corpus of Zuozhuan, the base model is fine-tuned, trained, and tested in order to construct an integrated labeling model of ancient Chinese participle and lexical annotation. The corpus of Zuozhuan is created and released by the Chinese information processing research team led by Prof. Chen of Nanjing Normal University, which consists of about 180,000 words, uses 17 kinds of classical markers designed by themselves, and has been proofread for four times, so that the quality of the corpus is guaranteed. In this study, the database is divided into three types of datasets: traditional Chinese characters, simplified Chinese characters, and mixed simplified and traditional Chinese characters, to explore the performance of each base model in the three types of datasets, and the test results are shown in follow.
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

### Sentences Breaking
The texts recorded in the original classics usually do not have punctuation marks. Sentence breaking aims at adding sentence separators to unpunctuated ancient texts, which not only enhances the readability of the ancient Chinese texts, but also guarantees the processing of different levels of textual information.
In this study, we utilize the corpus of the Twenty-Four Histories to fine-tune the models, construct an ancient Chinese sentence breaking model for the automatic sentence breaking task, and test the performance of the model. The ancient Chinese corpus of the Twenty-Four Histories selected in this study is extracted from The Complete Translation of the Twenty-Four Histories compiled under the auspices of Xu Jialu and others, which has been carefully proofread by many experts and is of high quality, and the corpus contains sentence breakage markers. In this study, 300,000 sentences are selected, and the corpus is divided into training set and test set according to the ratio of 9:1, and the test results are shown in follow. It can be seen that the “Siku” and “Guji” series of models developed by our group have obvious advantages over the general models in the task of sentence breaking in traditional Chinese. The best performance is achieved by GujiRoBERTa_fan, with an F1 value of 86.31%; in the task of simplified ancient text sentence breakage, GuwenBERT achieves the best performance, and GujiRoBERTa_jian achieves the second best performance, with a difference of about 3 percentage points. This is due to the fact that GuwenBERT's base model is Chinese-BERT-wwm for the Simplified Chinese task, and the corpus on which GuwenBERT continues to be pre-trained is a large-scale Simplified Ancient Chinese, whereas GujiBERT was obtained based on SikuBERT for Traditional Ancient Chinese, and SikuBERT's stronger Traditional Ancient Chinese domain may weaken the GujiBERT's ability to deal with Simplified Ancient Chinese; on the mixed corpus of Traditional Ancient Chinese and Simplified Ancient Chinese, RoBERTa-classical-Chinese-base-char performs optimally, which is on the one hand, due to the fact that the base model of RoBERTa-classical-Chinese-base-char is GuwenBERT, on the other hand, although the Simplified Chinese and Traditional Chinese corpus in this task have the same number of characters, the Traditional Chinese has more characters with the same morphology as its Simplified form, so the total number of Simplified Chinese characters is more, which makes RoBERTa-classical-Chinese-base-char perform better. The above results also corroborate the effectiveness of continued pre-training of the model's domainization, highlighting the need for pre-training language models for traditional Chinese.
| training corpus | models | P(%) | R(%) | F1(%) |
| :----------------: | :----------: | :---------: | :---------: | :---------: |
| traditional | GujiBERT_fan | 84.90 | 85.85 | 85.37 | 
| traditional | GujiRoBERTa_fan | 85.87 | 86.75 | 86.31 | 
| traditional | SikuBERT | 84.12 | 85.16 | 84.63 | 
| traditional | SikuRoBERTa | 85.06 | 85.96 | 85.51 | 
| traditional | BERT-base-Chinese | 78.78 | 79.92 | 79.35 | 
| traditional | Chinese-RoBERTa-wwm-ext | 77.34 | 78.16 | 77.75 | 
| simplified | GujiBERT_jian | 83.29 | 84.20 | 83.74 | 
| simplified | GujiRoBERTa_jian | 83.47 | 84.38 | 83.92 | 
| simplified | BERT-base-Chinese | 78.86 | 79.74 | 79.30 | 
| simplified | Chinese-RoBERTa-wwm-ext | 77.44 | 78.15 | 77.80 | 
| simplified | GuwenBERT | 86.96 | 87.41 | 87.18 | 
| simplified + traditional | GujiBERT_jian_fan | 86.03 | 86.88 | 86.45 | 
| simplified + traditional | GujiRoBERTa_jian_fan | 86.44 | 87.12 | 86.78 | 
| simplified + traditional | BERT-base-Chinese | 80.90 | 81.76 | 81.33 | 
| simplified + traditional | Chinese-RoBERTa-wwm-ext | 79.98 | 80.61 | 80.29 | 
| simplified + traditional | RoBERTa-classical-Chinese-base-char | 87.65 | 88.04 | 87.85 | 

### Automatic Punctuation
Automatic punctuation of ancient Chinese refers to the use of Chinese current “Punctuation Usage” (GB/T 15834-2011) specification for the original ancient texts without punctuation automatically add punctuation, not only makes the processed ancient texts more in line with the reading habits of modern people, but also is the basis for the realization of the fine-grained processing of ancient texts. In this section, we use the twenty-five pre-Qin canonical texts that have been manually labeled and proofread by our group for automatic punctuation experiments. In order to fully improve the generalization ability of the model, this study selects 189798 corpora with sufficient length for training to ensure that the model can learn richer semantic representations. In the data processing stage, this study divides the dataset according to the ratio of 8:1:1, and after removing all the punctuation in the dataset, the data are processed using the BIO annotation format to ensure that the label corresponding to the previous character at the punctuation position in the original text is the punctuation label in the label set.
On the task of automatic punctuation of Chinese classics, all the ancient Chinese base models have gained advantages over the generalized models, among which, on the task of punctuation of traditional ancient Chinese, the performance of GujiBERT_fan and GujiRoBERTa_fan models we developed is significantly better than that of the “Siku” series models. Among them, GujiRoBERTa_fan achieves the best performance with the highest F1 value of 76.00%. On the task of automatic punctuation of simplified text, GuwenBERT achieves the best performance with the highest F1 value of 77.19%, which is slightly higher than that of “Guji” series model, and this difference may be related to the word list and the training corpus. The GujiRoBERTa_jian_fan model achieves the best performance on the mixed corpus of traditional Chinese and simplified Chinese, with the highest F1 value of 78.53%, and the RoBERTa-classical-Chinese-base-char model achieves the second best performance, with the highest F1 value of 78.47%, due to the fact that it is trained from the GuwenBERT model. GuwenBERT model, it also inherits the efficient automatic punctuation of GuwenBERT model. Taking the above tasks together, we find that the GuwenBERT family of models may be more suitable for handling automatic sentence breaking and punctuation tasks, probably because GuwenBERT streamlines the vocabulary lists and retrains the word embedding representations.
| training corpus | models | P(%) | R(%) | F1(%) |
| :----------------: | :----------: | :---------: | :---------: | :---------: |
| traditional | GujiBERT_fan | 75.96 | 76.93 | 76.00 | 
| traditional | GujiRoBERTa_fan | 76.06 | 77.03 | 76.09 | 
| traditional | SikuBERT | 75.68 | 76.60 | 75.69 | 
| traditional | SikuRoBERTa | 75.73 | 76.97 | 75.91 | 
| traditional | BERT-base-Chinese | 73.99 | 74.85 | 73.91 | 
| traditional | Chinese-RoBERTa-wwm-ext | 73.94 | 74.59 | 73.71 | 
| simplified | GujiBERT_jian | 75.76 | 76.51 | 75.68 | 
| simplified | GujiRoBERTa_jian | 75.35 | 76.30 | 75.42 | 
| simplified | BERT-base-Chinese | 74.50	75.07	74.20 | 
| simplified | Chinese-RoBERTa-wwm-ext | 74.47 | 75.00 | 74.17 | 
| simplified | GuwenBERT | 77.02 | 78.45 | 77.19 | 
| simplified + traditional | GujiBERT_jian_fan | 77.53 | 78.32 | 77.92 | 
| simplified + traditional | GujiRoBERTa_jian_fan | 78.14 | 78.93 | 78.53 | 
| simplified + traditional | BERT-base-Chinese | 75.69 | 75.15 | 75.42 | 
| simplified + traditional | Chinese-RoBERTa-wwm-ext | 75.93 | 75.84 | 75.88 | 
| simplified + traditional | RoBERTa-classical-Chinese-base-char | 78.06 | 78.89 | 78.47 | 

### Machine Translation
Natural Language Generation (NLG) task is an important branch in the field of intelligent information processing, covering subtasks such as text summarization, machine translation, dialog systems and so on. In this study, in order to investigate the specific performance of base models on the natural language generation task, the models are evaluated using the machine translation subtask. In this evaluation task, the book “Twenty-four Histories in Full Translation”, a key book of the National “Tenth Five-Year” Publishing Plan, was chosen as the data source. One million sets of roughly processed parallel corpus of the Twenty-four Histories were obtained through the Aligner tool and several rounds of manual proofreading. 
On the basis of completing the corpus construction, in order to accurately assess the actual translation ability (text generation ability) from ancient Chinese to modern Chinese of each model, the study adopted BLEU as the main evaluation index of the experiment. All models used the same experimental configuration information, and after five rounds of training, the evaluation results of the generated content of each model are shown in follow.
| training corpus | models | BLEU1 | BLEU2 | BLEU3 | BLEU4 |
| :----------------: | :----------: | :---------: | :---------: | :---------: | :---------: |
| traditional | SikuGPT | 0.714 | 0.505 | 0.383 | 0.297 | 
| traditional | GujiGPT_fan | 0.715 | 0.507 | 0.385 | 0.299 | 
| traditional | GPT2-base-Chinese | 0.715 | 0.507 | 0.385 | 0.299 | 
| simplified | GPT2-Chinese-ancient | 0.712 | 0.503 | 0.381 | 0.295 | 
| simplified | GujiGPT_jian | 0.715 | 0.505 | 0.383 | 0.298 | 
| simplified + traditional | GujiGPT_jian_fan | 0.715 | 0.507 | 0.385 | 0.299 | 

## How to use

### Huggingface Transformers

```python

from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("hsc748NLP/GujiGPT")

model = AutoModelForCausalLM.from_pretrained("hsc748NLP/GujiGPT")

```
