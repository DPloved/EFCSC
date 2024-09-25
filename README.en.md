
## README

+ **CGEC benchmark models`./models`**:
  + **Seq2Edit model`./models/seq2edit-based-CGEC`**: This kind of models treats GEC as a sequence labeling task and performs error corrections via a sequence of token-level edits, including insertion, deletion, and substitution.
    +  With minor modifications to accommodate Chinese, we adopt [GECToR](https://github.com/grammarly/gector), which achieves the SOTA performance on English GEC datasets.
  + **Seq2Seq model`./models/seq2seq-based-CGEC`**：This kind of models straightforwardly treats GEC as a monolingual translation task
    + We fine-tune the recently-proposed Seq2Seq pretrained model [Chinese-BART](https://github.com/fastnlp/CPT) and use it in CGEC.
  + **Ensemble model`./scorers/ChERRANT/emsemble.sh`**：We adopt a simple edit-wise vote mechanism, which can support the ensemble of heterogeneous models (such as Seq2Seq and Seq2Edit) and lead to significant performance boosts.


### Experimental enviroment

We use Python 3.8 to experiment, and the necessary dependencies can be installed through the following code. Considering that there are some conflicts between the environments of Seq2Seq and Seq2Edit models, two environments need to be installed separately:
```
# Seq2Edit environment
pip install -r requirements_seq2edit.txt

# Seq2Seq environment
pip install -r requirements_seq2seq.txt
```

### Training data

The training data used in our experiment is composed of: 1) Chinese `Lang8` corpus; 2)`HSK` corpus. We upsampling `HSK` corpus 5 times. We only use the erroneous part of the training data.

Download Link: [Google Drive](https://drive.google.com/file/d/1l0A50z7fMXjQT3y2ct7TQsEHqOwlvg0_/view?usp=sharing)

<!-- **Note: the copyright issue about HSK data is under discussion, so the training data download link is not available at present.** -->

### Usage
We provide pipeline scripts to use our model, including the process of preprocessing->training->inference. Please refer to
`./models/seq2edit-based-CGEC/pipeline.sh` and `./models/seq2seq-based-CGEC/pipeline.sh`

Besides, we also provide converged checkpoints for testing (the following metrics are precision/recall/F0.5):

The ensemble strategy used in our paper can be found in `./scorers/ChERRANT/ensemble.sh`. Please kindly note that above seq2edit checkpoints are based on `Chinese-StructBERT-large` and seq2seq checkpoints are based on `Chinese-BART-Large`.


### Evaluation

To get the evaluation results on the [Official NLPCC18 dataset](http://tcci.ccf.org.cn/conference/2018/taskdata.php), you can make predictions by using our benchmark models, and evaluate the results through [M2Scorer](https://github.com/nusnlp/m2scorer). It is important to note that the predicted results must be segmented using the PKUSEG tool.

To get the evaluation results on MuCGEC, you can evaluate the results through our proposed [ChERRANT](./scorers/ChERRANT). Please refer to `./scorers/ChERRANT/demo.sh` for the use of ChERRANT.



