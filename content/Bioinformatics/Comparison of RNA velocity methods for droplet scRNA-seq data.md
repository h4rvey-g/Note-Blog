---
author: Harvey Guo
created: 2024-11-13 16:22
modified: 2024-11-13 16:22
aliases: []
share: true
---
|           Method ID            | Agreement | Strand-aware | Counting of multi-gene reads |                                               Comments                                               |
| :----------------------------: | :-------: | :----------: | :--------------------------: | :--------------------------------------------------------------------------------------------------: |
|        _alevin_sep_gtr_        |   good    |     yes      |             yes              |                                                                                                      |
|       _alevin_coll_gtr_        |   good    |     yes      |             yes              |                                                                                                      |
|   _kallisto_\|_bus_sep_excl_   |   good    |      no      |              no              |                            Reads in ambiguous regions typically discarded                            |
|           _starsolo_           |   good    |     yes      |              no              |                                                                                                      |
|    _alevin_coll_decoy_gtr_     | variable  |     yes      |             yes              |                                                                                                      |
|           _velocyto_           | variable  |     yes      |              no              |                                                                                                      |
|  _kallisto_\|_bus_coll_excl_   | variable  |      no      |              no              |                                                                                                      |
|     _alevin_sep_decoy_gtr_     |   poor    |     yes      |             yes              |                              Reads in ambiguous regions double-counted.                              |
| _alevin_spliced_unspliced_gtr_ | variable  |     yes      |             yes              |        3’ tag protocols does not provide enough information for spliced/unspliced resolution.        |
|           _dropest_            |   poor    |      no      |          partially           |                                     Insufficient UMI collapsing                                      |
|  _kallisto_\|_bus_coll_incl_   |   poor    |      no      |              no              |                                                                                                      |
|   _kallisto_\|_bus_sep_incl_   |   poor    |      no      |              no              |                              Reads in ambiguous regions double-counted.                              |
|        _starsolo_diff_         | variable  |     yes      |          partially           | Non-zero unspliced count possible even without introns; nominally negative unspliced count possible. |

Reference: Soneson C, Srivastava A, Patro R, Stadler MB. Preprocessing choices affect RNA velocity results for droplet scRNA-seq data. PLoS Comput Biol. 2021 Jan 11;17(1):e1008585. doi: [10.1371/journal.pcbi.1008585](https://doi.org/10.1371/journal.pcbi.1008585). PMID: 33428615; PMCID: [PMC7822509](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7822509).