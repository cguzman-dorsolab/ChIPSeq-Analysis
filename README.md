# ChIPSeq-Analysis
Documentation for CHIP SEQ ANALYSIS

### Resources for ChIP-seq data 
1. [ENCODE: Encyclopedia of DNA Elements](https://www.encodeproject.org/)  
2. [ENCODE Factorbook](https://www.encodeproject.org/)  
3. [ChromNet ChIP-seq interactions](http://chromnet.cs.washington.edu/#/?search=&threshold=0.5)  
    paper: [Learning the human chromatin network using all ENCODE ChIP-seq datasets](http://biorxiv.org/content/early/2015/08/04/023911)  
4. [The International Human Epigenome Consortium (IHEC) epigenome data portal](http://epigenomesportal.ca/ihec/index.html?as=1)
5. [GEO](http://www.ncbi.nlm.nih.gov/gds/?term=). Sequences are in .sra format, need to use sratools to dump into fastq.
6. [European Nucleotide Archive](http://www.ebi.ac.uk/ena). Sequences are available in fastq format.
7. [Data bases and software from Sheirly Liu's lab at Harvard](http://liulab.dfci.harvard.edu/WEBSITE/software.htm)
8. [Blueprint epigenome](http://dcc.blueprint-epigenome.eu/#/home)
9. [A collection of tools and papers for nucelosome positioning and TF ChIP-seq](http://generegulation.info/)

### Papers on ChIP-seq
1. [ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia](http://www.ncbi.nlm.nih.gov/pubmed/22955991) 
2. [Practical Guidelines for the Comprehensive Analysis of ChIP-seq Data](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1003326)    
3. [Systematic evaluation of factors influencing ChIP-seq fidelity](http://www.nature.com/nmeth/journal/v9/n6/full/nmeth.1985.html)
4. [ChIP–seq: advantages and challenges of a maturing technology](http://www.nature.com/nrg/journal/v10/n10/abs/nrg2641.html)
5. [ChIP–seq and beyond: new and improved methodologies to detect and characterize protein–DNA interactions](http://www.nature.com/nrg/journal/v13/n12/abs/nrg3306.html) 
6. [Beyond library size: a field guide to NGS normalization](http://biorxiv.org/content/early/2014/06/19/006403)
7. [ENCODE paper portol](http://www.nature.com/encode/threads)  
8. [Enhancer discovery and characterization](http://www.nature.com/encode/threads/enhancer-discovery-and-characterization)  

    **Protocols**  
1. [A computational pipeline for comparative ChIP-seq analyses](http://www.ncbi.nlm.nih.gov/pubmed/22179591)    
2. [Identifying ChIP-seq enrichment using MACS](http://www.nature.com/nprot/journal/v7/n9/full/nprot.2012.101.html)  
3. [Spatial clustering for identification of ChIP-enriched regions (SICER) to map regions of histone methylation patterns in embryonic stem cells](http://www.ncbi.nlm.nih.gov/pubmed/24743992)
4. [ENCODE tutorials](http://www.genome.gov/27553900) 
5. [A User's Guide to the Encyclopedia of DNA Elements (ENCODE)](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001046)

### Peak calling  

It is important to have controls for your ChIP-seq experiments. A DNA input control (no antibody is applied) is preferred.
The IgG control is also fine, but because so little DNA is there, you might get many duplicated reads due to PCR artifacts.

1. The most popular peak caller by Tao Liu: [MACS2](https://github.com/taoliu/MACS/).
2. [HOMER](http://homer.salk.edu/homer/ngs/peaks.html) can also used to call Transcription factor ChIP-seq peaks and histone 
    modification ChIP-seq peaks.

**Different parameters using the same program can produce drasticly different sets of peaks especially for histone modifications with variable enrichment length and gaps between peaks. You need to be able to make a valid argument for the parameters you use.** 

An example of different parameters for homer `findPeaks`:  
![](http://i.imgur.com/zT2mVwT.png)

### Gene set enrichment analysis for ChIP-seq peaks  
1. [Broad Enrich](http://broad-enrich.med.umich.edu/)  
2. [ChIP Enrich](http://chip-enrich.med.umich.edu/)  
3. [GREAT](http://bejerano.stanford.edu/great/public/html/) predicts functions of cis-regulatory regions.  
4. [ENCODE ChIP-seq significance tool](http://encodeqt.simple-encode.org/). Given a list of genes, co-regulating TFs will be identified.  
5. [cscan](http://159.149.160.51/cscan/) similar to the ENCODE significance tool.  
6. [CompGO: an R package for comparing and visualizing Gene Ontology enrichment differences between DNA binding experiments](http://www.biomedcentral.com/1471-2105/16/275)  
7. [interactive and collaborative HTML5 gene list enrichment analysis tool](http://amp.pharm.mssm.edu/Enrichr/)

### Peak annotation 

1. Homer [`annotatePeak`](http://homer.salk.edu/homer/ngs/annotation.html) 
2. Bioconductor package [ChIPseeker](http://bioconductor.org/packages/release/bioc/html/ChIPseeker.html) by [Guangchuan Yu](http://ygc.name/)   
   See an important post by him on 0 or 1 based [coordinates](http://ygc.name/2015/08/07/parsing-bed-coordinates/).

>Most of the software for ChIP annotation doesn't considered this issue when annotating peak (0-based) to transcript (1-based). To my knowledge, only HOMER consider this issue. After I figure this out, I have updated ChIPseeker (version >= 1.4.3) to fix the issue. - [Reference](http://ygc.name/2014/04/13/chipseeker-for-chip-peak-annotation/) 
