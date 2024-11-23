---
author: Harvey Guo
created: 2024-11-21 16:39
modified: 2024-11-21 16:39
aliases: []
share: true
---
# What makes refgenie better?
---
1. **It provides a command-line interface to download individual resources**. Think of it as `GitHub` for reference genomes. You just type `refgenie pull hg38/bwa_index`.
2. **It's scripted**. In case you need resources _not_ on the server, such as for a custom genome, you can `build` your own: `refgenie build custom_genome/bowtie2_index`.
3. **It simplifies finding local asset locations**. When you need a path to an asset, you can `seek` it, making your pipelines portable across computing environments: `refgenie seek hg38/salmon_index`.
4. **It provides remote operation mode**, useful for cloud applications. Get a path to an asset file hosted on AWS S3: `refgenie seekr hg38/fasta --remote-class s3`.
5. **It includes a Python API**. For tool developers, you use `rgc = refgenconf.RefGenConf("genomes.yaml")` to get a Python object with paths to any genome asset, _e.g._, `rgc.seek("hg38", "kallisto_index")`.
6. **It strictly determines genomes compatibility**. Users refer to genomes with arbitrary aliases, like "hg38", but refgenie uses sequence-derived identifiers to verify genome identity with asset servers.
# Commands
---
## Install and configure
```
pip install --user refgenie
export PATH=~/.local/bin:$PATH
refgenie init -c data/reference_data/genome_config.yaml
export REFGENIE=data/reference_data/genome_config.yaml
refgenie listr
```
## Download pre-built reference genome assets
The `listr` command _lists remote assets_ to see what's available:
`refgenie listr`

The `pull` _downloads_ the specific asset of your choice:
`refgenie pull GENOME/ASSET`

Where `GENOME` refers to a genome key (_e.g._ hg38) and `ASSET` refers to one or more specific asset keys (_e.g._ bowtie2_index). For example:
`refgenie pull hg38/bowtie2_index`

You can also pull many assets at once:
`refgenie pull --genome mm10 bowtie2_index hisat2_index`
## Refer to assets
```bash
refgenie seek rCRSd/fasta path/to/genomes/archive/rCRSd/fasta/default/rCRSd.fa
```