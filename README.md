# Deep learning for BIPV segmentation on facades <br> Comparison with human annotations across facade designs

[Ayca Duran](https://systems.arch.ethz.ch/ayca-duran), [Pedram Mirabian](https://www.linkedin.com/in/pmirabian/?originalSubdomain=ch), [Panagiotis Karapiperis](https://www.linkedin.com/in/panagiotis-karapiperis-ethz/?originalSubdomain=ch), [Christoph Waibel](https://www.linkedin.com/in/christoph-waibel-19205114b/?originalSubdomain=ch), [Bernd Bickel](https://berndbickel.com/about-me), [Arno Schlueter](https://systems.arch.ethz.ch/arno-schlueter)

[[ Paper ]](https://doi.org/10.1016/j.buildenv.2026.114292)

## Table of Contents
1. [Abstract](#abstract)
2. [Setup Instructions](#setup-instructions)
3. [Citation](#citation)
4. [Acknowledgements](#acknowledgements)

## Abstract
Building-integrated photovoltaics (BIPV) on facades are a significant but underutilized source of solar energy in urban environments. Automating the recognition of BIPV on facades through vision based systems can help guide design recommendations and extend solar asset maps. Unlike rooftop photovoltaic (PV) systems, facade BIPV recognition is difficult due to limited visibility in overhead imagery, high visual variability, and the absence of structured datasets. This study proposes a method based on deep learning (DL) for automated segmentation of BIPV panels on building facades using street-level and web images. A new dataset comprising 400 annotated BIPV projects was created, including detailed pixel-level masks and project attributes. Two model architectures, Mask Region-based Convolutional Neural Network (Mask R-CNN) and SegFormer, as well as human baselines are evaluated. The SegFormer model outperforms Mask R-CNN in pixel-level metrics. A user study conducted with human annotators without domain-specific expertise provides comparative insight into human performance, revealing common challenges in recognizing facade BIPV. The results demonstrate that DL models, trained specifically for this task, can segment BIPV panels more accurately than mean of human annotators, with SegFormer achieving an IoU of 0.69 compared to 0.42. The user study suggests that BIPV with satin finishes, invisible cells, and a PV-to-facade ratio of more than half challenge human recognition and therefore can be prioritized in visually sensitive areas. The outputs of the segmentation model are also utilized to estimate the BIPV energy yield. The annotated dataset and models are made available to facilitate future research.

# Setup Instructions

This repository contains the Python scripts and relevant files used in the fine-tuning and evaluation of the pre-trained models, as well evaluation of  human annotations referenced in the publication. 

In order to facilitate running the scripts, use **Google Colab**, with the files stored on the **Google Drive** of the account running the code. The primary storage requirement arises from the trained model checkpoint files, which are not included seperately (download instructions [below](#model-loading)).


### Prerequisites & Environment Setup

* All required libraries are either included in Google Colab by default, or installed in the Python notebook in which they are utilized. 

* For the notebooks dealing with model training or evaluation, using a GPU Colab instance is required.

* PV Facades Dataset (required, see [Dataset Setup](#dataset-setup))

* Fine-tuned models (optional, see [Model Loading Setup](#model-loading-setup))

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

The code uses the folder named "dataset" located in [files/02_dataset](/files/02_dataset/) by default, so the full dataset path will be files/02_dataset/dataset. 

This dataset is available [here](TODO-link), along with its variants:
1. UnstratUnaug
2. StatUnaug
3. StratAug

In each case, renaming the desired folder to "dataset" is the method with the least amount of changes needed to run the training and evaluation. You can see the folder schema [here](/files/02_dataset/schema.txt).

## Model Loading Setup

**Fine-tune models from pre-trained:** This project uses pre-trained MaskRCNN and SegFormer models available on Detectron2 and HuggingFace, which are then fine-tuned in [4_MaskRCNN_training](/code/4_MaskRCNN_training.ipynb) and [6_SegFormer_training](/code/6_SegFormer_training.ipynb). Following these scripts will download the pre-trained (but not yet fine-tuned) model checkpoints in [files/03_model_checkpoints](/files/03_model_checkpoints/), and proceed with fine-tuning.

**Load already fine-tuned models**: Instead of fine-tuning from scratch, the models referred to in the paper can be found [TODO here](https://huggingface.co/aycaduran). These checkpoint files need to be downloaded manually (or using Colab) and placed in [files/03_model_checkpoints](/files/03_model_checkpoints/), and selected in the model evaluation scripts [5_MaskRCNN_eval.ipynb](/code/5_maskrcnn_eval.ipynb) and [7_SegFormer_eval.ipynb](/code/7_segformer_eval.ipynb)

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

## Acknowledgements
 [MMSegmentation](https://github.com/open-mmlab/mmsegmentation)<br> 
 [Detectron 2](https://detectron2.readthedocs.io/en/latest/) 
