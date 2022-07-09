---
layout: post
title: Deep NLP Chatbot Using a Seq2Seq Model
date: 2020-08-30 00:00:00 -0500
tags:
- machine learning
- nlp
- tensorflow
categories:
- Portfolio
---

Machine learning (ML) has been the tech buzzword of the decade. I first heard the term in reference to DeepMind's [legendary Go program](https://deepmind.com/research/case-studies/alphago-the-story-so-far), and it's been on my radar ever since. This summer, I tackled a project to build a [chatbot program](https://github.com/dlzou/dnlp-chatbot) that can respond to English human dialogue inputs with sentences. Sounds simple (it sure did to me at first), but there's a lot under the hood. (**Updated 2020-12-30**)

<!--more-->

{{< toc >}}

# Why Machine Learning, and How?

When anyone who's written code before is asked to build a chatbot, their first thought is probably: **if statements**. In fact, that's how many chatbots in the past and present are implemented, like many simple Discord bots or that nice phone lady who asks you to "press 0."

{{< tweet user="iamdevloper" id="830070592611172357" >}}

An obvious issue is that the input space is limited. To build a robust program for conversations, I have to handle some randomness and intepret inputs more deeply. This is where ML comes in.

Generally speaking, ML models are complex functions that map a set of inputs to a set of outputs. How does one treat an English sentence as input data? One simplistic model that accomplishes this is **bag-of-words**. In this model, you make note of words in a sentence without regard to order or frequency, which can easily be done by having a vector with thousands of elements---each corresponding to a word in the dictionary---and filling each element with 1 if it's in the sentence, or 0 otherwise. Convert a bunch of sentences to vectors like so, and we get a dataset for training a basic neural net.

However, simple is not always better, and it's no-brainer that word order is important to the meaning of a sentence. Unsatisfied by bag-of-words, I moved on to a more complex model called **seq2seq** (sequence-to-sequence). A seq2seq model has two components: an encoder takes an input and condenses its "information" (a very abstract concept) into a context vector, and a decoder reads that context to generate an output. It's worth noting that seq2seq has many more applications like translation, image captioning, and even solving differential equations. In my project, both encoder and decoder are implemented as <a href="#addendum-understanding-rnns">recurrent neural networks (RNNs)</a>.

The final piece to the puzzle is **attention**. In vanilla seq2seq, the encoder spits out a single vector that stores the context of the entire input, so problems occur when the input becomes longer. Attention mechanisms get around this by letting the decoder see the whole input sequence and focus on the parts it needs to. Attention is so powerful that some people want to completely ditch RNNs for it! But for now, both seem to have their place. Lilian Weng has a [great post](https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html) that explains attention.

# The Process

This being my first ML project, I relied on a lot of tutorials, articles, and papers to get off the ground. Luckily, the seq2seq model has already been studied for years, and there are many online resources to help a beginner like me accomplish my goal. 

The first step was to look for a large dataset on which I can train my seq2seq model. My search engine explorations led me to the [Cornell Movie-Dialogs Corpus](http://www.cs.cornell.edu/~cristian/Cornell_Movie-Dialogs_Corpus.html), an archive of over 200,000 lines of conversation taken assembled from hundreds of movies. I preprocessed the data by grouping the lines into conversations according to their metadata, then recording each pair of lines as the input/target pairs for my training/validation dataset. While working on data acquisition, I had a moment of realization: depending the data on which my model is trained, I can completely change its purpose! For example, if instead of CMDC I used a dataset of English-French sentence pairs, my chatbot would turn into a machine translation system, with minimal changes to the model itself.

I chose to build my model using the Python interface of TensorFlow 2, and finding my way around this huge library was its own learning curve, especially since TensorFlow provides multiple APIs for doing the same things. TensorFlow has a [full guide](https://www.tensorflow.org/tutorials/text/nmt_with_attention) for building a basic seq2seq model, but I also made many modifications like adding bidirectional RNN layers, changing the attention mechanism, and enabling static graph optimizations. The internet had me covered for pretty much everything I needed.

The time came to train my model, but this became my biggest obstacle. Although my PC is fairly powerful among laptops, it doesn't compare to the specialized, distributed solutions that are standard for the industry. The amount of training required to get reasonable results would take at least a week with my current setup, and I would have limited access to my computer that whole time. There's still hope; if I get access to some big servers and make use of the `tf.distributed` module, I can finish training and see the final results of this project.

# 2020-12-30 Update

After a four-mouth hiatus, I'm revisiting this project with more knowledge and resources.

One major feature I added is a **beam search decoder**. Compared to my previous implementation that used greedy search, which locally optimizes for the next word in a sequence, [beam search](https://towardsdatascience.com/an-intuitive-explanation-of-beam-search-9b1d744e7a0f) returns more optimal sequences overall. However, not all beam search decoders are created equal. My model only uses beam search at the evaluation stage to decode user input. A more comprehensive approach, as described by [Wiseman & Rush](https://arxiv.org/pdf/1606.02960.pdf), is to also use beam search during training and validation, but this involves defining a new loss function, plus some other complications.

The next part started with a small coincidence: after becoming a member of [Berkeley CSUA](https://www.csua.berkeley.edu/) root staff this past fall, I learned that the organization maintains a GPU cluster that is open to all students. This is exactly what I need! As I'm currently typing, my chatbot model is training remotely on an absolute unit of a computer. However, I still expect the process to take some time due to the lack of parallelizeable components in RNNs. Regardless of how smart (or dumb) my chatbot ends up being, I think this a fitting conclusion to the project.

# Addendum: Understanding RNNs

RNNs are important for understanding how seq2seq works. I'm far from qualified to give a full lesson on RNNs, but I still want to include a few remarks on what I've learned.

Neural networks often get compared to biological brains and take on a connotation of intelligence. This metaphor brings huge publicity, but I didn't find it useful for learning; I prefer [James Loy's interpretation](https://towardsdatascience.com/how-to-build-your-own-neural-network-from-scratch-in-python-68998a08e4f6) that neural networks are big vector functions. Feed in a vector, get out a vector.

RNNs adapt the basic neural network with artificial "memory" to deal with sequential data like sentences or audio. I find it convenient to think of RNNs as [discrete state models](https://en.wikipedia.org/wiki/State-space_representation):

$$
\vec{h}(k)=\vec{f}(\vec{x}(k),\vec{u}(k))\\\\
\vec{x}(k+1)=\vec{g}(\vec{x}(k),\vec{u}(k))
$$

Still vector functions, but with a twist: the next state (\\(\vec{x}\\)) of the model depends on its previous state as well as the new input (\\(\vec{u}\\)), which means the model state stores "memory" of the previous \\(0\\) through \\(k\\) inputs. The inputs to my chatbot program are the individual words in a sentence, and different inputs change the model state, leading to different outputs (\\(\vec{h}\\)). There are many variants of RNNs such as Gated Recurrent Units (which I used) and Long Short-Term Memory. [This Christopher Olah article](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) explains how these work in some detail, along with nice diagrams.

