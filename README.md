# Awesome Drug Response Prediction (ADRP)

The ADRP is a curated list of resources for drug response prediction research maintained by Brian.

# Goal

To identify effective anti-cancer drugs for patients by examining each patient's unique gene level information using machine learning algorithm.

# Challenges

Currently, there are three major challenges regarding training data: 1) Scarcity, 2) Low ratio of samples to features (LRSF), and 3) Heterogeneity

## 1. Scarcity: Volume of data

- Lack of [cancer clinical data](https://docs.gdc.cancer.gov/Encyclopedia/pages/Clinical_Data/)

> Approaches

- Merge multiple data for training : Multi-omics data analysis 

  Regarding when to merge multi-omics data for training, there are two different ways.

  1. Early integration : Concatenate omics data, then learn features via autoencoders
     - Disdavangages
       1. Each omics' unique distribution is disregarded
       2. Must be normalized appropriately
       3. Dimention is increased      
  2. Late integration : Learn features, then concatnate
     - Avoid disadvantages of early integration method
     - Ex) MOLI (Sharifi-Noghabi et al., 2019) : Somatic mutation, CNA, gene expression data were used for training. 

- [Transfer learning](https://en.wikipedia.org/wiki/Transfer_learning)
- [Domain adaptation](https://en.wikipedia.org/wiki/Domain_adaptation)

![Domain adaptation](https://upload.wikimedia.org/wikipedia/commons/1/11/Transfer_learning_and_domain_adaptation.png) 
<p align="center">Source: wikipedia</p>

## 2. Characteristics of data

- High dimensionality
- Low ratio of samples to features: The number of features often exceeds 10,000 while the number of samples is around 800. Thus, it is not ideal data set for Deep Neural Network (DNN).
- Imbalanced classes: The number of samples in each class are extremly imbalanced. In general, the number of sensitive (1) is smaller than the number of resistant (0).

> Approaches 

- Multi-task learning (MTL)
- [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering)
- [Autoencoder](https://en.wikipedia.org/wiki/Autoencoder): Feature extraction

## 3. Heterogeneity: Difference between _in vitro_ and _in vivo_.

- Whereas training data are from cell lines or animal models(PDX), test data are from patiens. And there is difference between these two types of data.
- According to research articles, the difference is caused by batch effect.

> Approaches
 
- Domain adaptation (DA)

# Methods

## Measurement

- The half-maximal inhibitory concentration ([IC<sub>50</sub>](https://en.wikipedia.org/wiki/IC50)): Amount of drug inhibiting biological component by 50%

## Type of data

Typically, data frame consists of rows representing samples and columns representing features and label.

### Features
- [Gene expression](https://en.wikipedia.org/wiki/Gene_expression)
- [Mutations](https://www.genome.gov/genetics-glossary/Mutation)
- [Copy number aberrations (CNA)](https://en.wikipedia.org/wiki/Copy_number_variation)
- [Epigenetic data](https://en.wikipedia.org/wiki/Epigenetics)
- ...

### Label (class)

- Drug sensitivity ([IC<sub>50</sub>](https://en.wikipedia.org/wiki/IC50)) : Sensitive (1) or Resistant (0)

## Public data for training

### Database for preclinical data

| Database | Samples | Features | Label |
| -------- | ---------- | ---------- | ---------- |
| Cancer Cell Line Encyclopedia (CCLE) | Tumor cell lines | GE, Mutation, CNA(?) | [IC<sub>50</sub>](https://en.wikipedia.org/wiki/IC50) |
| [Genomics of Drug Sensitivity in Cancer (GDSC)](https://www.cancerrxgene.org/) | Tumor cell lines | GE, Mutation, CNA | [IC<sub>50</sub>](https://en.wikipedia.org/wiki/IC50) | 
| Patient-Derived Xenografts (PDX) | Animal model | GE, Mutation, CNA | [RECIST](https://recist.eortc.org/) |

### Clinical data

| Database | Samples | Features | Label |
| -------- | ---------- | ---------- | ---------- |
| [The Cancer Genome Atlas (TCGA)](https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga) | Patients | ? | ? |
| 2014 | Patients | ? | ? |

### Anti-cancer drugs

- Docetaxel
- Cisplatin
- Gemcitabine
- Paclitaxel
- Erlotinib
- Cetuximab
- ...

## Common machine learning library

- [PyTorch](https://pytorch.org/)
- [Keras](https://keras.io/) / [Tensorflow](https://www.tensorflow.org/)
- [scikit-learn](https://scikit-learn.org/stable/index.html)

## Machine learning algorithms

Drug response prediction is a binary classification problem (sensitive or resistant). Therefore, any binary classifier can be used to estimate drug response.

- [K-Nearest Neighbors (kNN)](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)
- [Support Vector Machine (SVM)](https://en.wikipedia.org/wiki/Support-vector_machine)
- [Ridge Logistic Regression](https://scikit-learn.org/stable/modules/linear_model.html)
- [Random Forests](https://en.wikipedia.org/wiki/Random_forest)
- [Deep Neural Network (DNN)](https://en.wikipedia.org/wiki/Deep_learning)

# References

## Survey

- Adam, G., Rampášek, L., Safikhani, Z., Smirnov, P., Haibe-Kains, B., & Goldenberg, A. (2020). Machine learning approaches to drug response prediction: Challenges and recent progress. Npj Precision Oncology, 4(1), 1–10. https://doi.org/10.1038/s41698-020-0122-1
- Chen, J., & Zhang, L. (2021). A survey and systematic assessment of computational methods for drug response prediction. Briefings in Bioinformatics, 22(1), 232–246. https://doi.org/10.1093/bib/bbz164
- Firoozbakht, F., Yousefi, B., & Schwikowski, B. (2022). An overview of machine learning methods for monotherapy drug response prediction. Briefings in Bioinformatics, 23(1), bbab408. https://doi.org/10.1093/bib/bbab408

## Algorithms

### Deep learning

- Sakellaropoulos, T., Vougas, K., Narang, S., Koinis, F., Kotsinas, A., Polyzos, A., Moss, T. J., Piha-Paul, S., Zhou, H., Kardala, E., Damianidou, E., Alexopoulos, L. G., Aifantis, I., Townsend, P. A., Panayiotidis, M. I., Sfikakis, P., Bartek, J., Fitzgerald, R. C., Thanos, D., … Gorgoulis, V. G. (2019). A Deep Learning Framework for Predicting Response to Therapy in Cancer. Cell Reports, 29(11), 3367-3373.e4. https://doi.org/10.1016/j.celrep.2019.11.017
- Sharifi-Noghabi, H., Zolotareva, O., Collins, C. C., & Ester, M. (2019). MOLI: Multi-omics late integration with deep neural networks for drug response prediction. Bioinformatics, 35(14), i501–i509. https://doi.org/10.1093/bioinformatics/btz318

## Datasets

- Ding, Z., Zu, S., & Gu, J. (2016). Evaluating the molecule-based prediction of clinical drug responses in cancer. Bioinformatics (Oxford, England), 32(19), 2891–2895. https://doi.org/10.1093/bioinformatics/btw344
- Gao, H., Korn, J. M., Ferretti, S., Monahan, J. E., Wang, Y., Singh, M., Zhang, C., Schnell, C., Yang, G., & Zhang, Y. (2015). High-throughput screening using patient-derived tumor xenografts to predict clinical trial drug response. Nature Medicine, 21(11), 1318–1325.
- Iorio, F., Knijnenburg, T. A., Vis, D. J., Bignell, G. R., Menden, M. P., Schubert, M., Aben, N., Gonçalves, E., Barthorpe, S., & Lightfoot, H. (2016). A landscape of pharmacogenomic interactions in cancer. Cell, 166(3), 740–754.

