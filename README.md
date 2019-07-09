# Kaggle : Quora Insincere Questions Classification

## Introduction

### On the competition 

> An existential problem for any major website today is how to handle toxic and divisive content. Quora wants to tackle this problem head-on to keep their platform a place where users can feel safe sharing their knowledge with the world.
Quora is a platform that empowers people to learn from each other. On Quora, people can ask questions and connect with others who contribute unique insights and quality answers. A key challenge is to weed out insincere questions -- those founded upon false premises, or that intend to make a statement rather than look for helpful answers.
In this competition, Kagglers will develop models that identify and flag insincere questions. To date, Quora has employed both machine learning and manual review to address this problem. With your help, they can develop more scalable methods to detect toxic and misleading content.
Here's your chance to combat online trolls at scale. Help Quora uphold their policy of “Be Nice, Be Respectful” and continue to be a place for sharing and growing the world’s knowledge.

See https://www.kaggle.com/c/quora-insincere-questions-classification/overview

The metric was the F1-Score, as the problem was an unbalanced binary classification one.

### Results

This competiton was the first one I really invested in. I did it solo, and ended up 26th out of 4037 (private).
My best model achieved 0.700 on the public leaderboard, which ranked about 400th, but the 0.688 CV model I selected was robust enough to perform well on the private leaderboard.

## Work overview

### Preprocessing : 

- Some special characters cleaning
- Number processing
- Contractions & mispells replacement 
- Latex tags cleaning.
- No lowering though

## Embeddings 

Concatenation of glove, fasttext and paragram.
4 embeddings were made available by the organisers, I kept those three.

### Features : 

- Toxic words ratio
- Total length
- word vs unique words
- ratio of capital letters

### Model:

Single model, 5 folds, 4 epochs :
- Embedding layer + some noise
- LSTM, 64 Units (unidirectional)
- GRU, 32 Units (unidirectional)
- Attention, maxpool & average pool on the outputs of both rnns
- Concatenating them with features
- 32 units dense + reLu + Batchnorm + Dropout
- And the final layer

## Additional work :

Here are some kernels I made public during the competiton :

- [Text processing for embeddings](https://www.kaggle.com/theoviel/improve-your-score-with-some-text-preprocessing)
- [Text processing for embeddings with performance comparison](https://www.kaggle.com/theoviel/improve-your-score-with-text-preprocessing-v2)
- [Augmenting insincere texts with word embeddings](https://www.kaggle.com/theoviel/using-word-embeddings-for-data-augmentation)
- [Augmenting insincere texts with SMOTE](https://www.kaggle.com/theoviel/dealing-with-class-imbalance-with-smote)
- [Applying usual cleaning methods to our problem](https://www.kaggle.com/theoviel/should-you-clean-your-data)
