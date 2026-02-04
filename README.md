# Deep learning for BIPV segmentation on facades <br> Comparison with human annotations across facade designs

[Ayca Duran](https://systems.arch.ethz.ch/ayca-duran), [Pedram Mirabian](https://www.linkedin.com/in/pmirabian/?originalSubdomain=ch), [Panagiotis Karapiperis](https://www.linkedin.com/in/panagiotis-karapiperis-ethz/?originalSubdomain=ch), [Christoph Waibel](https://www.linkedin.com/in/christoph-waibel-19205114b/?originalSubdomain=ch), [Bernd Bickel](https://berndbickel.com/about-me), [Arno Schlueter](https://systems.arch.ethz.ch/arno-schlueter)

[[ Paper ]](https://doi.org/10.1016/j.buildenv.2026.114292)

## Table of Contents
1. [Abstract](#abstract)
2. [Model Setup Instructions](#model-setup-instructions)
3. [Citation](#citation)
4. [Acknowledgements](#acknowledgements)

## Abstract
Building-integrated photovoltaics (BIPV) on facades are a significant but underutilized source of solar energy in urban environments. Automating the recognition of BIPV on facades through vision based systems can help guide design recommendations and extend solar asset maps. Unlike rooftop photovoltaic (PV) systems, facade BIPV recognition is difficult due to limited visibility in overhead imagery, high visual variability, and the absence of structured datasets. This study proposes a method based on deep learning (DL) for automated segmentation of BIPV panels on building facades using street-level and web images. A new dataset comprising 400 annotated BIPV projects was created, including detailed pixel-level masks and project attributes. Two model architectures, Mask Region-based Convolutional Neural Network (Mask R-CNN) and SegFormer, as well as human baselines are evaluated. The SegFormer model outperforms Mask R-CNN in pixel-level metrics. A user study conducted with human annotators without domain-specific expertise provides comparative insight into human performance, revealing common challenges in recognizing facade BIPV. The results demonstrate that DL models, trained specifically for this task, can segment BIPV panels more accurately than mean of human annotators, with SegFormer achieving an IoU of 0.69 compared to 0.42. The user study suggests that BIPV with satin finishes, invisible cells, and a PV-to-facade ratio of more than half challenge human recognition and therefore can be prioritized in visually sensitive areas. The outputs of the segmentation model are also utilized to estimate the BIPV energy yield. The annotated dataset and models are made available to facilitate future research.
## Code Setup Instructions
Tba

## Model Setup Instructions
Tba
<!--- This repository contains the dataset, the pre-trained topic model, and a Python notebook to demonstrate the use of the pre-trained model. --->

### Prerequisites
Tba
<!--- - Anaconda or Miniconda must be installed on your machine. You can download it from [Anaconda's site](https://www.anaconda.com/products/individual). -->

### Environment Setup
Tba 

### Model Loading
Tba

### To Do
– Update file system managing <br> 
– Upload model ckpts to Huggingface

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
