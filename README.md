# SimCLR_tested_on_cifar10

Testing on cifar10 using the SimCLR model
#### Reference Paper: Chen, Ting, et al. "A simple framework for contrastive learning of visual representations." International conference on machine learning. PMLR, 2020.
#### Reference Codes:[PyTorch SimCLR: A Simple Framework for Contrastive Learning of Visual Representations](https://github.com/sthalles/SimCLR)


Table of contents
=================
   * [Introduction](#introduction)
   * [Installation](#installation)
        * [Step 1: Clone the Code from Github](# Step 1: Clone the Code from Github)
        * [Step 2: Install Requirements](# Step 2: Install Requirements)
   * [Run  Script  to Train](#Run Script to Train)
   * [Tuning a hyper-parameter](#Tuning a hyper-parameter)

## introduction
[SimCLR](https://sthalles.github.io/simple-self-supervised-learning/#1) uses the same principles of contrastive learning described above. In the proposed paper, the method achieves SOTA in self-supervised and semi-supervised learning benchmarks. It introduces a simple framework to learn representations from unlabeled images based on heavy data augmentation. ***To put it simply, SimCLR uses contrastive learning to maximize agreement between 2 augmented versions of the same image.\***

<div align="center">
  <img src="https://camo.githubusercontent.com/47395e06a77f8d3a10579a0d0d48aa4d1a3227e044f32b4eb92bb829b39cbec1/68747470733a2f2f737468616c6c65732e6769746875622e696f2f6173736574732f636f6e74726173746976652d73656c662d737570657276697365642f636f7665722e706e67"  />
</div>

## installation

### Step 1: Clone the Code from Github

```
git clone https://github.com/zjuygm/SimCLR_tested_on_cifar10.git
cd SimCLR_tested_on_cifar10\SimCLR-test
```

### Step 2: Install Requirements

**Python**: see [`requirements.txt`](https://github.com/StanfordVL/taskonomy/blob/master/taskbank/requirement.txt) for complete list of used packages. We recommend doing a clean installation of requirements using virtualenv:

```bash
conda env create --name simclr --file env.yml
conda activate simclr
```

If you don't want to do the above clean installation via virtualenv, you could also directly install the requirements through:
```bash
pip install -r requirements.txt --no-index
```


## Run Script to Train
Before running SimCLR, make sure you choose the correct running configurations. You can change the running configurations by passing keyword arguments to the `run.py` file.
```bash
python run.py -data ./datasets -dataset-name cifar10 --log-every-n-steps 100 --epochs 100 
```

## Tuning a hyper-parameter

Feature evaluation is done using a linear model protocol.Tuning a hyper-parameter and analyzing its effects on performance.Note that SimCLR benefits from **longer training**.**Top 1 is  on cifar10  test set.**

| Linear Classification      | Dataset | Feature Extractor | Architecture                                                 | Feature dimensionality | Projection Head dimensionality | Epochs | Top1 % |
| -------------------------- | ------- | ----------------- | ------------------------------------------------------------ | ---------------------- | ------------------------------ | ------ | ------ |
| Logistic Regression (Adam) | CIFAR10 | SimCLR            | [ResNet-50](https://drive.google.com/open?id=1lc2aoVtrAetGn0PnTkOyFzPCIucOJq7C) | 512                    | 128                            | 100    | 65.625 |
| Logistic Regression (Adam) | CIFAR10 | SimCLR            | [ResNet-50](https://drive.google.com/open?id=1lc2aoVtrAetGn0PnTkOyFzPCIucOJq7C) | 512                    | 128                            | 150    | 71.093 |
| Logistic Regression (Adam) | CIFAR10 | SimCLR            | [ResNet-50](https://drive.google.com/open?id=1lc2aoVtrAetGn0PnTkOyFzPCIucOJq7C) | 512                    | 128                            | 200    | 73.242 |


