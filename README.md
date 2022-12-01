# Thai Sentence Segmentation with mT5

## Introduction
- Many writing systems indicate the end of a sentence with a punctuation mark. English, as well as many other European languages, ends its sentences with either a punctuation mark (.), a question mark (?), or an exclamation mark (!). In contrast, a number of languages lack a clear system to mark sentence boundaries, making sentence segmentation in NLP a challenging task. One of such languages is Thai.

- Punctuation in Thai hardly serves any functions in indicating the end of a sentence in a text: punctuation marks are used with abrreviated nouns, while question and exclamation marks are rarely used in formal domains[^1]. However, Thai orthography does make use of spaces to signal the end of a clause or a sentence, but it is largely subjective and varies from context to context, which is not a reliable method.

- Several methods have been proposed to tackle this issue. An alternative linguistic analysis is offered by Wirote Aroonmanakun (2007), who argues that clauses should serve as basic syntactic units instead of sentences.[^2] Different model architectures, such as CRF[^3] and BiLSTM-CNN[^4], are utilized in combination with n-gram and POS features for Thai sentence segmentation. Recently, researchers have been able to achieve remarkable results using WangchanBERTa[^5] and attain the state-of-the-art result on the Orchid and UGWC datasets with ELMo[^6].

- So far, little attention has been paid to the implementation of sequence-to-sequence models. This project therefore aims to experiment on the segmentation task using Google's mT5, a multilingual varaint of the T5 model, with the newly released LST20 Corpus.

- Our mT5-small model achieves a sentence-level F1 score of 31.9% on inputs with a short English prompt. Results also suggest that the language and phrasing used in prompts have an effect on the performance of the model.

## Our Methodology 

- As with T5, mT5 is an encoder-decoder model which takes text sequences as input and converts them to target text sequences, which means that it can perform any sequence-to-sequence tasks such as summarization, question answering, translation, text generation, and even sentence segmentation. The model is pretrained on the mC4 dataset, covering a miltitude of languages including Thai. 
- mT5 requires that a 'prompt' or a prefix is added to the start of an input sequence to specify a task that the model needs to perform.
- Here, we attempt to implemented 2 variants of mT5: mT5-Small (with 300 million parameters) and mT5-Base (with 580 million parameters). We also opt for simpleT5⚡️ [^7] as a quick and simple method to fine-tune the models.
- We provide the training set and the evaluation set to simpleT5⚡️ with a pandas dataframe with 2 columns labeled 'source_text' for the input and 'target_text' for the output. The input is sequences of text prefixed by a prompt and the output is sequences of text marked with vertical bars (|) as sentence delimiters.

## Dataset
- The models are trained on the LST20 Corpus, which offers 74,180 Thai sentences annotated with a boundary marker[^8]. This large-scale NECTEC-developed dataset also comes with four other layers of linguistic annotation: word segmentation, POS tagging, named entities, and clause boundaries. It spans over 3,000,000 words from 3,745 documents in 15 news domain.

|           | train  | eval  | test  | all    |
|-----------|--------|-------|-------|--------|
| sentences | 63,310 | 5,620 | 5,250 | 74,180 |

## Experiment setup
- To reiterate, training texts from the LST20 Corpus is feed to the mT5 model. Task prefix is included at the beginning of each row of data with 4 variations to test whether differences in prompt length and language affect model performance. The propmts are listed below:
    - "ตัดประโยค: "
    - "ตัดประโยคด้วยเครื่องหมาย |: "
    - "segment sentence: "
    - "segment each sentence with |: "
- Each prompt takes approximately 25 minutes to train on the mT5-Small with GPU on a Google Colab free account. 
- Regarding hyperparameter tuning, simpleT5⚡️ handles most of the tasks and lets us specify these training arguments:
    - source_max_token_len: the max token length of source text is set to 150.
    - target_max_token_len: the max token length of target text is set to 150.
    - batch_size: batch size is set to 8.
    - max_epochs: the number of epochs is set to 3.

## Results 
- As can be seen from the data in the table below, no significant differences are found among Thai prompts, as noted that mT5 does not benefit from a task prefix during single-task fine-tuning[^9].
- However, the most striking result to emerge from the data is that different propmts do affect model performance. The short English propmt produces the best result with 31.9% of sentence-level F1 score, while the long English prompt however yields the lowest score. This may result from the fact that longer prompts take up more space during tokenization, cauing the input to be truncated.
- *mT5-Base ...... to be added*

### Model comparison
| Model     | Short Th Prompt | Long Th Prompt | Short En Prompt | Long En Prompt |
|-----------|-------------------|------------------|-------------------|------------------|
| mT5-Small | 20.5              | 20.7             | **31.9**              | 17.9             |
| mT5-Base  | *to be added* | *to be added* | *to be added* | *to be added* |


## Conclusion
- In dealing with Thai sentence segmentation, we attempt to experiment on the sequence-to-sequence mT5 model. Prefixed sequences of text from the LST20 Corpus are provided for the model to perform sentence segmentation.
- Results suggest that the short English prompt "segment sentence: " yields the best model performance, while Thai prefixes do not profit the model regardless of their lengths.
- *mT5-Base ...... to be added*


[^1]: Suthisa Rojana-Anun, "Punctuation in Thai: prescribed usages and current practice," *Journal of the Association of Frence Teacher in Thailand* 137, no. 42 (2019): 11-12, https://doi.org/10.14456/bulletin-atpf.2019.1.

[^2]: Wirote Aroonmanakun, "Thoughts on Word and Sentence Segmentation in Thai," *Proceedings of the Seventh Symposium on Natural language Processing, Pattaya, Thailand, December 13–15*, (2007): 85-90.

[^3]: Rungsiman Nararatwong, Natthawut Kertkeidkachorn, Nagul Cooharojananone, and Hitoshi Okada, "Improving Thai Word and Sentence Segmentation Using Linguistic Knowledge," *IEICE TRANSACTIONS on Information and Systems* 101, no. 12 (2018): 3218-3225, https://doi.org/10.1587/transinf.2018EDP7016.

[^4]: Sorratat Sirirattanajakarin, Duangjai Jitkongchuen, and Peerasak Intarapaiboon, "BoydCut: Bidirectional LSTM-CNN Model for Thai Sentence Segmenter," *2020 1st International Conference on Big Data Analytics and Practices (IBDAP)*, (2020): 1-4, https://doi.org/10.1109/IBDAP50342.2020.9245454.

[^5]: Sumeth Yuenyong and Virach Sornlertlamvanich, "TranSentCut - Transformer Based Thai Sentence Segmentation," *Songklanakarin Journal of Science and Technology (SJST)* 44, no. 3 (2022): 852-860, https://doi.org/10.14456/sjst-psu.2022.114.

[^6]: Chanatip Saetia, Ekapol Chuangsuwanich, Tawunrat Chalothorn, and Peerapon Vateekul, "Semi-supervised Thai Sentence Segmentation Using Local and Distant Word Representations," *Engineering Journal* 25, no. 6 (2021), https://doi.org/10.4186/ej.2021.25.6.15.

[^7]: https://github.com/Shivanandroy/simpleT5

[^8]: Prachya Boonkwan et al., "The Annotation Guideline of LST20 Corpus," (2020), https://doi.org/10.48550/arXiv.2008.05055.

[^9]: https://huggingface.co/docs/transformers/model_doc/mt5