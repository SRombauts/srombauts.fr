---
title:  "Recurrent Neural Networks with TensorFlow"
date:   2017-04-20 22:00:00 +0200
tags:
  - ai
  - github
---

Earlier this month I read one of OpenAI's early blog posts, ["Unsupervised sentiment neuron"][sentiment-neuron].
They trained a 4,096-unit LSTM to predict the next character across 82 million Amazon reviews.
Without sentiment labels, they discovered that a single "neuron" had learned to classify whether a review was positive or negative.
I read the article during a family vacation in Spain, and it immediately caught my imagination!

The phrase "predicting the next character" linked to Andrej Karpathy's 2015 article ["The Unreasonable Effectiveness of Recurrent Neural Networks"][rnn-effectiveness].
It is a clear introduction to recurrent neural networks and character-level language models.
Karpathy showed models trained on Shakespeare, Linux source code and LaTeX.
I was amazed by it! I had no doubt that the results were real, but some of my colleagues were skeptical when I told them about it.
From that moment, I wanted to try it on our own internal data, both as a proof of concept and as a learning exercise.
Thankfully, Karpathy had released the accompanying [char-rnn][char-rnn] code in Torch and Lua.

I was following Google's work in AI and wanted an excuse to learn some TensorFlow.
Rather than port Karpathy's code myself, I looked for an existing implementation and found Sherjil Ozair's [char-rnn-tensorflow][upstream].
It provided the same basic experiment in Python with TensorFlow 1.0: train an LSTM on a text file, save checkpoints, then sample new text one character at a time.

I [forked the project][fork] and made a few small changes while learning my way around it.
I added better reporting for the training loss and model parameters, improved the command-line help and documentation,
and added the English text of Tolstoy's *War and Peace* as another corpus.

I ran the experiment at my day job. I am working in the embedded R&D team at INEO Systrans, where we have years of development history in Git.
I exported all our commit messages into a training file and asked the network to invent new ones. :sweat_smile:

Most of the results were surprisingly well formatted. From a distance, they looked like our regular commits.
They combined familiar bits of our vocabulary with our typical Franglais in ways that felt oddly familiar.
Some samples began as credible commit subjects before drifting into hallucinations.
Karpathy had already [used the word][rnn-effectiveness] in 2015 when one of his RNNs invented a nonexistent URL.
A later study [identified this][hallucination-audit] as its first use for a language model in the modern deep learning era.

The code and my commits are available in [my char-rnn-tensorflow fork][fork].

note: [^1] [^2]

[^1]: Written retrospectively in 2026. The date is that of my commits to the fork on April 20, 2017; the experiment and its work context are recalled from memory.
[^2]: OpenAI later wrote that its first [generative pre-training work][gpt1], published in 2018 and now known as GPT-1, followed the sentiment-neuron experiment. Back in April 2017, I was just teaching TensorFlow to hallucinate commit messages for an embedded software team.

[sentiment-neuron]: https://openai.com/index/unsupervised-sentiment-neuron/
[rnn-effectiveness]: https://karpathy.github.io/2015/05/21/rnn-effectiveness/
[char-rnn]: https://github.com/karpathy/char-rnn
[upstream]: https://github.com/sherjilozair/char-rnn-tensorflow
[fork]: https://github.com/SRombauts/char-rnn-tensorflow
[gpt1]: https://openai.com/index/language-unsupervised/
[hallucination-audit]: https://arxiv.org/html/2404.07461v2
