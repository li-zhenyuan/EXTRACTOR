

# EXTRACTOR

EXTRACTOR helps to extract the system level attack behavior from unstructured threat reports. The extracted attack behavior will be represented in form of directed graphs, where the nodes represent system entities and edges represent system calls. EXTRACTOR leverages Natural Language Processing (NLP) techniques to transform a raw threat report into a graph representation.
<img width="1710" alt="architecture" src="https://user-images.githubusercontent.com/43620635/111570179-39c27980-8772-11eb-9c10-dcb497d6a4e3.png">

## Instructions
### Requirements

This repository uses `python 3.5+` and has the following requirements:
```
nltk == 3.4.5
spaCy == 2.1.0
allennlp == 0.8.4
neuralcoref == 4.0.0
graphviz == 0.13.2
textblob == 0.15.3
pattern == 3.6
numpy == 1.18.1
```
You can directly install the requirements using `pip install -r requirements.txt`


### Usage 

Run EXTRACTOR with `python3 main.py [-h] [--asterisk ASTERISK] [--crf CRF] [--rmdup RMDUP] [--elip ELIP] [--gname GNAME] [--input_file INPUT_FILE]`.

Depending on the usage, each argument helps to provide a different representation of the attack behavior. 
`[--asterisk true]` creates abstraction and can be used to replace anything that is not perceived as IOC/system entity into a wild-card. This representation can be used to be searched within the audit-logs.  

`[--crf true/false]` allows activating or deactivating of the co-referencing module. 

`[--rmdup true/false]` enables removal of duplicate nodes-edge. 

`[--elip true/false]` is to choose whether to replace ellipsis subjects using the surrounding subject or not.

`[--input_file path/filename.txt]` is to pass the text file to the application. 

`[--gname graph_name]` is to specify the name output graph (two files will be created, e.g., graph.pdf and graph.dot).

#### Example
`python3 main.py --asterisk true --crf true --rmdup true --elip true --input_file input.txt --gname mygraph`

Here is a sample of attack description and the corresponding attack behavior graph.
<img width="1708" alt="text and graph" src="https://user-images.githubusercontent.com/43620635/111570328-9c1b7a00-8772-11eb-9f17-383aa685a494.png">

## Summarizer
To perform the prediction/text summarization, you need to first convert the `txt` file to the required format `tsv` using `python3 txt2tsv.py`.


### Prediction
To do the extractive summarization, run `python3 prediction.py`


