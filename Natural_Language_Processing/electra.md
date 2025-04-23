# Blog Review: ELECTRA - Pre-training Text Encoders as Discriminators Rather Than Generators
Author: Manju Yadav 

Based on the paper by: Kevin Clark et al., Google AI & Stanford University (ICLR 2020)


## What is ELECTRA?

In the world of NLP, large-scale pretraining has revolutionized how we approach language understanding. While models like BERT rely on the Masked Language Modeling (MLM) objective, they come with a cost: inefficiency. Only about 15% of input tokens are used for learning during pretraining.

ELECTRA offers a smarter, more efficient solution. Instead of asking the model to guess masked tokens (as BERT does), ELECTRA trains a model to detect whether a token has been replaced by a generator or not. This leads to training on all tokens, making it dramatically more sample- and compute-efficient.

"So instead of being a token guesser like BERT, ELECTRA is a token detector."

### The Core Architecture

ELECTRA introduces two components:

Generator (G): A small MLM that predicts token replacements.

Discriminator (D): Trained to classify each token as original or replaced.

The key trick? After pretraining, only the discriminator is kept for fine-tuning.

Visual:

In the paper (Figure 2), the generator samples replacements for masked tokens, and the discriminator gets this corrupted sequence and learns to classify each token's authenticity.

<img width="552" alt="image" src="https://github.com/user-attachments/assets/eedb4fad-03e8-47f6-b8d9-4747cadf8656" />


### Why ELECTRA Works Better

Problems with MLM (like BERT):

Learns from only a small subset of tokens (~15%)

Uses [MASK] tokens during pretraining which never appear during fine-tuning

ELECTRA solves this by:

Learning from every token

Avoiding the [MASK] token mismatch

Providing a richer, more consistent training signal

### Results That Speak Volumes

On the GLUE Benchmark:

ELECTRA-Small outperforms GPT despite being trained with 30x less compute.

ELECTRA-Base beats BERT-Base and even BERT-Large.

ELECTRA-Large performs on par with RoBERTa and XLNet using only 25% of the compute.

SQuAD 2.0 Performance:

ELECTRA-Large achieves 88.7 EM, better than ALBERT, RoBERTa, and XLNet.

Efficiency and accuracy, hand-in-hand.

##3 Engineering Insights

Generator Size:

Best performance with the generator being 1/4 to 1/2 the size of the discriminator.

Weight Sharing:

Sharing token and positional embeddings (but not full encoder weights) gives a slight boost.

Training Alternatives (That Didn't Work):

Two-stage training (first generator, then discriminator)

Adversarial GAN-style generator (too unstable for text)

### Efficiency Analysis

Ablation studies from the paper show:

ELECTRA 15% (only training on replaced tokens) performs worse.

All-token MLM is better than BERT but worse than ELECTRA.

The best performance comes from Replaced Token Detection on all tokens.

## Final Thoughts

ELECTRA is a stellar example of how rethinking a problem slightly can lead to massive improvements. By reframing language modeling as a classification task instead of a generation task, ELECTRA:

Improves sample and compute efficiency

Delivers state-of-the-art results with fewer resources

Scales well across small to large model sizes

If you’re working with limited resources but want cutting-edge NLP, ELECTRA should be your go-to model.

## Further Reading

Original Paper: https://arxiv.org/pdf/2003.10555 
