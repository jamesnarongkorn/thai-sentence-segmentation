# Thai Sentence Segmentation with mT5

## Introduction
- ### Motivation 
    Many writing systems utilize punctuation marks to indicate the end of a sentence. English, as well as many other European languages, ends its sentences with either a punctuation mark (.), a question mark (?), and an exclamation mark (!). In contrast, a number of languages lack a clear system to mark a sentence boundary, making sentence segmentation in NLP a challenging task. One of such languages is Thai. 

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