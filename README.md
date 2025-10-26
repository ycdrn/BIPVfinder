# Photovoltaic panel segmentation on building facades

[Ayca Duran](https://systems.arch.ethz.ch/ayca-duran), [Pedram Mirabian](https://www.linkedin.com/in/pmirabian/?originalSubdomain=ch), [Panagiotis Karapiperis](https://www.linkedin.com/in/panagiotis-karapiperis-ethz/?originalSubdomain=ch), [Christoph Waibel](https://www.linkedin.com/in/christoph-waibel-19205114b/?originalSubdomain=ch), [Bernd Bickel](https://berndbickel.com/about-me), [Arno Schlueter](https://systems.arch.ethz.ch/arno-schlueter)

[[ Paper ]](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5373186) – Submitted, October 2025

## Table of Contents
1. [Abstract](#abstract)
2. [Model Setup Instructions](#model-setup-instructions)
3. [Citation](#citation)
4. [Acknowledgements](#acknowledgements)

## Abstract
Building-integrated photovoltaics (BIPV) on facades are a significant but underutilized source of solar energy in urban environments. Automating the recognition of BIPV on facades through vision based systems can help guide design recommendations and extend solar asset maps. Unlike rooftop photovoltaic (PV) systems, facade BIPV recognition is difficult due to limited visibility in overhead imagery, high visual variability, and the absence of structured datasets. This study proposes a method based on deep learning (DL) for automated segmentation of BIPV panels on building facades using street-level and web images. A new benchmark data set comprising 400 annotated BIPV projects was created, including detailed pixel-level masks and project attributes. Two model architectures, Mask R-CNN and SegFormer, as well as human baselines are evaluated. The SegFormer model outperforms Mask R-CNN in pixel-level metrics. A user study conducted with non-expert annotators provides comparative insight into human performance, revealing common challenges in recognizing facade BIPV. The results demonstrate that DL models, trained specifically for this task, can segment BIPV panels more accurately than the average of human annotators, with SegFormer achieving a mean IoU of 0.69 compared to 0.41. The user study suggests that BIPV with satin or glossy finishes, invisible cells, and a PV-to-Facade ratio of more than half challenge human recognition and therefore can be prioritized in visually sensitive areas. The segmentation model is also utilized to estimate the BIPV energy yield. The annotated dataset and models are made publicly available to facilitate future research.

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

## Citation
If using our dataset/model, please cite us as follows:
```bibtex
@article{DURAN2025112310,
  title     = {A review on artificial intelligence applications for facades},
  journal   = {Tba},
  volume    = {Tba},
  pages     = {Tba},
  year      = Tba,
  issn      = {Tba},
  doi       = {Tba},
  author    = {Ayca Duran and Pedram Mirabian and  Panagiotis Karapiperis and Christoph Waibel and Bernd Bickel and Arno Schlueter}
}
```

## Acknowledgements

 – Tba
