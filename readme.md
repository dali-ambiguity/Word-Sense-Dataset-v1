# Contextualised Polyseme Word Sense Dataset v1

This is the first version of a **Contextualised Polyseme Word Sense Dataset** collected by [Janosch Haber](http://janoschhaber.com) and [Massimo Poesio](https://sites.google.com/view/massimo-poesio/home) for the [DALI Project](http://dali.eecs.qmul.ac.uk/) at [Queen Mary University of London](https://www.qmul.ac.uk/). The dataset contains three different measures of word sense similarity for polysemic target words used in contexts invoking different sense interpretations. The first set contains 20 graded similarity judgements for polysemic target words used in sentence pairs invoking different sense interpretations. The second set contains co-predication acceptability judgements for sentence constructions combining the sentence pairs from the first set. As we observed a higher variance in ratings here, this dataset has between 20 and 45 judgements for every item. The third set lastly contains 10 categorical word class judgements for the polysemic target words, with participants selecting multiple applicable class labels from a pre-defined set. 

This version covers the following 10 systematic polysemes:

- newspaper (3 senses)
- War and Peace (2 senses)
- DVD (4 senses)
- school (4 senses)
- wine (2 senses)
- glass (2 senses)
- Hemingway (2 senses)
- lunch (2 senses)
- chicken (2 senses)
- construction (2 senses)
- door (2 senses)

together with a set of 15 homonyms and 15 synonyms in datasets 1 and 2. The collection of the dataset as well as an initial set of experiments analysing contextualised embeddings for target words are described in our paper [Word Sense Distance in Human Similarity Judgements and Contextualised Word Embeddings](https://www.aclweb.org/anthology/2020.pam-1.17.pdf), and a comparison between the different measures is reported in our paper __Assessing Polyseme Sense Similarity through Co-predication Acceptabilityand Contextualised Embedding Distance__.


## Word Sense Similarity Dataset

The dataset is stored in a single `polyseme_similarity.json` file with the following structure

```
{
  "0": {
    "worker": "worker_56",
    "duration": 103,
    "judgements": {
      "10_11": {
        "rating": "77",
        "target_word": "glass",
        "sample": "glass: container/container",
        "sentence_1": "The glass broke when she dropped it.",
        "sentence_2": "The glass fits about 200 ml of liquid.",
        "highlights_1": [
          1
        ],
        "highlights_2": [
          1
        ]
      },
      "1_21": {
        "rating": "87",
        "target_word": "newspaper",
        "sample": "newspaper: physical/organisation",
        "sentence_1": "The newspaper lies on the kitchen table.",
        "sentence_2": "The newspaper was sued for defamation.",
        "highlights_1": [
          1
        ],
        "highlights_2": [
          1
        ]
      },
      ...
    },
    ...
   },
   ...
}
```
The outer key numbers individual survey submissions, ranging from 0 to 299. Each survey contains an AMT worker's similarity judgements on 10 sentence pairs. 

Every submission has three entries: 
- `worker`, an anonymised representation of the worker's ID  
- `duration`, the duration of the submission in seconds
- `judgements`, a dictionary of the submitted judgements. Each survey contains judgements for target word similarity in 10 sentence pairs indicated by a unique Sample ID. 

Sample IDs uniquely identify target words and sample sentences shown to the participant. The full list of samples can be found in our paper. 

Every judgement has seven entries:
- `rating`, the assigned graded similarity rating on a scale from 1 to 100
- `target word`, the highlighted target expression rated by the participant
- `sample`, a description of the sample (target word and interpretations invoked by the sample sentences)
- `sentence_1`, the first sample sentence displayed to the participant
- `sentence_2`, the second sample sentence displayed to the participant
- `highlights_1`, the indexes of words highlighted in the first sample sentence
- `highlights_2`, the indexes of words highlighted in the second sample sentence

Target expression highlights can be used to extract word embeddings from contextualised language model encodings of the sample sentences. 

## Co-predication Acceptability Dataset

The dataset is stored in a single `polyseme_copredication.json` file with the following structure

```
{
  "0": {
    "worker": "worker_54",
    "duration": 74,
    "judgements": {
      "11_11": {
        "rating": "12",
        "copredication": "The construction began in early September and took far longer than expected.",
        "target_word": "construction",
        "sample": "construction: process/process",
        "sentence_1": "The construction took far longer than expected.",
        "sentence_2": "The construction will begin in early September.",
        "highlights_1": [
          1
        ],
        "highlights_2": [
          1
        ]
      },
      "1_32": {
        "rating": "99",
        "copredication": "The newspaper wasn't very interesting and got wet from the rain.",
        "target_word": "newspaper",
        "sample": "newspaper: information/physical",
        "sentence_1": "The newspaper wasn't very interesting.",
        "sentence_2": "The newspaper got wet from the rain.",
        "highlights_1": [
          1
        ],
        "highlights_2": [
          1
        ]
      },
      ...
    },
    ...
  },
  ...
}
```
The outer key numbers individual survey submissions, ranging from 0 to 466. Each survey contains an AMT worker's acceptability judgements on 10 co-predication structures. 

Every submission has three entries: 
- `worker`, an anonymised representation of the worker's ID  
- `duration`, the duration of the submission in seconds
- `judgements`, a dictionary of the submitted judgements. Each survey contains acceptability judgements for 10 co-predication structures indicated by a unique Sample ID. 

Sample IDs uniquely identify target words and co-predication structures shown to the participant. The full list of samples can be found in our paper [Word Sense Distance in Human Similarity Judgements and Contextualised Word Embeddings](https://www.aclweb.org/anthology/2020.pam-1.17.pdf), the sample building process is described in __Assessing Polyseme Sense Similarity through Co-predication Acceptabilityand Contextualised Embedding Distance__.

Every judgement has eight entries:
- `rating`, the assigned acceptability rating on a scale from 1 to 100
- `copredication`, the co-predication structure rated by the participant
- `target word`, the target expression in the structure (not highlighted in the survey)
- `sample`, a description of the sample (target word and interpretations invoked by the sample sentences)
- `sentence_1`, the first sample sentence used in the co-predication structure
- `sentence_2`, the second sample sentence used in the co-predication structure
- `highlights_1`, the indexes of target words in the first sample sentence (not highlighted in the survey)
- `highlights_2`, the indexes of target words in the second sample sentence (not highlighted in the survey)

## Sense Class Dataset

The dataset is stored in a single `polyseme_classification.json` file with the following structure

```
{
  "0": {
    "worker": "worker_6",
    "duration": 171,
    "judgements": {
      "10_22_1_0": {
        "class_id": 0,
        "class": "animal",
        "assigned": false,
        "target_word": "glass",
        "sentence": "The glass had a thick layer of foam.",
        "highlights": [
          1
        ]
      },
      "10_22_1_1": {
        "class_id": 1,
        "class": "building",
        "assigned": false,
        "target_word": "glass",
        "sentence": "The glass had a thick layer of foam.",
        "highlights": [
          1
        ]
      },
      ...
    },
    ...
  },
  ...
}
```
The outer key numbers individual survey submissions, ranging from 0 to 97. Each survey contains an AMT worker's sense class assignments for 10 sample sentences. 

Every submission has three entries: 
- `worker`, an anonymised representation of the worker's ID  
- `duration`, the duration of the submission in seconds
- `judgements`, a dictionary of the submitted judgements. Each survey contains the sense class assignments for 10 sample sentences indicated by a unique Sample ID. 

Sample IDs uniquely identify target words and co-predication structures shown to the participant. The full list of samples can be found in our paper [Word Sense Distance in Human Similarity Judgements and Contextualised Word Embeddings](https://www.aclweb.org/anthology/2020.pam-1.17.pdf), the sample building process is described in __Assessing Polyseme Sense Similarity through Co-predication Acceptabilityand Contextualised Embedding Distance__.

Every judgement has six entries:
- `class_id`, the ID of one of the 16 class labels
- `class`, the label of the class indicated by the label
- `assigned`, a boolean indicating whether this sense class label was assigned to the item
- `target word`, the highlighted target expression classified by the participant
- `sentence`, the sample sentence shown to the participant
- `highlights`, the indexes of target words highlighted in the sample sentence

There will be 16 of these entries for each survey, indicating whether or not a given class label was assigned to a given sample sentence. The full list of class labels is as follows:

- 0 animal
- 1 building
- 2 container
- 3 data or information
- 4 event or process
- 5 foodstuff
- 6 group of people
- 7 institution
- 8 liquid
- 9 literary work
- 10 medium
- 11 organisation
- 12 person
- 13 physical object
- 14 representative
- 15 other

## References
If you use this dataset, please cite our paper
```
@inproceedings{haber-poesio-2020-word,
    title = "Word Sense Distance in Human Similarity Judgements and Contextualised Word Embeddings",
    author = "Haber, Janosch and Poesio, Massimo",
    booktitle = "Proceedings of the Probability and Meaning Conference (PaM 2020)",
    month = jun,
    year = "2020",
    address = "Gothenburg",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.pam-1.17",
    pages = "128--145",
    abstract = "Homonymy is often used to showcase one of the advantages of context-sensitive word embedding techniques such as ELMo and BERT. In this paper we want to shift the focus to the related but less exhaustively explored phenomenon of polysemy, where a word expresses various distinct but related senses in different contexts. Specifically, we aim to i) investigate a recent model of polyseme sense clustering proposed by Ortega-Andres {\&} Vicente (2019) through analysing empirical evidence of word sense grouping in human similarity judgements, ii) extend the evaluation of context-sensitive word embedding systems by examining whether they encode differences in word sense similarity and iii) compare the word sense similarities of both methods to assess their correlation and gain some intuition as to how well contextualised word embeddings could be used as surrogate word sense similarity judgements in linguistic experiments.",
}

```

## Contact
For questions, please feel free to contact Janosch Haber at [j.haber@qmul.ac.uk](mailto:j.haber@qmul.ac.uk).