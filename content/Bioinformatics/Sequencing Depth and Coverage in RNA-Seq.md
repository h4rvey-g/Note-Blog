---
author: Harvey Guo
created: 2024-02-11 15:39
modified: 2024-02-11 15:39
aliases: []
share: true
---
Sequencing Depth/Sequencing Coverage/Depth of Coverage/Read Depth is the average number of times that a particular nucleotide is represented in a collection of random raw sequences ([https://www.nature.com/articles/nrg3642](https://www.nature.com/articles/nrg3642)). Basically, the average number of times you sequenced a nucleotide in the genome or transcript. This is an indication of accuracy. While mostly relevant for genomic sequencing, it can be important in RNA-seq if you are looking for different types of variation. I would recommend reading that linked review.
Breadth of Coverage refers to what proportion of the bases of a reference genome have a specified depth (i.e., Depth of Coverage)([https://www.metagenomics.wiki/pdf/definition/coverage-read-depth](https://www.metagenomics.wiki/pdf/definition/coverage-read-depth)). The examples given, 90% of the genome is covered at 1X depth - so that means 90% of the full sequence of the genome has been sequence at least once. If it was 70% covered at 5X, then 70% of the nucleotides in the genome have been sequenced five times.

Taken from that above review:
_Redundancy of coverage is also called the depth or the depth of coverage. In next-generation sequencing studies coverage is often quoted as average raw or aligned read depth, which denotes the expected coverage on the basis of the number and the length of high-quality leads before or after alignment to the reference. Although the terms depth and coverage can be used interchangeably (as they are in this Review), coverage has also been used to denote the breadth of coverage of a target genome, which is defined as the percentage of target bases that are sequenced a given number of times. For example, a genome sequencing study may sequence a genome to 30× average depth and achieve a 95% breadth of coverage of the reference genome at a minimum depth of ten reads._
However, for RNA-SEQ Read Depth or Sequencing Depth is the number of 'transcripts' from the RNA library you have sequenced = number of reads. Without context is is easy to get confused. Coverage could mean how many of the transcripts you have sequenced from the full transcriptome OR similar to genomic sequencing the number of times a base has been sequenced. The latter is relevant when looking for variants. It could also mean Read Depth depending on the person. There are no clear established definitions unfortunately.
