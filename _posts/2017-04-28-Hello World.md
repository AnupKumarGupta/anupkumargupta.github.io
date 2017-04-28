---
layout: post
title:  "Word2Vector"
excerpt: "This tutorial covers the skip gram neural network architecture for Word2Vec. We will cover, what are word vectors? What are different approaches to build a Word2Vec system ? Finally we dive deep and will try to build word2vec, the skip-gram model.."
---

This tutorial covers the skip gram neural network architecture for Word2Vec. We will cover, what are word vectors ? What are different approaches to build a Word2Vec system ? Finally we dive deep and will try to build word2vec, the skip-gram model. 

Let's begin then...

Machine learning applications on Natural Language are an extremely important tool in the data scientist’s toolbox. One can implement autocompleter, auto-suggester, spam detector in your spam folder or even a text summarizer. When we are playing around with text data, we come across one of the most important aspect :  `text classification`. 

In text classification, the data scientist tries to develop an algorithm that can figure out what a piece of text says. For example if we are given a word or phrase,the system must be able to figure out whether it is related to  a provided article or not? Or whether a proposed title is appropriate for a given novel or not?

So how will one tackle the problem of relating a word to an article ? One of the most naive approach is to take the word, simply scan the article and find out the occurrence of the word. But is it failproof?  

I guess no. Lets explore some pitfalls of a naive approach to the classification problem.In many cases traditional text classification can be difficult to scale, because of the order of the vocabulary, which counts in the thousands or tens of thousands. In such a case applying a naive approach may not end up with desired results. 

Considering the above mentioned articles on cats. If we naively  try to find the words "kitty" or "kitten", we may end up stating that the words are not all related to the article. Moreover this approach requires a great extent of human intervention. 

One solution to these problem is to move to Word2Vec for the processing of our unstructured text data. Word2Vec (W2V) is an algorithm that takes every word in our vocabulary and turns it into a unique vector that can be added, subtracted, and manipulated in ways just like a vector in space.

Once these vectors are generated, they end up displaying very interesting relationships between one another. Since the vectors are mathematical entities, we can perform operations such as adding and subtraction on them. We can get amazing results by creating simple word vector equations such:

`KING - MALE + FEMALE = QUEEN`
  
Also its worth mentioning that, words with similar meaning tend to have [similar vectors](https://en.wikipedia.org/wiki/Cosine_similarity). 
In words of J.R.Firth 

> "You shall know a word by the company	it keeps"

Now lets dive down, how to start build up these vectors. At first step we start with something known as `one hot encoding vector`. A `one hot encoding vector` is a vector with one 1 and other entries as 0s. Let's learn about it, with a small example. Consider a vocabulary with 4 words, {cat, dog, man, kitty}. Now the one hot encoding vector for each word will be of shape `1 X size_of_vocab` which turns out to `1 X 4`. The vectors for this vocab will be as follows:

```
cat :   [1 0 0 0 ]
dog :   [0 1 0 0 ]
man :   [0 0 1 0 ]
kitty : [0 0 0 1 ]
```

A point worth noting is that no two vectors have 1 at same index. Also it's clear that till now, there is no natural	notion of similarity in	a set of one-hot vectors. We aim that somehow, we modify these vectors such that, two words with a similar meaning have similar vectors. We will try to achieve something like this.

```
cat :   [1.0  0.2  0.3  0.9 ]
kitty : [0.9  0.1  0.1  1.0 ]
man :   [0.1  0.3  1.0  0.3 ]
```

We can now see that there is a sense of similarity between cat and kitty, but at the same time man differs from cat or kitty from a great distance.

---
We will try to define a model that aims to predict the context words given a center word.

$$ P(context\mathbin{\vert} W_t > 0) $$ 

where W_t is the center word. Our model will have a loss function. 

$$ J = 1 - P( W_{-t} \mathbin{\vert} W_t  ) $$


Where $ W_{-t} $ are all the words except the center word. We try to put almost all words of the corpus as the center word $ W_t $ and perform operations such as to minimize the loss. We keep adjusting the vector representations of words so as to minimize this loss. The basic idea is to have a model that tries to predict from given input, calculates loss and then tries to minimize it. ( _Good Boy Model_)

We have two brilliant ways to perform this task of minimizing the loss. There are two algorithms:

1. Continuous Bag of Words (CBOW)
2. Skip-grams (SG)

Algorithmically,both of these architectures are similar, except that CBOW predicts center words from context words, while the skip-gram does the inverse and predicts source context-words from the center words. 

For example, if we have the sentence: _"The quick brown fox jumps"_, then CBOW tries to predict _"brown"_ from _"the"_, _"quick"_, _"fox"_ and _"jumps"_, while Skip-Gram tries to predict _"the"_, _"quick"_, _"fox"_ and _"jumps"_ from _"brown"_.

---
######Word2Vec using Skip Gram model

For a given word( i.e. center word) we will try to predict surroundings words in a window of radius(say m).

---
######Equations and Figures

---
/*Lets us talk in mathematical equations. Suppose we T words, labeled as t=1,2..T.

For each word t belonging to T, we will calculate probability of occurrence of surrounding words in a radius of 'm'.
*/

We have our objective function something like this, 

  


---
######More is yet to come

---






