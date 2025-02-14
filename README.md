
# EFCSC
Entity-focused Chinese Spelling Error Correction: Dataset and Approach


# Overview
We propose an construct an entity-focused Chinese spelling correction dataset (EFCSC), the first public spelling correction corpus to emphasize entity errors. to incorporate adapted dependency syntax knowledge into GEC models. Furthermore, we propose an entity knowledge injected language model (EFCSC) designed for entity-focused spelling correction, which injects entity information into pre-trained language models, thus ensuring traditional spelling correction models pay more attention to entity words.




# How to Install

You can use the following commands to install the environment for EFCSC:

Seq2Seq
```
conda create -n Seq2Seq python==3.8
conda activate Seq2Seq
pip install -r requirements_seq2seq.txt
```

Seq2Edit
```
conda create -n seq2edit python==3.8
conda activate seq2edit
pip install -r requirements_seq2edit.txt
```


# How to Download Pre-trained Models

Seq2Seq Model:

| Name       | Download Link | Description |
|------------|---------------|-------------|
| **Bart-Base-Chinese** | [Link](https://huggingface.co/fnlp/bart-base-chinese) | Seq2Seq-based Pre-Trained Model|


SeqEdit Model:

| Name       | Download Link | Description |
|------------|---------------|-------------|
| **StructBert-Large-Chinese** | [Link](https://huggingface.co/junnyu/structbert-large-zh) | Seq2Edit-based Pre-Trained Model |


# How to Train
If you want to train new models using your own dataset, please follow the instructions in `./models/Seq2Seq-based-CGEC` or `./models/seq2edit-based-CGEC`:

+ `pipeline.sh`: train the GEC models and correct the error sentences.

You can use the following commands to train and predict:

```
sh pipeline.sh
```

# How to Ensemble

If you want to ensemble the multiple results to obtain the best results, please follow the instructions in `./scorers/ChERRANT/emsemble.sh`:

+ `ensemble.sh`: ensemble multiple model outputs results to one.

You can use the following commands to the ensemble:

```
sh ensemble.sh
```

# About EFCSC Dataset

We have now exposed the validation dataset and the test dataset, which can be downloaded in "".



| Name | Sent | Errors | usage|
| :------- | :---------: | :---------: |:---------: |
| EFCSC | 1200000 | 1857304 | Pre-Training|
| EFCSC-dev | 4000 | 4035 | Validation|
| EFCSC-test | 2500 | 2019 | Testing |



