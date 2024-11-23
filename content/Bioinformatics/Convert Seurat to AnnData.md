---
author: Harvey Guo
created: 2024-11-20 16:00
modified: 2024-11-20 16:00
aliases: []
share: true
---
```r
# Currently scCustomize 3.0.0 is not released yet. You may want to use 
pak::pkg_install("samuel-marsh/scCustomize@release/3.0.0")
# to get the latest features
scCustomize::as.anndata(x = pbmc, file_path = "~/Desktop", file_name = "pbmc_anndata.h5ad")
```
