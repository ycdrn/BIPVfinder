# Deep learning for BIPV segmentation on facades <br> Comparison with human annotations across facade designs

[Ayca Duran](https://aycaduran.com/contact), [Pedram Mirabian](https://www.linkedin.com/in/pmirabian/?originalSubdomain=ch), [Panagiotis Karapiperis](https://www.linkedin.com/in/panagiotis-karapiperis-ethz/?originalSubdomain=ch), [Christoph Waibel](https://www.linkedin.com/in/christoph-waibel-19205114b/?originalSubdomain=ch), [Bernd Bickel](https://berndbickel.com/about-me), [Arno Schlueter](https://systems.arch.ethz.ch/arno-schlueter)

[[ Paper ]](https://doi.org/10.1016/j.buildenv.2026.114292) – Published in Building and Environment, April 2026

## Table of Contents
1. [Abstract](#abstract)
2. [Setup Instructions](#setup-instructions)
4. [Citation](#citation)
5. [References](#references)

## Abstract
Building-integrated photovoltaics (BIPV) on facades are a significant but underutilized source of solar energy in urban environments. Automating the recognition of BIPV on facades through vision based systems can help guide design recommendations and extend solar asset maps. Unlike rooftop photovoltaic (PV) systems, facade BIPV recognition is difficult due to limited visibility in overhead imagery, high visual variability, and the absence of structured datasets. This study proposes a method based on deep learning (DL) for automated segmentation of BIPV panels on building facades using street-level and web images. A new dataset comprising 400 annotated BIPV projects was created, including detailed pixel-level masks and project attributes. Two model architectures, Mask Region-based Convolutional Neural Network (Mask R-CNN) and SegFormer, as well as human baselines are evaluated. The SegFormer model outperforms Mask R-CNN in pixel-level metrics. A user study conducted with human annotators without domain-specific expertise provides comparative insight into human performance, revealing common challenges in recognizing facade BIPV. The results demonstrate that DL models, trained specifically for this task, can segment BIPV panels more accurately than mean of human annotators, with SegFormer achieving an IoU of 0.69 compared to 0.42. The user study suggests that BIPV with satin finishes, invisible cells, and a PV-to-facade ratio of more than half challenge human recognition and therefore can be prioritized in visually sensitive areas. The outputs of the segmentation model are also utilized to estimate the BIPV energy yield. The annotated dataset and models are made available to facilitate future research.


![Schematic representation of overall method.](/overview.png)


# Setup Instructions

This repository contains the Python scripts and relevant files used in the fine-tuning and evaluation of the pre-trained models, as well evaluation of  human annotations referenced in the publication.

The codebase is split in 10 steps:
* Steps 1 and 2 handle the data collection, downloading of the images, and stratified sampling in order to create a representative dataset. These notebooks can be downloaded from [BIPV Facades Dataset repository](https://github.com/ycdrn/bipv_facades.git).
* Step 3 deals with the augmentation and creation of the prepared datasets (if using the pre-built datasets you do not need this step).
* Step 4 and 6 (first part) deal with the training of different model architectures, with MaskRCNN and SegFormer respectively.
* Step 5 and 6 (second part) deal with evaluating the trained model on the test dataset (unseen data).
* Step 8 evaluates the human labeling performance using data from an Amazon mTurk survey.
* Step 9 and 10 perform a uniform processing of model and human performance and report the metrics and illustrations used in the paper.

In order to facilitate running the scripts, use **Google Colab**, with the files stored on the **Google Drive** of the account running the code. The primary storage requirement arises from the trained model checkpoint files, which are not included seperately (download instructions [below](#model-loading)).


### Prerequisites & Environment Setup

* All required libraries are either included in Google Colab by default, or installed in the Python notebook in which they are utilized. 

* For the notebooks dealing with model training or evaluation, using a GPU Colab instance is required.

* PV Facades Dataset (required, see [Dataset Setup](#dataset-setup))

* Fine-tuned models (optional, see [Model Loading](#model-loading))

## Code Setup

To set up the repo open a new Google Colab notebook and run the following block to connect to Google Drive:
```
from google.colab import drive
drive.mount('/content/drive')
```
Followed by the block below to create the base path and clone the files:
```
%%bash
cd /content/drive/MyDrive/
mkdir -p BIPVFINDER
cd BIPVFINDER
git clone https://github.com/ycdrn/BIPVfinder.git .
``` 

## Dataset Setup

The code uses the folder named "dataset" located in [files/02_dataset](/files/02_dataset/) by default. 

This dataset is available at [BIPV Facades Dataset repository](https://github.com/ycdrn/bipv_facades.git), along with its variants:
1. 00_UnstratUnaug
2. 01_StatUnaug
3. 02_StratAug

You can see the folder schema [here](/files/02_dataset/schema.txt).
Therefore, the full dataset path will for example be 

```
files/02_dataset/dataset/StratAug/train/image.jpg
```

## Model Loading

**Fine-tune models from pre-trained:** This project uses pre-trained MaskRCNN and SegFormer models available on Detectron2 and HuggingFace, which are then fine-tuned in [4_MaskRCNN_training](/code/4_MaskRCNN_training.ipynb) and [6_SegFormer_training](/code/6_SegFormer_training.ipynb). Following these scripts will download the pre-trained (but not yet fine-tuned) model checkpoints in [files/03_model_checkpoints](/files/03_model_checkpoints/), and proceed with fine-tuning.

**Load already fine-tuned models**: Instead of fine-tuning from scratch, the models referred to in the paper can be found in [Hugging Face](https://huggingface.co/aycaduran/BIPVfinder). These checkpoint files need to be downloaded manually (or using Colab) and placed in [files/03_model_checkpoints](/files/03_model_checkpoints/), and selected in the model evaluation scripts [5_MaskRCNN_eval.ipynb](/code/5_maskrcnn_eval.ipynb) and [7_SegFormer_eval.ipynb](/code/7_segformer_eval.ipynb)

## Citation
If using our dataset/model, please cite us as follows:
```bibtex
@article{DURAN2026114292,
title = {Deep learning for BIPV segmentation on facades: Comparison with human annotations across facade designs},
journal = {Building and Environment},
pages = {114292},
year = {2026},
issn = {0360-1323},
doi = {https://doi.org/10.1016/j.buildenv.2026.114292},
url = {https://www.sciencedirect.com/science/article/pii/S0360132326000983},
author = {Ayca Duran and Pedram Mirabian and Panagiotis Karapiperis and Christoph Waibel and Bernd Bickel and Arno Schlueter}
}
```

## References
 [BIPV Facades Dataset](https://github.com/ycdrn/bipv_facades.git)<br>
 [MMSegmentation](https://github.com/open-mmlab/mmsegmentation)<br> 
 [Detectron 2](https://detectron2.readthedocs.io/en/latest/)
