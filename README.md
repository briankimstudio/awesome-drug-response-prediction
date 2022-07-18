# Awesome Drug Response Prediction (ADRP)

The ADRP is a curated list of resources for drug response prediction research maintained by Brian.

# Goal

To identify effective anti-cancer drugs for patients by examining each patient's unique gene level information using machine learning algorithm.

# Challenges

Curently, there are two major challenges regarding training data: Volume and low ratio of samples to features (LRSF)

## 1. Volume of data

- Lack of clinical data

> Approaches

- Merge multiple data for training (Sharifi-Noghabi et al., 2019)
- Transfer learning

## 2. Characteristics of data

- Low ratio of samples to features: The number of features often exceeds 10,000. Thus, it is not ideal data set for Deep Neural Network (DNN).
- Imbalanced classes: The number of samples in each class are extremly imbalanced. In general, the number of sensitive (1) is smaller than the number of resistant (0).

> Approaches 

- Feature engineering
- Autoencoders: Feature extraction

# Methods

## Measurement

- The half-maximal inhibitory concentration (IC<sub>50</sub>): Amount of drug inhibiting biological component by 50%

## Type of data

### Features
- Gene expression
- Mutations
- Copy number alterations (CNA)
- Epigenetic data
- ...

### Label (class)

- Drug sensitivity (IC<sub>50</sub>) : Sensitive (1) or Resistant (0)

## Public data for training

### Database for preclinical data

| Database | Lable type |
| -------- | ---------- |
| Cancer Cell Line Encyclopedia (CCLE) | ? |
| Genomics of Drug Sensitivity in Cancer (GDSC) | IC<sub>50</sub> |
| Patient-Derived Xenografts (PDX) | RECIST |

### Clinical data

| Database | Lable type |
| -------- | ---------- |
| The Cancer Genome Atlas (TCGA) | ? |

## Machine learning algorithms

Drug response prediction is a binary classification problem (sensitive or resistant). Therefore, any binary classifier can be used to estimate drug response.

- kNN
- SVM
- Ridge logistic regression
- Random forests
- Neural network

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

