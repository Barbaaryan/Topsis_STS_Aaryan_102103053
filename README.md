# Comparative Performance Analysis of Different Pre-trained Models for Text Sentence Similarity using Topsis

## Overview

Text Sentence Similarity is the task of determining how similar two texts are. Sentence similarity models convert input texts into vectors (embeddings) that capture semantic information and calculate how close (similar) they are between them. This task is particularly useful for information retrieval and clustering/grouping.

## Models

I have selected the following 5 pre-trained models from [Hugging Face](https://huggingface.co/):

1. [FlagEmbedding](https://huggingface.co/BAAI/bge-large-en-v1.5) - BAAI/bge-large-en-v1.5

2. [LLMRails](https://huggingface.co/llmrails/ember-v1) - llmrails/ember-v1

3. [Universal AnglE Embedding](https://huggingface.co/WhereIsAI/UAE-Large-V1) - WhereIsAI/UAE-Large-V1

4. [sf_model_e5](https://huggingface.co/jamesgpt1/sf_model_e5) - jamesgpt1/sf_model_e5

5. [General Text Embeddings (GTE) model](https://huggingface.co/thenlper/gte-large) - thenlper/gte-large

## Metrics

I have used the following 6 metrics to compare the performance of the models:

1. **cos_sim_pearson:**

Weight: 2

Impact: +

Reasoning: Higher values of Pearson correlation coefficient for cosine similarity indicate a stronger linear relationship between the model's cosine similarity scores and the gold standard similarity scores. Maximizing this coefficient ensures that the model's cosine similarity scores correlate closely with the gold standard scores in a linear fashion.

2. **cos_sim_spearman:**

Weight: 2

Impact: +

Reasoning: Higher values of Spearman's rank correlation coefficient for cosine similarity indicate a stronger monotonic relationship between the model's cosine similarity scores and the gold standard similarity scores. Maximizing this coefficient ensures that the model's rankings of sentence pairs based on cosine similarity align well with the rankings provided by the gold standard.

3. **euclidean_pearson:**

Weight: 1

Impact: -

Reasoning: Lower values of Pearson correlation coefficient for Euclidean distance indicate a weaker linear relationship between the model's Euclidean distance scores and the gold standard similarity scores. Minimizing this coefficient ensures that the model's Euclidean distance scores correlate closely with the gold standard scores in a linear fashion.

4. **euclidean_spearman:**

Weight: 1

Impact: -

Reasoning: Lower values of Spearman's rank correlation coefficient for Euclidean distance indicate a weaker monotonic relationship between the model's Euclidean distance scores and the gold standard similarity scores. Minimizing this coefficient ensures that the model's rankings of sentence pairs based on Euclidean distance align well with the rankings provided by the gold standard.

5. **manhattan_pearson:**

Weight: 1

Impact: -

Reasoning: Lower values of Pearson correlation coefficient for Manhattan distance indicate a weaker linear relationship between the model's Manhattan distance scores and the gold standard similarity scores. Minimizing this coefficient ensures that the model's Manhattan distance scores correlate closely with the gold standard scores in a linear fashion.

6. **manhattan_spearman:**

Weight: 1

Impact: -

Reasoning: Lower values of Spearman's rank correlation coefficient for Manhattan distance indicate a weaker monotonic relationship between the model's Manhattan distance scores and the gold standard similarity scores. Minimizing this coefficient ensures that the model's rankings of sentence pairs based on Manhattan distance align well with the rankings provided by the gold standard.

## Datasets

I have used the following 10 datasets to compare the performance of the models:

1. [BIOSSES](https://huggingface.co/datasets/mteb/biosses-sts) - Biomedical Semantic Similarity Estimation.

2. [SICK-R](https://huggingface.co/datasets/mteb/sickr-sts) - Semantic Textual Similarity SICK-R dataset

3. [STS12](https://huggingface.co/datasets/mteb/sts12-sts) - SemEval STS 2012 dataset.

4. [STS13](https://huggingface.co/datasets/mteb/sts13-sts) - SemEval STS 2013 dataset.

5. [STS14](https://huggingface.co/datasets/mteb/sts14-sts) - SemEval STS 2014 dataset.

6. [STS15](https://huggingface.co/datasets/mteb/sts15-sts) - SemEval STS 2015 dataset

7. [STS16](https://huggingface.co/datasets/mteb/sts16-sts) - SemEval STS 2016 dataset

8. [STS17](https://huggingface.co/datasets/mteb/sts17-crosslingual-sts) - STS 2017 dataset

9. [STS22](https://huggingface.co/datasets/mteb/sts22-crosslingual-sts) - SemEval 2022 Task 8: Multilingual News Article Similarity

10. [STSBenchmark](https://huggingface.co/datasets/mteb/stsbenchmark-sts) - Semantic Textual Similarity Benchmark (STSbenchmark) dataset.

## Library 

I have refered to [MTEB: Massive Text Embedding Benchmark](https://arxiv.org/abs/2210.07316) research paper. I have used the scripts available at their [GitHub](https://github.com/embeddings-benchmark/mteb/tree/main) to calculate the metrics.

I have used my own topsis python package uploaded to PyPi to perform the topsis ananlysis on the data. To check out my package click [here](https://pypi.org/project/topsis-aaryan-102103053/).

## Results

|Dataset|Rank 1 Model|
|:-:|:-:|
|BIOSSES|gte-large|
|SICK-R|UAE-Large-V1|
|STS12|sf_model_ef|
|STS13|UAE-Large-V1|
|STS14|ember-v1|
|STS15|ember-v1|
|STS16|bge-large-en-v1.5|
|STS17|ember-v1|
|STS22|UAE-Large-V1|
|STSBenchmark|ember-v1|

## Bar Chart

The bar chart visually represents the amount of times each model has recieved a specific rank.

![Bar Chart](https://github.com/Barbaaryan/Topsis_STS_Aaryan_102103053/blob/main/Comparision.jpg?raw=true)

## Analysis

ember-v1 has recieved **1st Rank** in *4 out of 10* evaluation datasets. 

UAE-Large-V1 has recieved **1st Rank** in  *3 out of 10* evaluation datasets.

If you have to choose between the five models I have chosen. You can try ember-v1 and UAE-Large-V1 and choose the model which performs your task better.

## Disclaimer

*Note: I have tried my best to balance the weights of the different metrics I have chosen but depending on your task there may be more important metrics and their weightage may be different.*
