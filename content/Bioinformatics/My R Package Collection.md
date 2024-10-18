---
author: Harvey Guo
created: 2024-06-29 14:58
modified: 2024-06-29 14:58
aliases: []
share: true
---
# Pipeline
---
1. targets
	- Turn scripts into manageable pipeline
	- Automatically save and load important objects, and keep them in track
	- Very suitable for median or large projects
# Analysis
---
## Common
1. genekitr: [🧬 Welcome to genekitr! | Genekitr: Gene Analysis Toolkit based on R](https://www.genekitr.fun/)
	- More visualization for ORA and GSEA results
	- Better gene ID conversion function
		- Automatically identify input type
		- Distinguish from symbol and alias
2. tidyomics: [tidyomics/tidyomics: Easily install and load packages from the tidyomcis ecosystem (github.com)](https://github.com/tidyomics/tidyomics)
	- A collection of packages for omics data analysis that are consistent with tidyverse ecosystem
## RNA-seq (bulk)
1. tidySummarizedExperiment: [Brings SummarizedExperiment to the Tidyverse • tidySummarizedExperiment (stemangiola.github.io)](https://stemangiola.github.io/tidySummarizedExperiment/)
	- tidySummarizedExperiment provides a bridge between Bioconductor SummarizedExperiment and the tidyverse. It creates an invisible layer that <span style="background:rgba(240, 200, 0, 0.2)">enables viewing the Bioconductor SummarizedExperiment object as a tidyverse tibble, and provides SummarizedExperiment-compatible dplyr, tidyr, ggplot and plotly functions.</span> This allows users to get the best of both Bioconductor and tidyverse worlds.
2. tidybulk
	- Seamlessly integrated with `tidySummarizedExperiment`
	- Provide many out-of-box functions for bulk RNA-seq pipeline
## scRNA-seq
1. escape: [ncborcherding/escape: Easy single cell analysis platform for enrichment (github.com)](https://github.com/ncborcherding/escape)
	- The escape package allows users to easily incorporate multiple methods of GSEA and offers several visualization and analysis methods.
# Visualization
---
1. ggstatsplot: [ggplot2 Based Plots with Statistical Details • ggstatsplot (indrajeetpatil.github.io)](https://indrajeetpatil.github.io/ggstatsplot/index.html)
	- Can automatically choose and perform statistical analysis, and depict it on plot
2. ggraph & tidyraph
	- Use tidyverse way to create network
3. tidyheatmaps
	- Use tidyverse way to create heatmaps
	- Support all features of `pheatmap`
4. ggsci: [Scientific Journal and Sci-Fi Themed Color Palettes for ggplot2 • ggsci (nanx.me)](https://nanx.me/ggsci/index.html)
	- A collection of ggplot2 color palettes inspired by scientific journals and data visualization libraries
	- Only has up to 10 colors in each palette, and expanding the colors could be tricky