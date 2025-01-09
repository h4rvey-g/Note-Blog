---
author: Harvey Guo
created: 2025-01-01 20:25
modified: 2025-01-01 20:25
aliases: []
share: true
---
Cells within the tumour microenvironment (TME) can impact tumour development and influence treatment response. Computational approaches have been developed to deconvolve the TME from bulk RNA-seq. Using scRNA-seq profiling from breast tumours we simulate thousands of bulk mixtures, representing tumour purities and cell lineages, to compare the performance of nine TME deconvolution methods (BayesPrism, Scaden, CIBERSORTx, MuSiC, DWLS, hspe, CPM, Bisque, and EPIC). _S_ome methods are more robust in deconvolving mixtures with high tumour purity levels. Most methods tend to mis-predict normal epithelial for cancer epithelial as tumour purity increases, a finding that is validated in two independent datasets. The breast cancer molecular subtype influences this mis-prediction. <span style="background:rgba(240, 200, 0, 0.2)">BayesPrism and DWLS have the lowest combined numbers of false positives and false negatives, and have the best performance when deconvolving granular immune lineages.</span> Our findings highlight the need for more single-cell characterisation of rarer cell types, and suggest that tumour cell compositions should be considered when deconvolving the TME.

Reference: [Performance of tumour microenvironment deconvolution methods in breast cancer using single-cell simulated bulk mixtures | Nature Communications](https://www.nature.com/articles/s41467-023-41385-5)
