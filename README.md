# Thai Sentence Segmentation with mT5

## Introduction
- ### Motivation 
    Many writing systems indicate the end of a sentence with a punctuation mark. English, as well as many other European languages, ends its sentences with either a punctuation mark (.), a question mark (?), and an exclamation mark (!). In contrast, a number of languages lack a clear system to mark sentence boundaries, making sentence segmentation in NLP a challenging task. One of such languages is Thai.


    Apart from the rare use of question and exclamation marks, punctuation in Thai serves no purpose in indicating the end or the beginning of a sentence. For instance, the punctuation mark Thai orthography, however, does make use of spaces to separate the end of a clause or a sentence, but they are not always a reliable method 

    [^1]

    the modern Thai script does not make use of any spaces to clarify word boundaries 

- What other people have done? What model have previous work have used? What did they miss?  (1-2 paragraphs)
- Summarize your idea
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


[^1]: Suthisa Rojana-anun, "Punctuation in Thai: prescribedusages and current practice," *Journal of the Association of Frence Teacher in Thailand* 137, no. 42 (2019): 11-12, https://doi.org/10.14456/bulletin-atpf.2019.1