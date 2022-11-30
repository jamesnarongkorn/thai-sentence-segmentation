# Thai Sentence Segmentation with mT5

## Introduction
-  Many writing systems indicate the end of a sentence with a punctuation mark. English, as well as many other European languages, ends its sentences with either a punctuation mark (.), a question mark (?), or an exclamation mark (!). In contrast, a number of languages lack a clear system to mark sentence boundaries, making sentence segmentation in NLP a challenging task. One of such languages is Thai.

- Punctuation in Thai hardly serves any functions in indicating the end of a sentence in a text: punctuation marks are used with abrreviated nouns, while question and exclamation marks are rarely used in formal domains[^1]. However, Thai orthography does make use of spaces to signal the end of a clause or a sentence, but it is largely subjective and varies from context to context, which is not a reliable method.

- Several methods have been proposed to tackle this issue. An alternative linguistic analysis is offered by Wirote Aroonmanakun (2007) who argues that clauses should serve as basic syntactic units instead of sentences.[^2] 
    
    The are some workarounds, like 



- What other people have done? What model have previous work have used? What did they miss?  (1-2 paragraphs)
- Summarize your idea
    In this project, I attempt to experiment on the issue using Google's mT5, a multilingual varaint of the T5 model.
- Summarize your results

## Our Approach/Methodology/Model 
Explain your model here how it works. 

- Input is ... 
- Output is ...
- Model description 

## Dataset 
- Annotation guidelines 
- Results total how many tokens, sentences, etc. 
- Label distribution

| Label | Frequency |
|--------|----------|
| good | 60% |
| bad | 40 % | 

## Experiment setup
- Which pre-trained model? How did you pretrain embeddings? 
- Computer. How long? 
- Hyperparameter tuning? Dropout? How many epochs? 

## Results 
How did it go?  + Interpret results. 

### Model comparison
| Model     | Th Short Prompt 1 | Th Long Prompt 2 | En Short Prompt 1 | En Long Prompt 2 |
|-----------|-------------------|------------------|-------------------|------------------|
| mT5-Small | 0.20              | 0.20             | **0.31**              | 0.17             |
| mT5-Base  | **                | **               | **                | **               |


## Conclusion
- What task? What did we do? 
- Summary of results.


[^1]: Suthisa Rojana-Anun, "Punctuation in Thai: prescribed usages and current practice," *Journal of the Association of Frence Teacher in Thailand* 137, no. 42 (2019): 11-12. https://doi.org/10.14456/bulletin-atpf.2019.1


[^2]: Wirote Aroonmanakun (2007)

[^3]: Alberto Poncelas et al., “Multiple Segmentations of Thai Sentences for Neural Machine Translation.” *Proceedings of the 1st Joint SLTU and CCURL Workshop (SLTU-CCURL)*, (2020). https://doi.org/10.48550/ARXIV.2004.11472.


we explore how to augment a set of English–Thai parallel data by replicating sentence-pairs with different word segmentation methods on Thai, as training data for NMT model training. Using different merge operations of Byte Pair Encoding, different segmentations of Thai sentences can be obtained. The experiments show that combining these datasets, performance is improved for NMT models trained with a dataset that has been split using a supervised splitting tool.


a discourse should be seen as a combination of clauses rather than sentences. Some discourse clues then can be used to segment these discourse units. The result from sentence segmentation module could be a sequence of segments composed of clauses, which then can be constructed into the discourse structure