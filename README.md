# Thai Sentence Segmentation with mT5

## Introduction
-  Many writing systems indicate the end of a sentence with a punctuation mark. English, as well as many other European languages, ends its sentences with either a punctuation mark (.), a question mark (?), or an exclamation mark (!). In contrast, a number of languages lack a clear system to mark sentence boundaries, making sentence segmentation in NLP a challenging task. One of such languages is Thai.

- Punctuation in Thai hardly serves any functions in indicating the end of a sentence in a text: punctuation marks are used with abrreviated nouns, while question and exclamation marks are rarely used in formal domains[^1]. However, Thai orthography does make use of spaces to signal the end of a clause or a sentence, but it is largely subjective and varies from context to context, which is not a reliable method.

- Several methods have been proposed to tackle this issue. An alternative linguistic analysis is offered by Wirote Aroonmanakun (2007) who argues that clauses should serve as basic syntactic units instead of sentences.[^2] Different model architectures, such as CRF[^3] and BiLSTM-CNN[^4], are utilized in combination with n-gram and POS features for Thai sentence segmentation. Recently, researchers have been able to achieve the state-of-the-art result on the Orchid and UGWC datasets using advanced language model such as ELMo[^5] and WangchanBERTa[^6].

- So far, little attention has been paid to the implementation of sequence-to-sequence model. This project therefore aims to experiment on the segmentation task using Google's mT5, a multilingual varaint of the T5 model, with the newly released LST20 Corpus, in which 74,180 sentences are annotated.

- Our mT5-small model achieves a sentence-level F1 score of 31.9% on inputs with an English short prompt. Results also suggest that the language and phrasing used in prompts have an effect on the performance of the model.

## Our Methodology 

- As with T5, mT5 is an encoder-decoder model which takes text sequences as  input and convert them to target text sequences, which means that it can perform any sequence-to-sequence tasks such as summarization, question answering, translation, text generation, and even sentence segmentation. The model is pretrained on the mC4 dataset, covering a miltitude of languages including Thai. mT5 requires that a 'prompt' or prefix is added to the start of an input sequence to specify a task that the model needs to perform.
- Here, we attempt to implemented 2 variants of mT5: mT5-Small (with 300 million parameters) and mT5-Base (with 580 million parameters). We also opt for simpleT5⚡️ [^7] as a quick and simple method to fine-tune the models.
- simpleT5⚡️ only accepts a pandas dataframe with 2 columns labeled 'source_text' and 'target_text' for both the training set and the evaluation set. No further steps are needed for data preparation.

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
| mT5-Small | 20.5              | 20.7             | **31.9**              | 17.9             |
| mT5-Base  | *to be added* | *to be added* | *to be added* | *to be added* |


## Conclusion
- What task? What did we do? 
- Summary of results.


[^1]: Suthisa Rojana-Anun, "Punctuation in Thai: prescribed usages and current practice," *Journal of the Association of Frence Teacher in Thailand* 137, no. 42 (2019): 11-12, https://doi.org/10.14456/bulletin-atpf.2019.1.

[^2]: Wirote Aroonmanakun, "Thoughts on Word and Sentence Segmentation in Thai," *Proceedings of the Seventh Symposium on Natural language Processing, Pattaya, Thailand, December 13–15*, (2007): 85-90.

[^3]: Rungsiman Nararatwong, Natthawut Kertkeidkachorn, Nagul Cooharojananone, and Hitoshi Okada, "Improving Thai Word and Sentence Segmentation Using Linguistic Knowledge," *IEICE TRANSACTIONS on Information and Systems* 101, no. 12 (2018): 3218-3225, https://doi.org/10.1587/transinf.2018EDP7016.

[^4]: Sorratat Sirirattanajakarin, Duangjai Jitkongchuen, and Peerasak Intarapaiboon, "BoydCut: Bidirectional LSTM-CNN Model for Thai Sentence Segmenter," *2020 1st International Conference on Big Data Analytics and Practices (IBDAP)*, (2020): 1-4, https://doi.org/10.1109/IBDAP50342.2020.9245454.

[^5]: Chanatip Saetia, Ekapol Chuangsuwanich, Tawunrat Chalothorn, and Peerapon Vateekul, "Semi-supervised Thai Sentence Segmentation Using Local and Distant Word Representations," *Engineering Journal* 25, no. 6 (2021), https://doi.org/10.4186/ej.2021.25.6.15.

[^6]: Sumeth Yuenyong and Virach Sornlertlamvanich, "TranSentCut - Transformer Based Thai Sentence Segmentation," *Songklanakarin Journal of Science and Technology (SJST)* 44, no. 3 (2022): 852-860, https://doi.org/10.14456/sjst-psu.2022.114.

[^7]: https://github.com/Shivanandroy/simpleT5
