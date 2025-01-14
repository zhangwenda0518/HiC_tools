# Hi-C data analysis tools and papers 

[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs) [![PR's Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)

Tools are added by publication date, newest on top. Unpublished tools are listed at the end of each section. See [Hi-C data notes](https://github.com/mdozmorov/HiC_data) and [single-cell Hi-C notes](https://github.com/mdozmorov/scHiC_notes) for more. Please, [contribute and get in touch](CONTRIBUTING.md)! See [MDnotes](https://github.com/mdozmorov/MDnotes) for other data science and genomics-related notes.

# Table of content

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Pipelines](#pipelines)
  - [QC, quality control](#qc-quality-control)
  - [Capture-C](#capture-c)
    - [Capture-C peaks](#capture-c-peaks)
  - [HiChIP](#hichip)
  - [4C](#4c)
- [Resolution improvement](#resolution-improvement)
  - [Simulation](#simulation)
- [Normalization](#normalization)
  - [CNV-aware normalization](#cnv-aware-normalization)
- [Reproducibility](#reproducibility)
- [AB compartments](#ab-compartments)
- [Peak/Loop callers](#peak-loop-callers)
- [Differential interactions](#differential-interactions)
- [TAD callers](#tad-callers)
  - [Architectural stripes](#architectural-stripes)
  - [Differential/timecourse TAD analysis](#differential-timecourse-tad-analysis)
- [Prediction of 3D features](#prediction-of-3d-features)
- [SNP-oriented](#snp-oriented)
- [CNV and Structural variant detection](#cnv-and-structural-variant-detection)
- [Visualization](#visualization)
- [De novo genome scaffolding](#de-novo-genome-scaffolding)
- [3D modeling](#3d-modeling)
- [Deconvolution](#deconvolution)
- [Haplotype separation](#haplotype-separation)
- [Papers](#papers)
  - [Methodological Reviews](#methodological-reviews)
  - [General Reviews](#general-reviews)
  - [Technology](#technology)
    - [Micro-C](#micro-c)
    - [Multi-way interactions](#multi-way-interactions)
    - [Imaging](#imaging)
  - [Normalization](#normalization-1)
  - [TAD detection](#tad-detection)
  - [Spectral clustering](#spectral-clustering)
- [Courses](#courses)
- [Labs](#labs)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Pipelines

- [FAN-C](https://github.com/vaquerizaslab/fanc) - Python pipeline for Hi-C processing. Input - raw FASTQ (aligned using BWA or Bowtie2, artifact filtering) or pre-aligned BAMs. KR or ICE normalization. Analysis and Visualization (contact distance decay, A/B compartment detection, TAD/loop detection, Average TAD/loop profiles, saddle plots, triangular heatmaps, comparison of two heatmaps). Automatic or modular. Compatible with .cool and .hic formats. [Tweet1](https://twitter.com/vaquerizas_lab/status/1225011187668209664?s=20), [Tweet2](https://twitter.com/vaquerizasjm/status/1339937903473025027?s=20). [Table 1](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-020-02215-9/tables/1) - detailed comparison of 13 Hi-C processing tools <details>
    <summary>Paper</summary>
    Kruse, Kai, Clemens B. Hug, and Juan M. Vaquerizas. "FAN-C: A Feature-Rich Framework for the Analysis and Visualisation of Chromosome Conformation Capture Data"  https://doi.org/10.1186/s13059-020-02215-9 Genome Biology 21, no. 1 (December 2020) 
</details>

- [HiCExplorer](https://github.com/deeptools/HiCExplorer/) - set of programs to process, normalize, analyze and visualize Hi-C data, Python, .cool format, conversion utilities. [Documentation](https://hicexplorer.readthedocs.io/) <details>
    <summary>Paper</summary>
    Ramírez, Fidel, Vivek Bhardwaj, Laura Arrigoni, Kin Chung Lam, Björn A. Grüning, José Villaveces, Bianca Habermann, Asifa Akhtar, and Thomas Manke. "High-Resolution TADs Reveal DNA Sequences Underlying Genome Organization in Flies"  https://doi.org/10.1038/s41467-017-02525-w Nature Communications 9, no. 1 (December 2018) 
</details> <details>
    <summary>Galaxy HiCExplorer</summary>
    [Galaxy HiCExplorer](https://hicexplorer.usegalaxy.eu/) - a web server for Hi-C data preprocessing, QC, visualization. [Docker container](https://github.com/deeptools/docker-galaxy-hicexplorer). Wolff, Joachim, Vivek Bhardwaj, Stephan Nothjunge, Gautier Richard, Gina Renschler, Ralf Gilsbach, Thomas Manke, Rolf Backofen, Fidel Ramírez, and Björn A. Grüning. "Galaxy HiCExplorer: A Web Server for Reproducible Hi-C Data Analysis, Quality Control and Visualization"  https://doi.org/10.1093/nar/gky504 Nucleic Acids Research 46, no. W1 (July 2, 2018). [v3 of the Galaxy HiCExplorer](https://hicexplorer.usegalaxy.eu/). Includes full analysis of Hi-C, Capture-C, scHi-C. Workflow-like description of tools/tasks for each data type. [scHiCExplorer](https://github.com/joachimwolff/scHiCExplorer) set of tools specifically designed for scHi-C data. [scHiCExplorer's documentation](https://schicexplorer.readthedocs.io/en/latest/). Wolff, Joachim, Leily Rabbani, Ralf Gilsbach, Gautier Richard, Thomas Manke, Rolf Backofen, and Björn A Grüning. "Galaxy HiCExplorer 3: A Web Server for Reproducible Hi-C, Capture Hi-C and Single-Cell Hi-C Data Analysis, Quality Control and Visualization"  https://doi.org/10.1093/nar/gkaa220 Nucleic Acids Research, (July 2, 2020)
</details>

- [GITAR](https://www.genomegitar.org/https://github.com/Zhong-Lab-UCSD/HiCtool) - full Hi-C pre-processing, normalization, TAD detection, and visualization. Python scripts wrapping other tools. Table 1 summarizes the functionality of existing tools. <details>
    <summary>Paper</summary>
    Calandrelli, Riccardo, Qiuyang Wu, Jihong Guan, and Sheng Zhong. “GITAR: An Open Source Tool for Analysis and Visualization of Hi-C Data.” Genomics, Proteomics & Bioinformatics 16, no. 5 (2018): 365–72. https://doi.org/10.1016/j.gpb.2018.06.006 
</details>

- [HiC-bench](https://github.com/NYU-BFX/hic-bench) - complete pipeline for Hi-C data analysis. <details>
    <summary>Paper</summary>
    Lazaris, Charalampos, Stephen Kelly, Panagiotis Ntziachristos, Iannis Aifantis, and Aristotelis Tsirigos. "HiC-Bench: Comprehensive and Reproducible Hi-C Data Analysis Designed for Parameter Exploration and Benchmarking"  https://doi.org/10.1186/s12864-016-3387-6 BMC Genomics 18, no. 1 (December 2017)
</details>

- [TADbit](https://github.com/3DGenomes/tadbit) - TADbit is a complete Python library to deal with all steps to analyze, model and explore 3C-based data. With TADbit, the user can map FASTsQ files to obtain raw interaction binned matrices (Hi-C like matrices), normalize and correct interaction matrices, identify and compare the Topologically Associating Domains (TADs), build 3D models from the interaction matrices, and finally, extract structural properties from the models. TADbit is complemented by TADkit for visualizing 3D models. <details>
    <summary>Paper</summary>
    Serra, François, Davide Baù, Mike Goodstadt, David Castillo, Guillaume J. Filion, and Marc A. Marti-Renom. "Automatic Analysis and 3D-Modelling of Hi-C Data Using TADbit Reveals Structural Features of the Fly Chromatin Colors"  https://doi.org/10.1371/journal.pcbi.1005665 PLoS Computational Biology 13, no. 7 (July 2017) 
</details>

- [HiCdat](https://github.com/MWSchmid/HiCdat) - Hi-C processing pipeline and downstream analysis/visualization. Analyses: normalization, correlation, visualization, comparison, distance decay, PCA, interaction enrichment test, epigenomic enrichment/depletion. <details>
    <summary>Paper</summary>
    Schmid, Marc W., Stefan Grob, and Ueli Grossniklaus. "HiCdat: A Fast and Easy-to-Use Hi-C Data Analysis Tool"  https://doi.org/10.1186/s12859-015-0678-x BMC Bioinformatics 16 (September 3, 2015) 
</details>

- [HiC-Pro](https://github.com/nservant/HiC-Pro) - Python and command line-based optimized and flexible pipeline for Hi-C data processing. [hicpro2juicebox](https://github.com/nservant/HiC-Pro/blob/master/bin/utils/hicpro2juicebox.sh) tool to generate Juicebox-compatible files (requires juicebox_clt.jar) <details>
    <summary>Paper</summary>
    Servant, Nicolas, Nelle Varoquaux, Bryan R. Lajoie, Eric Viara, Chong-Jian Chen, Jean-Philippe Vert, Edith Heard, Job Dekker, and Emmanuel Barillot. "HiC-Pro: An Optimized and Flexible Pipeline for Hi-C Data Processing."  https://doi.org/10.1186/s13059-015-0831-x Genome Biology 16 (December 1, 2015) - HiC pipeline, references to other pipelines, comparison. From raw reads to normalized matrices. Normalization methods, fast and memory-efficient implementation of iterative correction normalization (ICE). Data format. Using genotyping information to phase contact maps.
</details>

- [HiC_Pipeline](https://github.com/XiaoTaoWang/HiC_pipeline) - Python-based pipeline performing mapping, filtering, binning, and ICE-correcting Hi-C data, from raw reads (.sra, .fastq) to contact matrices. Additionally, converting to sparse format, performing QC. 

- [HiCUP](http://www.bioinformatics.babraham.ac.uk/projects/hicup/)  - Perl-based pipeline, alignment only, output BAM files. <details>
    <summary>Paper</summary>
    Wingett, Steven, Philip Ewels, Mayra Furlan-Magaril, Takashi Nagano, Stefan Schoenfelder, Peter Fraser, and Simon Andrews. "HiCUP: Pipeline for Mapping and Processing Hi-C Data"  https://doi.org/10.12688/f1000research.7334.1 F1000Research 4 (2015) - HiCUP pipeline, alignment only, removes artifacts (religations, duplicate reads) creating BAM files. Details about Hi-C sequencing artifacts. Used in conjunction with other pipelines.
</details>

- [Juicer](https://github.com/theaidenlab/juicebox/wiki/Download) - Java full pipeline to convert raw reads into Hi-C maps, visualized in Juicebox. Calls domains, loops, CTCF binding sites. `.hic` file format for storing multi-resolution Hi-C data. <details>
    <summary>Paper</summary>
    - Durand, Neva C., Muhammad S. Shamim, Ido Machol, Suhas S. P. Rao, Miriam H. Huntley, Eric S. Lander, and Erez Lieberman Aiden. "Juicer Provides a One-Click System for Analyzing Loop-Resolution Hi-C Experiments"  https://doi.org/10.1016/j.cels.2016.07.002 Cell Systems 3, no. 1 (July 2016)   
    - Rao, Suhas S. P., Miriam H. Huntley, Neva C. Durand, Elena K. Stamenova, Ivan D. Bochkov, James T. Robinson, Adrian L. Sanborn, et al. "A 3D Map of the Human Genome at Kilobase Resolution Reveals Principles of Chromatin Looping"  https://doi.org/10.1016/j.cell.2014.11.021 Cell 159, no. 7 (December 18, 2014)  - Juicer analysis example. TADs defined by frequent interactions. Enriched in CTCF and cohesin members. Five domain types. A1 and A2 enriched in genes. Chr 19 contains 6th pattern B6. Enrichment in different histone modification marks. TADs are preserved across cell types. Yet, differences between Gm12878 and IMR90 were detected. Boundaries detection by scanning image. Refs to the original paper.
</details>

- [ENCODE project Data Production and Processing Standard of the Hi-C Mapping Center, PDF](https://www.encodeproject.org/documents/75926e4b-77aa-4959-8ca7-87efcba39d79/@@download/attachment/comp_doc_7july2018_final.pdf)

- [Arima mapping pipeline](https://github.com/ArimaGenomics/mapping_pipeline) - Mapping pipeline for data generated using Arima-HiC

- [cword](https://github.com/dekkerlab/cworld-dekker) - perl cworld module and collection of utility/analysis scripts for C data (3C, 4C, 5C, Hi-C).

- [HiCpipe](https://github.com/ChenFengling/HiCpipe) - an efficient Hi-C data processing pipeline. It is based on Juicer and HiC-pro, which combines the advantages of these two processing pipelines. HiCpipe is much faster than Juicer and HiC-pro and can output multiple features of Hi-C maps.

- [my5C](http://my5c.umassmed.edu/) - web-based tools, well-documented analysis and visualization of 5S data.

- [nf-core-hic](https://github.com/nservant/nf-core-hic) - Analysis of Chromosome Conformation Capture data (Hi-C and more), Nextflow pipeline. https://github.com/nservant/nf-core-hic. Also, [nf-core/hic](https://github.com/nf-core/hic)

- [distiller-nf](https://github.com/mirnylab/distiller-nf) - Java modular Hi-C mapping pipeline for reproducible data analysis, nextflow pipeline. Alignment, filtering, aggregating Hi-C matrices.

- [4D Nucleome Hi-C Processing Pipeline](https://github.com/4dn-dcic/docker-4dn-hic), set of scripts wrapped in a Docker image. Works with `.hic` and `.cool` files. [Overview](https://data.4dnucleome.org/resources/data-analysis/hi_c-processing-pipeline)

- Abdennur, Nezar, and Leonid Mirny. "Cooler: Scalable Storage for Hi-C Data and Other Genomically-Labeled Arrays"  https://doi.org/10.1093/bioinformatics/btz540 Bioinformatics, January 1, 2020. 
    - [cooler](https://github.com/mirnylab/cooler) file format for storing Hi-C matrices, sparse, hierarchical, multi-resolution. `cooler` Python package for data loading, aggregation, merging, normalization (balancing), viewing, exporting data. Together with ["pairs" text-based format](https://github.com/4dn-dcic/pairix/blob/master/pairs_format_specification.md), and hic, cooler is accepted by the 4D Nucleome Consortium DAC. https://github.com/mirnylab/cooler, https://cooler.readthedocs.io/en/latest/
    - [cooltools](https://github.com/mirnylab/cooltools) - tools to work with .cool files, [Documentation](https://cooltools.readthedocs.io/en/latest/), https://github.com/mirnylab/cooltools
    - [hiclib](https://bitbucket.org/mirnylab/hiclib) - Python tools to QC, map, normalize, filter and analyze Hi-C data, https://bitbucket.org/mirnylab/hiclib
    - [hic2cool](https://github.com/4dn-dcic/hic2cool) - Lightweight converter between hic and cool contact matrices. https://github.com/4dn-dcic/hic2cool
    - [pairtools](https://github.com/mirnylab/pairtools) - tools for low-level processing of mapped Hi-C paired reads. https://github.com/mirnylab/pairtools. [Documentation](https://pairtools.readthedocs.io/en/latest/index.html)

### QC, quality control

- [qc3C](https://github.com/cerebis/qc3C) - Hi-C quality assessment method based on non-naturally occurring k-mers containing ligation artifacts (the proportion of "signal"). Details of various types for read-pairs, valid and invalid configurations. Tested on simulated and experimental data. Works of FASTQ or BAM files. Output - the breakdown of valid and invalid pairs (numbers, stacked barplots). Compatible with MultiQC. Conda, Docker, Singluarity installations. [Scripts for the paper](https://zenodo.org/record/4554522) <details>
    <summary>Paper</summary>
    DeMaere, Matthew Z., and Aaron E. Darling. "Qc3C: Reference-Free Quality Control for Hi-C Sequencing Data"  https://doi.org/10.1101/2021.02.24.432586 Preprint. Bioinformatics, February 25, 2021.
</details>

- [HiCNoiseMeasurer](https://github.com/JRowleyLab/HiCNoiseMeasurer) - a Python script to measure noise in .hic files using the auto-correlation function

- [HiCSampler](https://github.com/jrowleylab/hicsampler) - a Python script for subsetting .hic files

### Capture-C

- [CHiCANE](https://CRAN.R-project.org/package=chicane) - an R-based data processing and interaction calling toolkit for the analysis and interpretation of Capture Hi-C data (Arima, Dovetail). Data preprocessing with HiCUP (recommended), but BAMs from other pipelines are supported. Flexible regression modeling of the number of reads linking bait and target fragments, include distance. (Truncated) Negative binomial, Poisson distributions, zeros may be included, other covariates. Functionality to assess model fit. Similar tools - GOTHiC. CHiCAGO, ChiCMaxima. Protocol explaining each step. <details>
    <summary>Paper</summary>
    Holgersen, Erle M. "Identifying High-Confidence Capture Hi-C Interactions Using CHiCANE" https://doi.org/10.1038/s41596-021-00498-1 NATURE PROTOCOLS (April 2021)
</details>

- [CaptureCompendium](http://userweb.molbiol.ox.ac.uk/public/telenius/CaptureCompendium/) - all-in-one toolkit for the design, analysis and presentation of 3C experiments, combines oligonucleotide design [Capsequm2](http://apps.molbiol.ox.ac.uk/CaptureC/cgi-bin/CapSequm.cgi), sequence mapping and extraction [CCseqBasic](https://github.com/Hughes-Genome-Group/CCseqBasicS), statistical data presentation and distribution [CaptureCompare](https://github.com/Hughes-Genome-Group/CaptureCompare) with [Peaky](https://github.com/cqgd/pky) integration, [CaptureSee](https://capturesee.molbiol.ox.ac.uk/). Allows for multi-way interactions (Tri-C). Overview of previous tools doing parts. <details>
    <summary>Paper</summary>
    Telenius, Jelena M., Damien J. Downes, Martin Sergeant, A. Marieke Oudelaar, Simon McGowan, Jon Kerry, Lars L.P. Hanssen, et al. "CaptureCompendium: A Comprehensive Toolkit for 3C Analysis"  https://doi.org/10.1101/2020.02.17.952572 Preprint. Bioinformatics, February 18, 2020. 
</details>

- [capC-MAP](https://github.com/cbrackley/capC-MAP) - Capture-C analysis pipeline. Python and C++, run through a configuration file. Outputs bedGraph. Compared with HiC-Pro, better detects PCR duplicates, identifies more interactions. Normalization tuned for Capture-C data. [Documentation](https://capc-map.readthedocs.io/) <details>
    <summary>Paper</summary>
    Buckle, Adam, Nick Gilbert, Davide Marenduzzo, and Chris A Brackley. "capC-MAP: software for analysis of Capture-C data"  https://doi.org/10.1093/bioinformatics/btz480 Bioinformatics, 15 November 2019
</details>

- [GOPHER](https://github.com/TheJacksonLaboratory/Gopher) - probe design for Capture Hi-C. All, or selected, promoters, or around GWAS hits. <details>
    <summary>Paper</summary>
    Hansen, Peter, Salaheddine Ali, Hannah Blau, Daniel Danis, Jochen Hecht, Uwe Kornak, Darío G. Lupiáñez, Stefan Mundlos, Robin Steinhaus, and Peter N. Robinson. "GOPHER: Generator Of Probes for Capture Hi-C Experiments at High Resolution"  https://doi.org/10.1186/s12864-018-5376-4 BMC Genomics 20, no. 1 (December 2019). 
</details>

#### Capture-C peaks

- [ChiCMaxima](https://github.com/yousra291987/ChiCMaxima) - a pipeline for detection and visualization of chromatin loops in Capture Hi-C data. Loess smoothing combined with a background model to detect significant interactions Comparison with GOTHiC and CHiCAGO. <details>
    <summary>Paper</summary>
    Ben Zouari, Yousra, Anne M Molitor, Natalia Sikorska, Vera Pancaldi, and Tom Sexton. "ChiCMaxima: A Robust and Simple Pipeline for Detection and Visualization of Chromatin Looping in Capture Hi-C"  https://doi.org/10.1186/s13059-019-1706-3 Genome Biology, 22 May 2019
</details>

- [Peaky](https://github.com/cqgd/pky) - Bayesian sparse variable selection approach. The model proposes that for any given bait, the expected CHi-C signal at each prey fragment is expressed as a sum of contributions from a set of fragments directly contacting that bait. <details>
    <summary>Paper</summary>
    Eijsbouts, Christiaan Q, Oliver S Burren, Paul J Newcombe, and Chris Wallace. "Fine Mapping Chromatin Contacts in Capture Hi-C Data"  https://doi.org/10.1186/s12864-018-5314-5 BMC Genomics 20, no. 1 (December 2019). 
</details>

- [HiCapTools](https://github.com/sahlenlab/HiCapTools) - A software package that can design sequence capture probes for targeted chromosome capture applications and analyze sequencing output to detect proximities involving targeted fragments. Two probes are designed for each feature while avoiding repeat elements and non-unique regions. The data analysis suite processes alignment files to report genomic proximities for each feature at restriction fragment level and is isoform-aware for gene features. Statistical significance of contact frequencies is evaluated using an empirically derived background distribution. <details>
    <summary>Paper</summary>
    Anandashankar Anil, Rapolas Spalinskas, Örjan Åkerborg, Pelin Sahlén; "[HiCapTools: a software suite for probe design and proximity detection for targeted chromosome conformation capture applications"  https://doi.org/10.1093/bioinformatics/btx625 Bioinformatics, Volume 34, Issue 4, 15 February 2018
</details>

- [CHiCAGO](https://bioconductor.org/packages/Chicago/) protocol for Capture Hi-C analysis. Introduction into 3C-based technologies, as compared with Hi-C, Statistical model for background noise estimation, normalization, weighted p-value correction. Comparison with other tools (HiCapTools, CHiCMaxima, CHiCANE), downstream analysis with Peaky, Chicdiff. Preprocessing with HiCUP, input files (Table 1), how to create auxillary files and set parameters for different restriction enzymes (R, Python scripts), QC, visualization. [CHiCAGO R package](https://bioconductor.org/packages/Chicago/), [chicagoTools](https://bitbucket.org/chicagoTeam/chicago/src/master/), [PCHiCdata R package](https://bitbucket.org/chicagoTeam/chicago/src/master/PCHiCdata/inst/extdata/). <details>
    <summary>Paper</summary>
    Freire-Pritchett, Paula, Helen Ray-Jones, Monica Della Rosa, Chris Q. Eijsbouts, William R. Orchard, Steven W. Wingett, Chris Wallace, Jonathan Cairns, Mikhail Spivakov, and Valeriya Malysheva. "Detecting Chromosomal Interactions in Capture Hi-C Data with CHiCAGO and Companion Tools"  https://doi.org/10.1038/s41596-021-00567-5 Nature Protocols, August 9, 2021. 
    Cairns, Jonathan, Paula Freire-Pritchett, Steven W. Wingett, Csilla Várnai, Andrew Dimond, Vincent Plagnol, Daniel Zerbino, et al. "CHiCAGO: Robust Detection of DNA Looping Interactions in Capture Hi-C Data."  https://doi.org/10.1186/s13059-016-0992-2 Genome Biology 17, no. 1 (2016): 127.
</details>


### HiChIP

- [HiChIP-Peak](https://github.com/ChenfuShi/HiChIP_peaks) - HiChIP peak caller, focus on peaks at re-ligation sites. Peak filtering, then negative binomial model. Differential peak analysis similar to DiffBind. <details>
    <summary>Paper</summary>
    Shi, Chenfu, Magnus Rattray, and Gisela Orozco. "HiChIP-Peaks: A HiChIP Peak Calling Algorithm"  https://doi.org/10.1093/bioinformatics/btaa202 Bioinformatics, Volume 36, Issue 12, 15 June 2020
</details>

- [CID](https://groups.csail.mit.edu/cgs/gem/cid/) - Chromatin Interaction Discovery, call chromatin interactions from ChIA-PET. Outperforms ChIA-PET2, MANGO pipelines, call more peaks than HICCUPS, hichipper. Java implementation <details>
    <summary>Paper</summary>
    Guo, Yuchun, Konstantin Krismer, Michael Closser, Hynek Wichterle, and David K Gifford. "High Resolution Discovery of Chromatin Interactions"  https://doi.org/10.1093/nar/gkz051 Nucleic Acids Research, February 14, 2019. 
</details>

- [MAPS](https://github.com/ijuric/MAPS) - Model-based Analysis of PLAC-seq and HiChIP. A zero-truncated Poisson regression framework to explicitly remove systematic biases, normalize, call long-distance interactions. Compared with hichipper, identifies more long-range, biologically relevant interactions. Works with Arima's HiChIP data <details>
    <summary>Paper</summary>
    Juric, Ivan, Miao Yu, Armen Abnousi, Ramya Raviram, Rongxin Fang, Yuan Zhao, Yanxiao Zhang, et al. "MAPS: Model-Based Analysis of Long-Range Chromatin Interactions from PLAC-Seq and HiChIP Experiments"  https://doi.org/10.1371/journal.pcbi.1006982 April 15, 2019, 24.
</details>

- [HiChIP pipeline](https://hichip.readthedocs.io/) by Dovetail Genomics, technology and analysis steps.

### 4C

- [pipe4C](https://github.com/deLaatLab/pipe4C) - 4C-seq processing pipeline, R implementation. <details>
    <summary>Paper</summary>
    Krijger, Peter H.L., Geert Geeven, Valerio Bianchi, Catharina R.E. Hilvering, and Wouter de Laat. "4C-Seq from Beginning to End: A Detailed Protocol for Sample Preparation and Data Analysis"  https://doi.org/10.1016/j.ymeth.2019.07.014 Methods 170 (January 2020)
</details>

- [peakC](https://github.com/deWitLab/peakC) - an R package for non-parametric peak calling in 4C/Capture-c/PCHiC data. <details>
    <summary>Paper</summary>
    Geeven, Geert, Hans Teunissen, Wouter de Laat, and Elzo de Wit. "PeakC: A Flexible, Non-Parametric Peak Calling Package for 4C and Capture-C Data"  https://doi.org/10.1093/nar/gky443 Nucleic Acids Research 46, no. 15 (September 6, 2018)
</details>

- [4Cseqpipe](http://compgenomics.weizmann.ac.il/tanay/?page_id=367/) processing pipeline and a genome-wide 4C primer database. <details>
    <summary>Paper</summary>
    Werken, Harmen J. G. van de, Gilad Landan, Sjoerd J. B. Holwerda, Michael Hoichman, Petra Klous, Ran Chachik, Erik Splinter, et al. "Robust 4C-Seq Data Analysis to Screen for Regulatory DNA Interactions"  https://doi.org/10.1038/nmeth.2173 Nature Methods 9, no. 10 (October 2012) - 4C technology paper. Two different 4bp cutters to increase resolution. Investigation of beta-globin locus, interchromosomal interactions.
</details>

## Resolution improvement

 [VEHiCLE](https://github.com/Max-Highsmith/VEHiCLE) - a variational autoencoder (feature extraction, dimensionality reduction) and Generative Adversarial Network (maps low-dimensional vectors to Hi-C maps) for Hi-C resolution enhancement. Uses a combination of four loss functions: adversarial loss, variational loss, mean square error, and insulation score loss (interesting!). Intro into VAEs, GANs, loss functions. Uses GM12878, IMR90, K562, HMEC data. Compared using five metrics (similarity, reproducibility) against HiCPlus, DeepHic, HiCSR, outperforms all. Improves TAD identification, 3D structure modeling. Python implementation. <details>
    <summary>Paper</summary>
    Highsmith, Max, and Jianlin Cheng. "VEHiCLE: A Variationally Encoded Hi-C Loss Enhancement Algorithm for Improving and Generating Hi-C Data"  https://doi.org/10.1038/s41598-021-88115-9 Scientific Reports 11, no. 1 (December 2021)
</details>

- [DeepHiC](http://sysomics.com/deephic/) - a generative adversarial network (GAN) for enhancing Hi-C data. Does not change the bin size, enhances the content of Hi-C data. Reconstructs the content from \~1% of the original data. Outperforms BoostHiC, HiCPlus, HiCNN. [GitHub](https://github.com/omegahh/DeepHiC). <details>
    <summary>Paper</summary>
    - Hong, Hao, Shuai Jiang, Hao Li, Cheng Quan, Chenghui Zhao, Ruijiang Li, Wanying Li, et al. "DeepHiC: A Generative Adversarial Network for Enhancing Hi-C Data Resolution"  https://doi.org/10.1371/journal.pcbi.1007287 PLOS Computational Biology, February 21, 2020
</details>

- [HIFI](https://github.com/BlanchetteLab/HIFI) - Hi-C Interaction Frequency Inference for restriction fragment-resolution analysis of Hi-C data. Sparsity is resolved by using dependencies between neighboring restriction fragments, with Markov Random Fields performing the best. Better resolves TADs and sub-TADs, significant interactions. CTCF, RAD21, SMC3, ZNF143 are enriched around TAD boundaries. Matrices normalized for fragment-specific biases. <details>
    <summary>Paper</summary>
    - Cameron, Christopher JF, Josée Dostie, and Mathieu Blanchette. "Estimating DNA-DNA Interaction Frequency from Hi-C Data at Restriction-Fragment Resolution"  https://doi.org/10.1186/s13059-019-1913-y Genome Biology, 14 January 2020
</details>

- [HiCRes](https://github.com/ClaireMarchal/HiCRes) - resolution estimation, based on the linear dependence of 20th percentile of coverage and the window size used to access coverage. Includes preseq for estimating and predicting library complexity, bowtie2 and HiCUP for estimating Hi-C-specific QC metrics. Relatively insensitive to enzyme of choice. Implemented as Docker/Singularity images. Requires significant computational resources, like 5 hours on 40 CPU cluster. <details>
    <summary>Paper</summary>
    Marchal, Claire, Nivedita Singh, Ximena Corso-Díaz, and Anand Swaroop. "HiCRes: A Computational Method to Estimate and Predict the Resolution of HiC Libraries"  https://doi.org/10.1101/2020.09.22.307967 Preprint. Bioinformatics, September 22, 2020
</details>

- [HiCSR](https://github.com/PSI-Lab/HiCSR) - enhancement of Hi-C contact maps using a Generative Adversarial Network trained to optimize a custom loss function (weighted adversarial loss, pixel-wise L1 loss, and a feature reconstruction loss). An increase in resolution refers to recovering additional Hi-C contacts, "saturating" downsampled and noisy Hi-C matrices, not increasing the number of pixels. Representation learning with autoencoder with several convolutional layers and skip connections, then using it for the generator to create new matrices with discriminator telling them fake or real. Compared with HiCPlus, HiCNN, hicGAN, DeepHiC. Reproducibility is better using four metrics. Python3 PyTorch implementation. <details>
    <summary>Paper</summary>
    Dimmick, Michael C., Leo J. Lee, and Brendan J. Frey. "HiCSR: A Hi-C Super-Resolution Framework for Producing Highly Realistic Contact Maps"  https://doi.org/10.1101/2020.02.24.961714 Preprint. Genomics, February 25, 2020. 
</details>

- [hicGAN](https://github.com/kimmo1019/hicGAN) - improving resolution (saturation) of Hi-C data using Generative Adversarial Networks. Generator - five inner residual blocks to fight vanishing gradient (each block has two convolutional layers and batch normalization) and an outer skip connection. The discriminator has three convolutional blocks. Evaluation metrics: MSE, signal-to-noise ratio, structure similarity index, chromatin loop score. Compared against HiCPlus. Python, Tensorflow implementation. <details>
    <summary>Paper</summary>
    Liu, Qiao, Hairong Lv, and Rui Jiang. "HicGAN Infers Super Resolution Hi-C Data with Generative Adversarial Networks"  https://doi.org/10.1093/bioinformatics/btz317 Bioinformatics 35, no. 14 (July 15, 2019)
</details>

- [HiCNN](http://dna.cs.miami.edu/HiCNN/) - a computational method for resolution enhancement. A modification of the HiCPlus approach, using very deep (54 layers, five types of layers) convolutional neural network. A Hi-C matrix of regular resolution is transformed into the high-resolution but very sparse matrix, HiCNN predicts the missing values. Pearson and MSE evaluation metrics, overlap of Fit-Hi-C-detected significant interactions - perform similar or slightly better than HiCPlus. PyTorch implementation. <details>
    <summary>Paper</summary>
    Liu, Tong, and Zheng Wang. "HiCNN: A Very Deep Convolutional Neural Network to Better Enhance the Resolution of Hi-C Data"  https://doi.org/10.1093/bioinformatics/btz251 Bioinformatics, April 9, 2019
</details>

- [Boost-HiC](https://github.com/LeopoldC/Boost-HiC) - infer fine-resolution contact frequencies in Hi-C data, performs well even on 0.1% of the raw data. TAD boundaries remain. Better than HiCPlus. It can be used for differential analysis (comparison) of two Hi-C maps. <details>
    <summary>Paper</summary>
    Carron, Leopold, Jean-baptiste Morlot, Vincent Matthys, Annick Lesne, and Julien Mozziconacci. "Boost-HiC : Computational Enhancement of Long-Range Contacts in Chromosomal Contact Maps"  https://doi.org/10.1101/471607 November 18, 2018. 
</details>

- [HiCPlus](https://github.com/zhangyan32/HiCPlus) - increasing resolution of Hi-C data using convolutional neural network, mean squared error as a loss function. Basically, smoothing parts of Hi-C image, then binning into smaller parts. Performs better than bilinear/biqubic smoothing. <details>
    <summary>Paper</summary>
    Zhang, Yan, Lin An, Ming Hu, Jijun Tang, and Feng Yue. "HiCPlus: Resolution Enhancement of Hi-C Interaction Heatmap"  https://doi.org/10.1038/s41467-018-03113-2 March 1, 2017. 
</details>

- [mHi-C](https://github.com/keleslab/mHiC) - recovering alignment of multi-mapped reads in Hi-C data. Generative model to estimate probabilities for each bin-pair originating from a given origin. Reproducibility of contact matrices (stratum-adjusted correlation), reproducibility and number of significant interactions are improved. Novel interactions. Enrichment of TAD boundaries in LINE and SINE repetitive elements. Multi-mapping is not sensitive to trimming. Read filtering strategy (Figure 1, supplementary figures are very visual). <details>
    <summary>Paper</summary>
    Zheng, Ye, Ferhat Ay, and Sunduz Keles. "Generative Modeling of Multi-Mapping Reads with MHi-C Advances Analysis of High Throughput Genome-Wide Conformation Capture Studies"  https://doi.org/10.1101/301705 October 3, 2018.
</details>

### Simulation

- [FreeHi-C v.2.0]((https://github.com/keleslab/FreeHiC)) - simulation of realistic Hi-C matrices with user- or data-driven spike-ins. Spike-ins are introduced on read-level and converted to interaction frequency level. Benchmark of `HiCcompare`, `multiHiCcompare`, `diffHiC`, and `Selfish`. Assessment of FDR, power, significance order, PRC and AUROC, genomic properties. GM12878 and A549 replicates of experimental Hi-C data. Three simulation settings with varying background distribution of interaction frequencies, spike-in proportions, sequencing depth. Figure 5 - summary of performances for all methods and comparison types. Subjective top performers: `multiHiCcompare`, `HiCcompare`, `diffHiC`, `Selfish`.<details>
    <summary>Paper</summary>
    Zheng, Ye, Peigen Zhou, and Sündüz Keleş. "FreeHi-C Spike-in Simulations for Benchmarking Differential Chromatin Interaction Detection"  https://doi.org/10.1016/j.ymeth.2020.07.001 Methods, July 2020
</details>

- [FreeHi-C](https://github.com/keleslab/FreeHiC) - Hi-C data simulation based on properties of experimental Hi-C data. Preserves A/B compartments, TADs, the correlation between replicated (HiCRep), significant interactions, improves power to detect differential interactions. Robust to sequencing depth changes. Tested on replicates of GM12878, A549 human cancer cells, malaria P.falciparum. Compared with poorly performing Sim3C. All simulated data are at https://zenodo.org/record/3345896. Python3 implementation. <details>
    <summary>Paper</summary>
    Zheng, Ye, and Sündüz Keleş. "FreeHi-C Simulates High-Fidelity Hi-C Data for Benchmarking and Data Augmentation"  https://doi.org/10.1038/s41592-019-0624-3 Nature Methods 17, no. 1 (January 2020)
</details>

## Normalization

- [HiCorr](https://github.com/JinLabBioinfo/HiCorr) - a method for correcting known (mappability, CG content) and unknown (visibility) biases in Hi-C maps (multiplicative effects, Methods). Easy Hi-C protocol allowing for low-input (\~100K cells) Hi-C (in vivo HindIII digestion, in situ proximity ligation, DpnII digestion after lysis and reverse crosslink, Methods). HiCorr outputs ratio matrixes representing enrichment of Hi-C signal, hence loops can be easily extracted. Recovers 65% of HICCUPS loops and more. Chromatin loops are better marks of cell identity than compartments and outperform eQTLs in defining neurological GWAS target genes. Human iPSCs, neural progenitors (NPCs), neurons, fetal cerebellum, adult temporal cortex, data from other studies. <details>
    <summary>Paper</summary>
    Lu, Leina, Xiaoxiao Liu, Wei-Kai Huang, Paola Giusti-Rodríguez, Jian Cui, Shanshan Zhang, Wanying Xu, et al. "Robust Hi-C Maps of Enhancer-Promoter Interactions Reveal the Function of Non-Coding Genome in Neural Development and Diseases"  https://doi.org/10.1016/j.molcel.2020.06.007 Molecular Cell, June 2020
</details>

- [multiHiCcompare](https://bioconductor.org/packages/multiHiCcompare/) - R/Bioconductor package for joint normalization of multiple Hi-C datasets using cyclic loess regression through pairs of MD plots (minus-distance). Data-driven normalization accounting for the between-dataset biases. Per-distance edgeR-based testing of significant interactions. <details>
    <summary>Paper</summary>
    Stansfield, John C, Kellen G Cresswell, and Mikhail G Dozmorov. "MultiHiCcompare: Joint Normalization and Comparative Analysis of Complex Hi-C Experiments"  https://doi.org/10.1093/bioinformatics/btz048 Bioinformatics, January 22, 2019. 
</details>

- [normGAM](http://dna.cs.miami.edu/normGAM/) - an R package to normalize Genomic Architecture Mapping (GAM) data. New type of systematic bias, the fragment length bias. normGAM eliminates the fragment length bias resulting from random slicing, and biases related to window detection frequency, mappability, and GC content. Five normalization methods, including newly designed KR2 that handles negative values (others include the original GAM normalization algorithm normalized linkage disequilibrium NLD, VC, SCN, ICE). KR2 normalization produces better correlation with Hi-C data, all normalization methods improve concordance with FISH-detected distances.<details>
    <summary>Paper</summary>
    Liu, Tong, and Zheng Wang. "NormGAM: An R Package to Remove Systematic Biases in Genome Architecture Mapping Data"  https://doi.org/10.1186/s12864-019-6331-8 BMC Genomics, (December 2019)
</details>

- [Binless](https://github.com/3DGenomes/binless) - a resolution-agnostic normalization method that adapts to the quality and quantity of available data, to detect significant interactions and differences. Negative binomial count regression framework, adapted for ICE normalization. Fused lasso to smooth neighboring signals. TADbit for data processing, details of read filtering. <details>
    <summary>Paper</summary>
    - Spill, Yannick G., David Castillo, Enrique Vidal, and Marc A. Marti-Renom. "Binless Normalization of Hi-C Data Provides Significant Interaction and Difference Detection Independent of Resolution"  https://doi.org/10.1038/s41467-019-09907-2 Nature Communications 10, no. 1 (26 2019)
</details>

- [HiCcompare](https://bioconductor.org/packages/HiCcompare/) - R/Bioconductor package for joint normalization of two Hi-C datasets using loess regression through an MD plot (minus-distance). Data-driven normalization accounting for the between-dataset biases. Per-distance permutation testing of significant interactions. <details>
    <summary>Paper</summary>
    Stansfield, John C., Kellen G. Cresswell, Vladimir I. Vladimirov, and Mikhail G. Dozmorov. "HiCcompare: An R-Package for Joint Normalization and Comparison of HI-C Datasets"  https://doi.org/10.1186/s12859-018-2288-x BMC Bioinformatics 19, no. 1 (December 2018). 
</details>

- [HiFive](https://www.taylorlab.org/software/hifive/) - handling and normalization or pre-aligned Hi-C and 5C data. <details>
    <summary>Paper</summary>
    Sauria, Michael EG, Jennifer E. Phillips-Cremins, Victor G. Corces, and James Taylor. "HiFive: A Tool Suite for Easy and Efficient HiC and 5C Data Analysis"  https://doi.org/10.1186/s13059-015-0806-y Genome Biology 16, no. 1 (December 2015).  - HiFive - post-processing of aligned Hi-C and 5C data, three normalization approaches: "Binning" - model-based Yaffe & Tanay's method, "Express" - matrix-balancing approach, "Probability" - multiplicative probability model. Judging normalization quality by the correlation between matrices. 
</details>

- [HiCNorm](http://www.people.fas.harvard.edu/~junliu/HiCNorm/) - removing known biases in Hi-C data (GC content, mappability, fragment length) via Poisson regression. <details>
    <summary>Paper</summary>
    Hu, Ming, Ke Deng, Siddarth Selvaraj, Zhaohui Qin, Bing Ren, and Jun S. Liu. "HiCNorm: Removing Biases in Hi-C Data via Poisson Regression"  https://doi.org/10.1093/bioinformatics/bts570 Bioinformatics (Oxford, England) 28, no. 23 (December 1, 2012) - Poisson normalization. Also tested negative binomial.
</details>

### CNV-aware normalization

- Hi-C data normalization considering CNVs. Extension of matrix-balancing algorithm to either retain the copy-number variation effect (LOIC) or remove them (CAIC). ICE itself can lead to misrepresentation of the contact probabilities between CNV regions. Estimating CNV directly from Hi-C data correcting for GC content, mappability, fragment length using Poisson regression. LOIC - the sum of contacts for a given genomic bin is proportional to CNV. CAIC - raw interaction counts are the product of a CNV bias matrix and the expected contact counts at a given genomic distance. [Data](http://members.cbio.mines-paristech.fr/~nvaroquaux/normalization/), and [cancer-hic-norm](https://github.com/nservant/cancer-hic-norm) - Normalization of cancer Hi-C data, scripts for the manuscript. LOIC and CAIC methods are implemented in the [iced](https://github.com/hiclib/iced) Python package. <details>
    <summary>Paper</summary>
    Servant, Nicolas, Nelle Varoquaux, Edith Heard, Emmanuel Barillot, and Jean-Philippe Vert. "Effective Normalization for Copy Number Variation in Hi-C Data"  https://doi.org/10.1186/s12859-018-2256-5 BMC Bioinformatics 19, no. 1 (September 6, 2018)
</details>

- [OneD](https://github.com/qenvio/dryhic) - CNV bias-correction method, addresses the problem of partial aneuploidy. Bin-centric counts are modeled using the negative binomial distribution, and its parameters are estimated using splines. A hidden Markov model is fit to infer the copy number for each bin. Each Hi-C matrix entry is corrected by dividing its value by the square root of the product of CNVs for the corresponding bins. Reproducibility score (eigenvector decomposition and comparison) to measure improvement in the similarity between replicated Hi-C data. <details>
    <summary>Paper</summary>
    Vidal, Enrique, François leDily, Javier Quilez, Ralph Stadhouders, Yasmina Cuartero, Thomas Graf, Marc A Marti-Renom, Miguel Beato, and Guillaume J Filion. "OneD: Increasing Reproducibility of Hi-C Samples with Abnormal Karyotypes"  https://doi.org/10.1093/nar/gky064 Nucleic Acids Research, January 31, 2018. 
</details>

- [HiCapp](https://bitbucket.org/mthjwu/hicapp) - Iterative correction-based caICB method. Method to adjust for the copy number variants in Hi-C data. Loess-like idea - we converted the problem of removing the biases across chromosomes to the problem of minimizing the differences across the count-distance curves of different chromosomes. Our method assumes equal representation of genomic locus pairs with similar genomic distances located on different chromosomes if there were no bias in the Hi-C maps. <details>
    <summary>Paper</summary>
    Wu, Hua-Jun, and Franziska Michor. "A Computational Strategy to Adjust for Copy Number in Tumor Hi-C Data"  https://doi.org/10.1093/bioinformatics/btw540 Bioinformatics (Oxford, England) 32, no. 24 (December 15, 2016)
</details>

## Reproducibility

- [HPRep](https://github.com/yunliUNC/HPRep) - reproducibility measure for HiChIP and PLAC-seq data. HiCrep-inspired. Reorganize data into anchor-centric interaction bins, normalize (fragment length, GC content, mappability, log2 obs/exp) smooth, stratify by distance (concatenate bins with the same distance from anchors). Considering "AND" (bin-pairs), "XOR" (one anchor bin), "NOT" (no interactions, ignored) bin pairs. Distance metric - weighted Pearson correlation (pairs of columns) stratified by distance. Compared with HiCRep, HiC-Spector, and naive Pearson on mouse H3K4me3 PLAC-seq data (brain and mESCs), human H3K37ac HiChIP data from GM12878 and K562, human H3K4me3 PLAC-seq brain data. HPRep shows higher similarity for replicates and more differentiation between cell lines, robust to downsampling. Nearly same results can be achieved analysing one chromosome (for speed). <details>
    <summary>Paper</summary>
    Rosen, Jonathan D, Yuchen Yang, Armen Abnousi, Jiawen Chen, Michael Song, Yin Shen, Ming Hu, and Yun Li. "HPRep: Quantifying Reproducibility in HiChIP and PLAC-Seq Datasets"  https://doi.org/10.3390/cimb43020082 Current issues in molecular biology, 17 September 2021
</details>

- [HiCrep.py](https://github.com/dejunlin/hicrep) - a fast Python implementation of stratum-adjusted correlation coefficient metric for measuring similarity between Hi-C datasets (HiCrep method, originally in R). Can be used for MDS. Evaluated on 90 datasets from 4D Nucleome. More than 20 times faster on a single CPU. Results are the same as R implementation.<details>
    <summary>Paper</summary>
    Lin, Dejun, Justin Sanders, and William Staﬀord Noble. "HiCRep.Py: Fast Comparison of Hi-C Contact Matrices in Python"  https://doi.org/10.1093/bioinformatics/btab097 Bioinformatics, February 12, 2021
</details>

- [IDR2D](https://github.com/gifford-lab/idr2d) - Irreproducible Discovery Rate that identifies replicable interactions in ChIP-PET, HiChIP, and Hi-C data. Includes the original 1D IDR version (https://github.com/nboley/idr). Resolves multiple pairwise interactions. <details>
    <summary>Paper</summary>
    Krismer, Konstantin, Yuchun Guo, and David K Gifford. "IDR2D Identifies Reproducible Genomic Interactions"  https://doi.org/10.1093/nar/gkaa030 Nucleic Acids Research, 06 April 2020
</details>

- [3DChromatin_ReplicateQC](https://github.com/kundajelab/3DChromatin_ReplicateQC) - Comparison of four Hi-C reproducibility assessment tools, `HiCRep`, `GenomeDISCO`, `HiC-Spector`, `QuASAR-Rep`. Tested the effects of noise, sparsity, resolution. Spearman doesn't work well. All tools performed similarly, worsening expectedly. QuASAR has a QC tool measuring the level of noise. <details>
    <summary>Paper</summary>
    Yardimci, Galip, Hakan Ozadam, Michael E.G. Sauria, Oana Ursu, Koon-Kiu Yan, Tao Yang, Abhijit Chakraborty, et al. "Measuring the Reproducibility and Quality of Hi-C Data](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-019-1658-7 Genome Biology, March 19, 2019
</details>

- [localtadsim](https://github.com/Kingsford-Group/localtadsim) - Analysis of TAD similarity using a variation of information (VI) metric as a local distance measure. 23 human Hi-C datasets, Hi-C Pro processed into 100kb matrices, Armatus to call TADs. Defining structurally similar and variable regions. Comparison with previous studies of genomic similarity. Cancer-normal comparison - regions containing pan-cancer genes are structurally conserved in normal-normal pairs, not in cancer-cancer. <details>
    <summary>Paper</summary>
    - Sauerwald, Natalie, and Carl Kingsford. "Quantifying the Similarity of Topological Domains across Normal and Cancer Human Cell Types"  https://doi.org/10.1093/bioinformatics/bty265 Bioinformatics (Oxford, England) 34, no. 13 (July 1, 2018)
</details>

- [HiCRep](https://github.com/MonkeyLB/hicrep) - Similarity assessment using generalized Cochran-Mantel-Haenzel statistics M2. Spearman/Pearson doesn't work. 2-step procedure: Smooth the matrix, then CMH statistics. Basically, splitting data by distance chunks, Pearson on each chunk, summarize. Simple and well-thought stats. Methods: Hi-C datasets with replicates, including 11 ENCODE datasets. [R package](https://github.com/MonkeyLB/hicrep), and [Python implementation](https://github.com/cmdoret/hicreppy) <details>
    <summary>Paper</summary>
    Yang, Tao, Feipeng Zhang, Galip Gurkan Yardimci, Ross C Hardison, William Stafford Noble, Feng Yue, and Qunhua Li. "HiCRep: Assessing the Reproducibility of Hi-C Data Using a Stratum-Adjusted Correlation Coefficient](https://genome.cshlp.org/content/27/11/1939.long Genome Research, August 30, 2017
</details>

- [HiC-Spector](https://github.com/gersteinlab/HiC-spector) - reproducibility metric to quantify the similarity between contact maps using spectral decomposition. Decomposing Laplacian matrices and sum the Euclidean distance between eigenvectors. <details>
    <summary>Paper</summary>
    - Yan, Koon-Kiu, Galip Gürkan Yardimci, Chengfei Yan, William S. Noble, and Mark Gerstein. "HiC-Spector: A Matrix Library for Spectral and Reproducibility Analysis of Hi-C Contact Maps"  https://doi.org/10.1093/bioinformatics/btx152 Bioinformatics (Oxford, England) 33, no. 14 (July 15, 2017)
</details>

- [QuASAR] - Hi-C quality and reproducibility measure using spatial consistency between local and regional signals. Finds the maximum useful resolution by comparing quality and replicate scores of replicates. Part of the [HiFive pipeline](https://github.com/bxlab/hifive). <details>
    <summary>Paper</summary>
    Sauria, Michael EG, and James Taylor. "QuASAR: Quality Assessment of Spatial Arrangement Reproducibility in Hi-C Data"  https://doi.org/10.1101/204438 BioRxiv, November 14, 2017.
</details>

## AB compartments

- [Calder](https://github.com/CSOgroup/CALDER) - multi-scale compartment and sub-compartment detection, improvement over dichotomous AB compartment detection. Clustering contact similarities (Fisher's z-transformed correlations) into high intra and low inter-region similarities, followed by a divisive hierarchical clustering within each domain. The likelihood of nested sub-domains can be estimated using a mixture log-normal distribution. Detailed methods, complex. Eight subcompartments, 4 within the A and 4 within the B compartment, balanced set, in contrast to SNIPER. Expected associations with active/inactive genomic annotations. Nested compartments may be associated with TADs/loops. Analysis of domain repositioning across 114 cell lines. 40kb resolution. R package, named after [Alexander Calder](https://en.wikipedia.org/wiki/Alexander_Calder), an American sculptor. [Supplementary](https://www.nature.com/articles/s41467-021-22666-3#Sec23) Data 1 - IDs and links to Hi-C, ChIP-seq, and RNA-seq datasets; Data 2 - hg19 BED files of Complete domain hierarchies inferred by CALDER from 127 Hi-C contact maps; Data 7 - coordinates of Repositioned compartment domains between normal and cancer cell lines derived from breast, prostate, and pancreatic tissue samples. <details>
    <summary>Paper</summary>
    - Liu, Yuanlong, et al. "Systematic Inference and Comparison of Multi-Scale Chromatin Sub-Compartments Connects Spatial Organization to Cell Phenotypes"  https://doi.org/10.1038/s41467-021-22666-3 Nature Communication, 10 May 2021
</details>

- [POSSUM](https://github.com/JRowleyLab/POSSUM) - A/B compartment detection method in super-resolution Hi-C matrices. PCA of Sparse SUper Massive Matrices, Calculating eigenvectors for sparse matrices using power method (Figure 1, Methods). New GM12878 data at 500kb resolution (42 billion read pairs, 33 billion contacts). Genes can span compartments, but gene promoters almost exclusively (95%) are located in A compartments. Distinguishing loops formed by extrusion and non-extrusion mechanisms (SIP, HiCCUPS, Fit-Hi-C for detection), high resolution of Hi-C data is important. Applied to other datasets, organisms. A part of the Juicer pipeline [Eigenvector](https://github.com/aidenlab/juicer/wiki/Eigenvector), [C++ POSSUM code](https://github.com/JRowleyLab/POSSUM) on Jordan Rowley's lab GitHub. Other tools: [HiCSampler](https://github.com/jrowleylab/hicsampler), [HiCNoiseMeasurer](https://github.com/JRowleyLab/HiCNoiseMeasurer). [Tweet1](https://twitter.com/dphansti/status/1446126731723558915?s=20) by Doug Phanstiel, [Tweet2](https://twitter.com/MJordanRowley/status/1446127588032716810?s=20) by Jordan Rowley. <details>
    <summary>Paper</summary>
    - Gu, Huiya, Hannah Harris, Moshe Olshansky, Kiana Mohajeri, Yossi Eliaz, Sungjae Kim, Akshay Krishna, et al. "Fine-Mapping of Nuclear Compartments Using Ultra-Deep Hi-C Shows That Active Promoter and Enhancer Elements Localize in the Active A Compartment Even When Adjacent Sequences Do Not"  https://doi.org/10.1101/2021.10.03.462599 Preprint. Genomics, October 3, 2021.
</details>

- [dcHiC](https://github.com/ay-lab/dchic) - differential A/B compartment analysis of Hi-C data. Uses Multiple Factor Analysis (MFA), and extension of PCA which combines Hi-C maps before performing generalized PCA. Analogous to weighted PCA in which every dataset is normalized for its biases (Methods). Multivariate distance measure to estimate statistical significance of compartment differences. Applied to mouse neuronal differentiation, mouse hematopoietic system, human cell Hi-C data. Gene enrichment analysis shows biologically relevant signal. Input - sparse matrix, hic, cool files. <details>
    <summary>Paper</summary>
    Wang, Jeffrey, Abhijit Chakraborty, and Ferhat Ay. "DcHiC: Differential Compartment Analysis of Hi-C Datasets"  https://doi.org/10.1101/2021.02.02.429297 BioRxiv, January 1, 2021
</details>

- [SNIPER](https://github.com/ma-compbio/SNIPER) - 3D subcompartment (A1, A2, B1, B2, B3) identification from low-coverage Hi-C datasets. A neural network based on a denoising autoencoder (9 layers) and a multi-layer perceptron. Sigmoidal activation of inputs, ReLU, softmax on outputs. Dropout, binary cross-entropy. exp(-1/C) transformation of Hi-C matrices. Applied to Gm12878 and 8 additional cell types to compare subcompartment changes. Compared with Rao2014 annotations, outperforms Gaussian HMM and MEGABASE. <details>
    <summary>Paper</summary>
    Xiong, Kyle, and Jian Ma. "Revealing Hi-C Subcompartments by Imputing High-Resolution Inter-Chromosomal Chromatin Interactions"  https://doi.org/10.1038/s41467-019-12954-4 Nature Communications, 07 November 2019
</details>

- [Eigenvector](https://github.com/aidenlab/juicer/wiki/Eigenvector) - Juicer's native tool. The eigenvector can be used to delineate compartments in Hi-C data at coarse resolution; the sign of the eigenvector typically indicates the compartment. The eigenvector is the first principal component of the Pearson's matrix.

## Peak/Loop callers

- [ZipHi-C](https://github.com/igosungithub/HMRFHiC) - a Bayesian framework based on a Hidden Markov Random Field model to detect significant interactions and experimental biases in Hi-C data. Predecessors - HMRFBayesHi-C, FastHiC. Borrows information from neighboring loci. Tested on simulated and experimental data, less false positives than FastHi-C, Juicer, HiCExplorer. Detailed stats methods.<details>
    <summary>Paper</summary>
    Osuntoki, Itunu G., Andrew P. Harrison, Hongsheng Dai, Yanchun Bao, and Nicolae Radu Zabet. "[ZipHiC: a novel Bayesian framework to identify enriched interactions and experimental biases in Hi-C data"  https://doi.org/10.1101/2021.10.19.463680 bioRxiv (October 20, 2021).
</details>

- [HiC-ACT](https://yunliweb.its.unc.edu/hicACT/) - improved chromatin loop detection considering spatial dependency (especially at high 5-10kb resolution). Aggregated Cauchy Test (ACT) based approach accounting for possible correlations between adjacent loci pairs from high-resolution Hi-C data. Combine a set of p-values, T statistics following Cauchy distribution under arbitrary dependence structure. Need the local smoothing bandwidth size. Post-processing of results from loop callers that assume independence among loci. Input - bin-pair identifiers and the corresponding p-values. Tested on GM12878 and mESC data. The improvement in power is most pronounced in low-depth (downsampled) data. Fast, implemented in R. [GitHub](https://github.com/tmlagler/hicACT). <details>
    <summary>Paper</summary>
    Lagler, Taylor M., Armen Abnousi, Ming Hu, Yuchen Yang, and Yun Li. "HiC-ACT: Improved Detection of Chromatin Interactions from Hi-C Data via Aggregated Cauchy Test"  https://doi.org/10.1016/j.ajhg.2021.01.009 The American Journal of Human Genetics, (February 2021)
</details>

- [Chromosight](https://github.com/koszullab/chromosight) - loop and pattern detection, computer vision-based (borders, FIREs, hairpins, and centromeres) in Hi-C maps. Takes in a single, whole-genome contact map, text-based bedGraph2d, and binary cool formats, ICE-normalizes. Sliding window, pattern detection using Pearson correlation with the template, then series of filters. Output - text-based. Outperforms HiCexplorer, HICCUPS, HOMER, cooltools, in the order of decreasing F1. Tested on synthetic Hi-C data mimicking S. cerevisiae genome, [benchmark data at Zenodo](https://zenodo.org/record/3742095), [Python3 code](https://github.com/koszullab/chromosight) <details>
    <summary>Paper</summary>
    Matthey-Doret, Cyril, Lyam Baudry, Axel Breuer, Rémi Montagne, Nadège Guiglielmoni, Vittore Scolari, Etienne Jean, et al. "Computer Vision for Pattern Detection in Chromosome Contact Maps"  https://doi.org/10.1038/s41467-020-19562-7 Nature Communications, (December 2020)
</details>

- [FIREcaller](https://yunliweb.its.unc.edu/FIREcaller/download.php) - an R package to call frequently interacting regions from Hi-C data, as well as clustered super-FIREs. Normalization using HiCNormCis to regress out systematic biases. Converts normalized cis-interactions into Z-scores, calculates one-sided p-values and classifies bins as FIRE/nonFIRE. Also outputs continuous FIREscore (-ln(p-value)). FIREs are tissue-specific, can distinguish samples. Associated with H3K27ac and H3K4me3 signal. <details>
    <summary>Paper</summary>
    Crowley, Cheynna, Yuchen Yang, Yunjiang Qiu, Benxia Hu, Jakub Lipi, Hyejung Won, Bing Ren, Ming Hu, and Yun Li. "FIREcaller: Detecting Frequently Interacting Regions from Hi-C Data"  https://doi.org/10.1101/619288 October 26, 2020, 11.
</details>

- [Mustache](https://github.com/ay-lab/mustache) - loop detection from Hi-C and Micro-C maps. Scale-space theory, detection of blob-shaped objects in a multi-scale representation of contact maps, Gaussian kernels with increasing scales. Differences of adjacent Gaussians guide the search for local maxima. Series of filtering steps to minimize false positives. Corrected for multiple testing p-values of blobs. Applied to Gm12878 and K562 Hi-C data, and HFFc6 cell line Micro-C data, 5kb resolution. Compared with HiCCUPS, SIP comparison added, detects similar and more loops flanked by convergent CTCF, RAD21, SMC3, loops confirmed by ChIA-PET and HiChIP data. Python3 tool, Conda/Docker wrapped, handles .hic/.cool files. https://github.com/ay-lab/mustache, [Tweet](https://twitter.com/ferhatay/status/1232716714346872832?s=20). <details>
    <summary>Paper</summary>
    Ardakany, Abbas Roayaei. "Mustache: Multi-Scale Detection of Chromatin Loops from Hi-C and Micro-C Maps Using Scale-Space Representation"  https://doi.org/10.1186/s13059-020-02167-0 Genome Biology, February 24, 2020
</details>

- [NeoLoopFinder](https://github.com/XiaoTaoWang/NeoLoopFinder) - detecting chromatin interactions induced by all kinds of structural variants (SVs). Input - a Hi-C contact matrix and a list of SV breakpoints. Output - genome-wide CNV profile, CNV segments, local assembly around SVs (graph-based algorithm), corrected Hi-C matrix for newly assembled regions and normalized for CNV effect and allelic effect, chromatin loops in rearranged regions (Peakachu), enhancer-hijacking events (needs H3K27ac data). CNVs are detected by HMM-based segmentation module. Includes visualization module. Neo-loop detection in 50 cancer Hi-C datasets from cell lines and patient samples (17 cancer types). Cancer-specific neoloops, associated genes, epigenomic enrichments. Methods - DI + HMM. [Video, 20m](https://youtu.be/J61hFn5lB14). <details>
    <summary>Paper</summary>
    Wang, Xiaotao, Jie Xu, Baozhen Zhang, Ye Hou, Fan Song, Huijue Lyu, and Feng Yue. "Genome-Wide Detection of Enhancer-Hijacking Events from Chromatin Interaction Data in Rearranged Genomes"  https://doi.org/10.1038/s41592-021-01164-w Nature Methods, (June 2021)
</details>

- [Peakachu](https://github.com/tariks/peakachu) - loop prediction from Hi-C data using random forest on loop-specific pixel intensities within 11x11 window. ChIA-PET and HiChIP provide positive training examples. H3K27ac HiChIP better predicts short-range interactions, CTCF ChIA-PET is better for longer interactions. 10Kb resolution data, Gm12878 and K562 cell line. Excels for short-range interactions. Detects more loops than Fit-Hi-C, HiCCUPS, with good overlap. FDR estimated on auxin-treated vs. untreated HCT-116 cells, about 0.2%. Model trained using data from Hi-C performs well in other technologies, Micro-C, DNA SPRITE. Robust to sequencing depth. MCC to select best model. 3-fold cross-validation. Balanced training, same number of negative examples (with short and long distances between interacting loci). [Predicted loops for 56 cell/tissue types](http://promoter.bx.psu.edu/hi-c/publications.html). <details>
    <summary>Paper</summary>
    Salameh, Tarik J., Xiaotao Wang, Fan Song, Bo Zhang, Sage M. Wright, Chachrit Khunsriraksakul, Yijun Ruan, and Feng Yue. "A Supervised Learning Framework for Chromatin Loop Detection in Genome-Wide Contact Maps"  https://doi.org/10.1038/s41467-020-17239-9 Nature Communications, (December 2020)
</details>

- [SIP](https://github.com/PouletAxel/SIP) - loop caller using image analysis. Regional maxima-based, peaks called in a sliding window. Distance-normalized Hi-C matrices, image adjusted using Gaussian blur, contrast enhancement, White Top-Hat correction, identified peaks then filtered by peak enrichment, empirical FDR, loop decay. Comparison with HiCCUPS and cLoops callers. Robust to noise, sequencing depth, much faster, good agreement, improved detection rate. SIPMeta - average metaplots of loops on bias-corrected images for better representation. Java implementation, works with .hic and .cool files. <details>
    <summary>Paper</summary>
    Rowley, M. Jordan, Axel Poulet, Michael H. Nichols, Brianna J. Bixler, Adrian L. Sanborn, Elizabeth A. Brouhard, Karen Hermetz, et al. "Analysis of Hi-C Data Using SIP Effectively Identifies Loops in Organisms from C. Elegans to Mammals"  https://doi.org/10.1101/gr.257832.119 Genome Research 30, no. 3 (March 2020)
</details>

- [StripeCaller](https://github.com/XiaoTaoWang/StripeCaller) - A toolkit for analyzing architectural stripes. Architectural stripes, created by extensive loading of cohesin near CTCF anchors, with Nipbl and Rad21 help. Little overlap between B cells and ESCs. Architectural stripes are sites for tumor-inducing TOP2beta DNA breaks. ATP is required for loop extrusion, cohesin translocation, but not required for maintenance, Replication of transcription is not important for loop extrusion. Zebra algorithm for detecting architectural stripes, image analysis, math in Methods. Human lymphoblastoid cells, mouse ESCs, mouse B-cells activated with LPS, CH12 B lymphoma cells, wild-type, treated with hydroxyurea (blocks DNA replication), flavopiridol (blocks transcription, PolII elongation), oligomycin (blocks ATP). Hi-C, ChIA-pet, ChIP-seq, ATAC-seq, and more [Data1](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE82144), [Data2](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE98119). <details>
    <summary>Paper</summary>
    Vian, Laura, Aleksandra Pękowska, Suhas S.P. Rao, Kyong-Rim Kieffer-Kwon, Seolkyoung Jung, Laura Baranello, Su-Chen Huang, et al. "The Energetics and Physiological Impact of Cohesin Extrusion"  https://doi.org/10.1016/j.cell.2018.03.072 Cell 173, no. 5 (May 2018)
</details>

- [coolpup.py](https://github.com/Phlya/coolpuppy) - Pile-up (aggregation, averaging) analysis of Hi-C data (.cool format) for visualizing and identifying chromatin loops from several sparse datasets, e.g., single-cell. Visualization using plotpup.py script. [Scripts for the paper](https://github.com/Phlya/coolpuppy_paper/tree/master/Nagano). <details>
    <summary>Paper</summary>
    Flyamer, Ilya M., Robert S. Illingworth, and Wendy A. Bickmore. "Coolpup.Py - a Versatile Tool to Perform Pile-up Analysis of Hi-C Data"  https://doi.org/10.1101/586537 BioRxiv, January 1, 2019
</details>

- [cLoops2](https://github.com/YaqiangCao/cLoops2) - improved pipeline for analysing Hi-TrAC/TrAC data. Peak/loop calling, differentially enriched loops, annotation, resolution estimation, similarity, aggregation/visualization. Improved blockDBSCAN clustering algorithm. Outperforms MACS2, SICER, HOMER, SEACR. <details>
    <summary>Paper</summary>
    Cao, Yaqiang, Shuai Liu, Gang Ren, Qingsong Tang, and Keji Zhao. "CLoops2: A Full-Stack Comprehensive Analytical Tool for Chromatin Interactions"  https://doi.org/10.1101/2021.07.20.453068 BioRxiv, 2021.
</details>

- [cLoops](https://github.com/YaqiangCao/cLoops) - DBSCAN-based algorithm for the detection of chromatin loops in ChIA-PET, Hi-C, HiChIP, Trac-looping data. Local permutation-based estimation of statistical significance, several tests for enrichment over the background. Outperforms diffHiC, Fit-Hi-C, GOTHiC, HiCCUPS, HOMER. <details>
    <summary>Paper</summary>
    Cao, Yaqiang, Xingwei Chen, Daosheng Ai, Zhaoxiong Chen, Guoyu Chen, Joseph McDermott, Yi Huang, and Jing-Dong J. Han. "Accurate Loop Calling for 3D Genomic Data with CLoops"  https://doi.org/10.1101/465849 November 8, 2018. 
</details>

- [FastHiC](https://yunliweb.its.unc.edu/fasthic/) - hidden Markov random field (HMRF)-based peak caller, fast and well-performing. <details>
    <summary>Paper</summary>
    Xu, Zheng, Guosheng Zhang, Cong Wu, Yun Li, and Ming Hu. "FastHiC: A Fast and Accurate Algorithm to Detect Long-Range Chromosomal Interactions from Hi-C Data"  https://doi.org/10.1093/bioinformatics/btw240 Bioinformatics (Oxford, England) 32, no. 17 (01 2016)
</details>

- [FitHiC](https://noble.gs.washington.edu/proj/fit-hi-c/) - Python tool for detection of significant chromatin interactions. <details>
    <summary>Paper</summary>
    Ay, Ferhat, Timothy L. Bailey, and William Stafford Noble. "Statistical Confidence Estimation for Hi-C Data Reveals Regulatory Chromatin Contacts"  https://doi.org/10.1101/gr.160374.113 Genome Research 24, no. 6 (June 2014) - Fit-Hi-C method, Splines to model distance dependence. Model mid-range interaction frequencies, decay with distance. Biases, normalization methods. Two-step splines - use all dots for the first fit, identify and remove outliers, second fit without outliers. Markers of boundaries - insulators, heterochromatin, pluripotent factors. CNVs are enriched in chromatin boundaries. Replication timing data how-to http://www.replicationdomain.com/. Validation Hi-C data. http://chromosome.sdsc.edu/mouse/hi-c/download.html
</details>

- [FitHiC2](https://github.com/ay-lab/fithic) - protocol to install/run FitHiC Python3 tool/scripts. Fit of non-increasing cubic splines to distance-interaction frequency decay to identify significant interactions in individual matrices. Accounts for biases derived from KR (ICE, or other) normalization (HiCKRy). Works with fixed-bin- or restriction cut site resolution data. Overview of FitHiC algorithm, accounting for biases. Flexible input options, from HiC-Pro, Juicer, and other tools, validPairs file format. Post-processing to prioritize highly significant interactions supported by the nearby loci, and filter noisy detections. HTML report, flexible BED-derived output format, conversion to formats for WashU epigenome and UCSC browsers. Installable using conda, pip, GitHub. Comparable methods - HiCCUPS, HOMER, GOTHiC, HiC-DC, a brief description of each. Tested on three datasets. [GitHub](https://github.com/ay-lab/fithic), Executable on [Code Ocean](https://codeocean.com/capsule/4528858/tree/v3), [Data](https://zenodo.org/record/3380589). <details>
    <summary>Paper</summary>
    Kaul, Arya, Sourya Bhattacharyya, and Ferhat Ay. "Identifying Statistically Significant Chromatin Contacts from Hi-C Data with FitHiC2"  https://doi.org/10.1038/s41596-019-0273-0 Nature Protocols, January 24, 2020.
</details>

- [FitHiChIP](https://github.com/ay-lab/FitHiChIP) - significant peak caller in HiChIP and PLAC-seq data. Accounts for assay-specific biases, as well as for the distance effect. 3D differential loops detection. Methods. <details>
    <summary>Paper</summary>
    Bhattacharyya, Sourya, Vivek Chandra, Pandurangan Vijayanand, and Ferhat Ay. "FitHiChIP: Identification of Significant Chromatin Contacts from HiChIP Data"  https://doi.org/10.1101/412833 September 10, 2018. 
</details>

- [GoTHIC](https://www.bioconductor.org/packages/release/bioc/html/GOTHiC.html) - R package for peak calling in individual HiC datasets, while accounting for noise. <details>
    <summary>Paper</summary>
    Mifsud, Borbala, Inigo Martincorena, Elodie Darbo, Robert Sugar, Stefan Schoenfelder, Peter Fraser, and Nicholas M. Luscombe. "GOTHiC, a Probabilistic Model to Resolve Complex Biases and to Identify Real Interactions in Hi-C Data"  https://doi.org/10.1371/journal.pone.0174744 Edited by Mark Isalan. PLOS ONE 12, no. 4 (April 5, 2017) - The GOTHiC (genome organization through HiC) algorithm uses a simple binomial distribution model to simultaneously remove coverage-associated biases in Hi-C data and detect significant interactions by assuming that the global background interaction frequency of two loci. Use of the Benjamini–Hochberg multiple-testing correction to control for the false discovery rate. 
</details>

- [HiC-DC](https://bitbucket.org/leslielab/hic-dc/src/master/) - significant interaction detection using the zero-inflated negative binomial model and accounting for biases like GC content, mappability. Compared with Fit-Hi-C, more conservative. Robust to sequencing depth. Detects significant, biologically relevant interactions at all length scales, including sub-TADs. BWA-MEM alignment (Python script), then processing in R. <details>
    <summary>Paper</summary>
    Carty, Mark, Lee Zamparo, Merve Sahin, Alvaro González, Raphael Pelossof, Olivier Elemento, and Christina S. Leslie. "An Integrated Model for Detecting Significant Chromatin Interactions from High-Resolution Hi-C Data"  https://doi.org/10.1038/ncomms15454 Nature Communications 8, no. 1 (August 2017)
</details>

- [HiCExplorer's hicDetectLoops](https://hicexplorer.readthedocs.io/en/latest/content/tools/hicDetectLoops.html#hicdetectloops) for loop detection. Review and critique of HiCCUPS, HOMER, GOTHIC, cLoops, FastHiC. Distance-dependent of chromatin interactions with a continuous negative binomial distribution, detection of the interaction counts with p-values smaller than a threshold, then filtering. [GitHub](https://github.com/deeptools/HiCExplorer/). <details>
    <summary>Paper</summary>
    Wolff, Joachim, Rolf Backofen, and Björn Grüning. "Loop Detection Using Hi-C Data with HiCExplorer"  https://doi.org/10.1101/2020.03.05.979096 Preprint. Bioinformatics, March 6, 2020
</details>

- [HMRFBayesHiC](https://yunliweb.its.unc.edu/HMRFBayesHiC/) - a hidden Markov random field-based Bayesian peak caller to identify long-range chromatin interactions from Hi-C data. Borrowing information from neighboring loci. Previous peak calling methods, Fit-Hi-C. Interactions between enhancers and promoters as a benchmark. <details>
    <summary>Paper</summary>
    Xu, Zheng, Guosheng Zhang, Fulai Jin, Mengjie Chen, Terrence S. Furey, Patrick F. Sullivan, Zhaohui Qin, Ming Hu, and Yun Li. "A Hidden Markov Random Field-Based Bayesian Method for the Detection of Long-Range Chromosomal Interactions in Hi-C Data"  https://doi.org/10.1093/bioinformatics/btv650 Bioinformatics (Oxford, England) 32, no. 5 (01 2016)
</details>

- [LASCA](https://github.com/ArtemLuzhin/LASCA_pipeline) - loop/significant contact caller that uses Weibull distribution-based modeling to each diagonal. DBSCAN to cluster adjacent significant pixels. Works with Hi-C data from any species, tested on human, C. Elegans, S. Cerevisiae. Filters according Aggregate Peak Analysis patterns may be used to refine calls. Compared with HiCCUPS, MUSTACHE, demonstrates good overlap. Also identifies non-CTCF-driven loops. Input - .cool files. [Python code](https://github.com/ArtemLuzhin/LASCA_pipeline). <details>
    <summary>Paper</summary>
    Luzhin, Artem V., Arkadiy K. Golov, Alexey A. Gavrilov, Artem K. Velichko, Sergey V. Ulianov, Sergey V. Razin, and Omar L. Kantidze. "LASCA: Loop and Significant Contact Annotation Pipeline"  https://doi.org/10.1038/s41598-021-85970-4 Scientific Reports, (December 2021)
</details>

- [HiCPeaks](https://github.com/XiaoTaoWang/HiCPeaks) - Python CPU-based implementation for BH-FDR and HICCUPS, two peak calling algorithms for Hi-C data, proposed by Rao et al. 2014. Text-to-cooler Hi-C data converter, two scripts to call peaks, and one for visualization (creation of a .png file). [Pypi repo](https://pypi.org/project/hicpeaks/)

- [HOMER](http://homer.ucsd.edu/homer/interactions/) - Perl scripts for normalization, visualization, significant interaction detection, motif discovery. Does not correct for bias.

## Differential interactions

- [NE-MVNMF](https://github.com/Roy-lab/mvnmf) - combines network enhancement (network denoising) and multitask non-negative matrix factorization for comparing multiple Hi-C matrices and idenrtifying dynamic (changing) regions. MVNMF - joint decomposition to find a common underlying structure in multiple matrices, clustering regions, comparing cluster assignments, identifying stretches of 5 or more regions switching clusters (dynamic regions). Applied to rat mammary epithelial cells, two time points (within and outside the window of susceptibility (WOS) to breast cancer, week 6 and 12). Arima Genomics, triplicates (6 samples total), merged into two, 10kb, HiC-Pro processing, ICE normalization, differential point interactions as intersection of Selfish and Fit-Hi-C. Integrated with gene expression (RNA-seq) and published breast cancer SNPs. [GEO GSE184285](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE184285). <details>
    <summary>Paper</summary>
    Baur, Brittany, Da-Inn Lee, Jill Haag, Deborah Chasman, Michael Gould, and Sushmita Roy. “Deciphering the Role of 3D Genome Organization in Breast Cancer Susceptibility.” Frontiers in Genetics 12 (January 11, 2022): 788318. https://doi.org/10.3389/fgene.2021.788318.
</details>

- [HICDCPlus](https://bioconductor.org/packages/HiCDCPlus/) - an R/Bioconductor package for Hi-C/Hi-ChIP interaction calling (directly from raw data, negative binomial regression accounting for genomic distance,GC content, mappability, restriction enzyme-based bin size) and differential analysis (DESeq2). Includes TAD (TopDom) and A/B compartment callers. Input - HiC-Pro or Juicer. Output compatible with visualization in Juicebox and HiCExplorer. Compared with diffHiC, multiHiCcompare, Selfish, provides better results. Normalization by ChIP-seq input may not be helpful. [BitBucket](https://bitbucket.org/leslielab/hicdcplus/src/master/). <details>
    <summary>Paper</summary>
    Sahin, Merve, Wilfred Wong, Yingqian Zhan, Kinsey Van Deynze, Richard Koche, and Christina S. Leslie. "[HiC-DC+ enables systematic 3D interaction calls and differential analysis for Hi-C and HiChIP"  https://doi.org/10.1038/s41467-021-23749-x Nature communications, 07 June 2021
</details>

- [BART3D](https://github.com/zanglab/bart3d) - transcriptional regulators associated with differential chromatin interactions from Hi-C data. Input: HiC-Pro matrices, .hic Juicer files, .cool files. Output - ranked lists of transcriptional regulators. Distance-based normalization to average of individual matrices. Difference detection by a paired t-test of normalized interactions within 200kb (Figure 1A). Differential interactions are mapped to the union of DNAseI hypersensitive sites, then standard [BART](http://bartweb.uvasomrc.io/) algorithm. Python implementation. <details>
    <summary>Paper</summary>
    Wang, Zhenjia, Yifan Zhang, and Chongzhi Zang. "BART3D: Inferring Transcriptional Regulators Associated with Differential Chromatin InteracTions from Hi-C Data"  https://doi.org/10.1093/bioinformatics/btab173 Bioinformatics, 15 March 2021
</details>

- [CHESS](https://github.com/vaquerizaslab/CHESS) (Comparison of Hi-C Experimentss using Structural Similarity) - comparative analysis of Hi-C matrices and automatic feature extraction (TADs, loops, stripes). Image analysis-based structural similarity index (SSIM, combines brightness, contrast, and structure differences, S = 1 - identical matrices, <1 - differences) to assign similarity score and an associated p-value (from empirical distribution of SSIMs, two types of bacground model, Methods) to pairs of genomic regions. Obs/exp transformation, differential matrix, denoise, smooth, binarize, feature extraction using close morphology filter, k-means clustering, classification. Works with low sequencing depth, high noise data. Outperforms diffHiC, HOMER, and ACCOST. Applied to interspecies comparison of syntenic regions (Synteny portal), WT and Zelda-depleted Drosophila, C-cell lymphoma, Capture-C analysis. Input - Juicer, Cooler, of FAN-C format, plus .bedpe for regions to compare (chess pairs to generate). Python, scikit-image module. [Documentation](https://chess-hic.readthedocs.io/en/latest/index.html). <details>
    <summary>Paper</summary>
    Galan, Silvia, Nick Machnik, Kai Kruse, Noelia Díaz, Marc A. Marti-Renom, and Juan M. Vaquerizas. "CHESS Enables Quantitative Comparison of Chromatin Contact Data and Automatic Feature Extraction"  https://doi.org/10.1038/s41588-020-00712-y Nature Genetics, October 19, 2020
</details>

- [DiffGR](https://github.com/wmalab/DiffGR) - differentially interacting genomic regions. Stratum-adjusted correlation coefficient (SCC) (HiCrep-inspired) to measure similarity of local TAD regions. Focus on within-TAD interactions. Simulated data at various levels of sparsity, noise, HiCseg for TAD calling. 2D mean filter for smoothing, KR normalization. Permutation test to estimate the significance of SCC changes. FDR depends on the proportion of altered TADs. R implementation. <details>
    <summary>Paper</summary>
    Liu, Huiling, and Wenxiu Ma. "DiffGR: Detecting Differentially Interacting Genomic Regions from Hi-C Contact Maps"  https://doi.org/10.1101/2020.08.29.273698 bioRxiv, August 31, 2020
</details>

- [Serpentine](https://github.com/koszullab/serpentine) - differential analysis of two Hi-C maps using the 2D serpentine-binning method. Serpentine is a subset of connected pixels defined by thresholds in control and experimental contact maps. Serpentines are then compared using the Mean-Deviation plot. Help to alleviate the effect of sparsity. Uses HiCcompare functionality. Normalization does not help. Python package, currently processes full 1500x1500 matrices. <details>
    <summary>Paper</summary>
    Baudry, Lyam, Gaël A Millot, Agnes Thierry, Romain Koszul, and Vittore F Scolari. "Serpentine: A Flexible 2D Binning Method for Differential Hi-C Analysis"  https://doi.org/10.1093/bioinformatics/btaa249 Edited by Alfonso Valencia. Bioinformatics 36, no. 12 (June 1, 2020)
</details>

- [ACCOST](https://bitbucket.org/noblelab/accost/src/master/) (Altered Chromatin COnformation STatirstics) - distance-aware differential Hi-C analysis. Extends the statistical model of DEseq by using the size factors to model the genomic distance effect. The use of the MD plot. Compared with diffHiC, FIND, and HiCcompare. Evaluated on human, mouse, plasmodium Hi-C data. <details>
    <summary>Paper</summary>
    - Cook, Kate B., Borislav H. Hristov, Karine G. Le Roch, Jean Philippe Vert, and William Stafford Noble. "[Measuring significant changes in chromatin conformation with ACCOST"  https://doi.org/10.1093/nar/gkaa069 Nucleic acids research, (18 March 2020) 
</details>

- [multiHiCcompare](https://bioconductor.org/packages/multiHiCcompare/) - R/Bioconductor package for joint normalization of multiple Hi-C datasets using cyclic loess regression through pairs of MD plots (minus-distance). Data-driven normalization accounting for the between-dataset biases. Per-distance edgeR-based testing of significant interactions. <details>
    <summary>Paper</summary>
    Stansfield, John C, Kellen G Cresswell, and Mikhail G Dozmorov. "MultiHiCcompare: Joint Normalization and Comparative Analysis of Complex Hi-C Experiments"  https://doi.org/10.1093/bioinformatics/btz048 Bioinformatics, January 22, 2019
</details>

- [Chicdiff](https://github.com/RegulatoryGenomicsGroup/chicdiff) - differential interaction detection in Capture Hi-C data. Signal normalization based on the CHiCAGO framework, differential testing using DESeq2. Accounting for distance effect by the Independent Hypothesis Testing (IHW) method to learn p-value weights based on the distance to maximize the number of rejected null hypotheses. <details>
    <summary>Paper</summary>
    Cairns, Jonathan, William R. Orchard, Valeriya Malysheva, and Mikhail Spivakov. "Chicdiff: A Computational Pipeline for Detecting Differential Chromosomal Interactions in Capture Hi-C Data"  https://doi.org/10.1101/526269 BioRxiv, January 1, 2019
</details>

- [Selfish](https://github.com/ucrbioinfo/Selfish) - comparative analysis of replicate Hi-C experiments via a self-similarity measure - local similarity borrowed from image comparison. Check reproducibility, detect differential interactions. Boolean representation of contact matrices for reproducibility quantification. Deconvoluting local interactions with a Gaussian filter (putting a Gaussian bell around a pixel), then comparing derivatives between contact maps for each radius. Simulated (Zhou method) and real comparison with FIND - better performance, especially on low fold-changes. Stronger enrichment of relevant epigenomic features. Matlab implementation. <details>
    <summary>Paper</summary>
    Roayaei Ardakany, Abbas, Ferhat Ay, and Stefano Lonardi. "Selfish: Discovery of Differential Chromatin Interactions via a Self-Similarity Measure"  https://doi.org/10.1093/bioinformatics/btz362 Bioinformatics, July 2019
</details>

- [HiCcompare](https://bioconductor.org/packages/HiCcompare/) - R/Bioconductor package for joint normalization of two Hi-C datasets using loess regression through an MD plot (minus-distance). Data-driven normalization accounting for the between-dataset biases. Per-distance permutation testing of significant interactions. <details>
    <summary>Paper</summary>
    Stansfield, John C., Kellen G. Cresswell, Vladimir I. Vladimirov, and Mikhail G. Dozmorov. "HiCcompare: An R-Package for Joint Normalization and Comparison of HI-C Datasets"  https://doi.org/10.1186/s12859-018-2288-x BMC Bioinformatics 19, no. 1 (December 2018)
</details>

- [diffloop](https://bioconductor.org/packages/diffloop/) - Differential analysis of chromatin loops (ChIA-PET). edgeR framework. <details>
    <summary>Paper</summary>
    Lareau, Caleb A., and Martin J. Aryee. "Diffloop: A Computational Framework for Identifying and Analyzing Differential DNA Loops from Sequencing Data"  https://doi.org/10.1093/bioinformatics/btx623 Bioinformatics (Oxford, England), September 29, 2017. 
</details>

- [FIND](https://bitbucket.org/nadhir/find/downloads/) - differential chromatin interaction detection comparing the local spatial dependency between interacting loci. Previous strategies - simple fold-change comparisons, binomial model (HOMER), count-based (edgeR). FIND exploits a spatial Poisson process model to detect differential chromatin interactions that show a significant change in their interaction frequency and the interaction frequency of their adjacent bins. "Variogram" concept. For each point, compare densities between conditions using Fisher's test. Explored various multiple correction testing methods, used r^th ordered p-values (rOP) method. Benchmarking against edgeR in simulated settings - FIND outperforms at shorter distances, edgeR has more false positives at longer distances. Real Hi-C data normalized using KR and MA normalizations. R package. <details>
    <summary>Paper</summary>
    Mohamed Nadhir, Djekidel, Yang Chen, and Michael Q. Zhang. “FIND: DifFerential Chromatin INteractions Detection Using a Spatial Poisson Process.” Genome Research, February 12, 2018. https://doi.org/10.1101/gr.212241.116.
</details>

- [AP](https://github.com/XiaoTaoWang/TADLib) - aggregation preference - parameter, to quantify TAD heterogeneity. Call significant interactions within a TAD, cluster with DBSCAN, calculate weighted interaction density within each cluster, average. AP measures are reproducible. Comparison of TADs in Gm12878 and IMR90 - stable TADs change their aggregation preference, these changes correlate with LINEs, Lamin B1 signal. Can detect structural changes (block split) in TADs. <details>
    <summary>Paper</summary>
    Wang, X.-T., Dong, P.-F., Zhang, H.-Y., and Peng, C. (2015). "[Structural heterogeneity and functional diversity of topologically associating domains in mammalian genomes.](https://academic.oup.com/nar/article/43/15/7237/2414371)" Nucleic Acids Research
</details>

- [diffHiC](https://bioconductor.org/packages/diffHic/) - Differential contacts using the full pipeline for Hi-C data. Explanation of the technology, binning. MA normalization, edgeR-based. Comparison with HOMER. <details>
    <summary>Paper</summary>
    Lun, Aaron T. L., and Gordon K. Smyth. "DiffHic: A Bioconductor Package to Detect Differential Genomic Interactions in Hi-C Data"  https://doi.org/10.1186/s12859-015-0683-0 BMC Bioinformatics 16 (2015)
</details>

## TAD callers

- [HiCKey](https://github.com/YingruWuGit/HiCKey) - hierarchical TAD caller, comparison of TADs across samples. A generalized likelihood-ratio (GRL) test for detecting change-points in an interaction matrix that follows negative binomial distribution (Methods). Bottom-up approach to detect hierarchy. Tested on Forcato simulated data with nested TADs, TPR/FPR/difference/Fowlkes-Mallows index to estimate performance. Applied to seven cell lines. TAD hierarchy is up to four levels. Compared with TADtree, 3DNetMod, IC-Finder, HiCSeg. Colocalization within a 2-bin distance. Input - normalized, distance effect removed matrix in sparse text format, output - TAD start coordinate, hierarchy level, p-value of the changepoint. C++ implementation. Did not compare with SpectralTAD hierarchical caller.<details>
    <summary>Paper</summary>
    Xing, Haipeng. "Deciphering Hierarchical Organization of Topologically Associated Domains through Change-Point Testing"  https://doi.org/10.1186/s12859-021-04113-8 BMC Bioinformatics, April 10, 2021
</details>

- [GRiNCH](https://roy-lab.github.io/grinch/) - TAD detection algorithm using Graph Regularized Nonnegative matrix factorization. Graph captures distance dependence. Also smoothes/imputes Hi-C matrices. Compared with Directionality Score, Insulation Index, rGMAP, Armatus, HiCseg, TopDom using several metrics - Davies-Bouldin index, Delta Contact Counts, Rand Index, Mutual Information. GRiNCH detects consistent similarly-sized TADs, robust to different resolutions, boundaries show robust enrichment in known markers of TAD boundaries (TFBSs and histone), detects consistent Fit-Hi-C significant interactions (area under precision-recall curve). Applied to mouse neural development and pluripotency reprogramming to confirm known and discover new boundary regulators. Applied to SPRITE and HiChIP data. [Project](https://roy-lab.github.io/grinch/), [GitHub](https://github.com/Roy-lab/grinch), and [Visualization tutorial](https://github.com/Roy-lab/grinch/tree/master/visualization)<details>
    <summary>Paper</summary>
    Lee, Da-Inn, and Sushmita Roy. "Graph-Regularized Matrix Factorization for Reliable Detection of Topological Units from High-Throughput Chromosome Conformation Capture Datasets"  https://doi.org/10.1186/s13059-021-02378-z Genome Biology, 25 May 2021
</details>

- [BHi-Cect](https://github.com/princeps091-binf/BHi-Cect) - identification of the full hierarchy of chromosomal interactions (TADs). Spectral clustering starting from the whole chromosome, detecting nested BHi-Cect Partition Trees (BPTs), partitioned in non-contiguous and interwoven enclaves, inspired by fractal globule idea. Variation of information to test the agreement between two clustering results, overlap-based metrics to test correspondence with TADs. Correspondence analysis of enclaves association with TF content. Gene enrichment. Different enclaves show different epigenomic and gene expression signatures, bottom enclaves are most crisply defined. Resolution affects what enclave size can be detected. <details>
    <summary>Paper</summary>
    Kumar, Vipin, Simon Leclerc, and Yuichi Taniguchi. "BHi-Cect: A Top-down Algorithm for Identifying the Multi-Scale Hierarchical Structure of Chromosomes"  https://doi.org/10.1093/nar/gkaa004 Nucleic Acids Research 48, no. 5 (March 18, 2020)
</details>

- [TADBD](https://github.com/bioinfo-lab/TADBD/) TAD caller using a multi-scale Haar diagonal template (sum of on-diagonal squares minus the sum of off-diagonal squares). Compared with HiCDB, IC-Finder, EAST (also using Haar features), TopDom, HiCseg using simulated (Forcato) and experimental (K562 and IMR90). ICE-normalized data. MCC, Jaccard. R package. <details>
    <summary>Paper</summary>
    Lyu, Hongqiang, Lin Li, Zhifang Wu, Tian Wang, Jiguang Zheng, and Hongda Wang. "TADBD: A Sensitive and Fast Method for Detection of Typologically Associated Domain Boundaries"  https://doi.org/10.2144/btn-2019-0165 BioTechniques, April 7, 2020
</details>

- [TADpole](https://github.com/3DGenomes/TADpole) - hierarchical TAD boundary caller. Preprocessing by filtering sparse rows, transforming the matrix into its Pearson correlation coefficient matrix, running PCA on it and retaining 200 PCs, transforming into a Euclidean distance matrix, clustering using the Constrained Incremental Sums of Squares clustering (rioja::chclust(, coniss)), estimating significance, Calinski-Harabasz index to estimate the optimal number of clusters (chromatin subdivisions). Benchmarking using Zufferey 2018 datasets, mouse limb bud development with genomic inversions from Kraft 2019. Resolution, normalization, sequencing depth. Metrics: the Overlap Score, the Measure of Concordance, all from Zufferey 2018. Enrichment in epigenomic marks. DiffT metric for differential analysis (on binarized TAD/non-TAD matrices). Compared with 22 TAD callers, including hierarchical (CaTCH, GMAP, Matryoshka, PSYCHIC). <details>
    <summary>Paper</summary>
    Soler-Vila, Paula, Pol Cuscó Pons, Irene Farabella, Marco Di Stefano, and Marc A. Marti-Renom. "Hierarchical Chromatin Organization Detected by TADpole"  https://doi.org/10.1101/698720 Preprint. Bioinformatics, July 11, 2019. 
</details>

- [HiCDB](https://github.com/ChenFengling/RHiCDB) - TAD boundary detection using local relative insulation (LRI) metric, improved stability, less parameter tuning, cross-resolution, differential boundary detection, lower computations, visualization. Review of previous methods, directionality index, insulation score. Math of LRI. GSEA-like enrichment in genome annotations (CTCF). Differential boundary detection using the intersection of extended boundaries. Compared with Armatus, DI, HiCseg, IC-finder, Insulation, TopDom on 40kb datasets. Accurately detects smaller-scale boundaries. Differential TADs are enriched in cell-type-specific genes. <details>
    <summary>Paper</summary>
    Chen, Fengling, Guipeng Li, Michael Q. Zhang, and Yang Chen. "HiCDB: A Sensitive and Robust Method for Detecting Contact Domain Boundaries"  https://doi.org/10.1093/nar/gky789 Nucleic Acids Research 46, no. 21 (November 30, 2018)
</details>

- [OnTAD](https://github.com/anlin00007/OnTAD) - hierarchical TAD caller, Optimal Nested TAD caller. Sliding window, adaptive local minimum search algorithm, similar to TOPDOM. C++ implementation. [OnTAD for coolers](https://github.com/cchlanger/cooler_ontad) - a Python wrapper to work with `.cool` files. <details>
    <summary>Paper</summary>
    An, Lin, Tao Yang, Jiahao Yang, Johannes Nuebler, Qunhua Li, and Yu Zhang. "Hierarchical Domain Structure Reveals the Divergence of Activity among TADs and Boundaries"  https://doi.org/10.1101/361147 July 3, 2018. - Intro about TADs, Dixon's directionality index, Insulation score. Other hierarchical callers - TADtree, rGMAP, Arrowhead, 3D-Net, IC-Finder. Limitations of current callers - ad hoc thresholds, sensitivity to sequencing depth and mapping resolution, long running time and large memory usage, insufficient performance evaluation. Boundaries are asymmetric - some have more contacts with other boundaries, support for asymmetric loop extrusion model. Performance comparison with DomainCaller, rGMAP, Arrowhead, TADtree. Stronger enrichment of CTCF and two cohesin proteins RAD21 and SMC3. TAD-adjR^2 metric quantifying the proportion of variance in the contact frequencies explained by TAD boundaries. Reproducibility of TAD boundaries - Jaccard index, tested at different sequencing depths and resolutions. Boundaries of hierarchical TADs are more active - more CTCF, epigenomic features, TFBSs expressed genes. Super-boundaries - shared by 5 or more TADs, highly active. Rao-Huntley 2014 Gm12878 data. Distance correction - subtracting the mean counts at each distance.
</details>

- [3D-NetMod](https://bitbucket.org/creminslab/3dnetmod_method_v1.0_10_06_17) - hierarchical, nested, partially overlapping TAD detection using graph theory. Community detection method based on the maximization of network modularity, Louvain-like locally greedy algorithm, repeated several (20) times to avoid local maxima, then getting consensus. Tuning parameters are estimated over a sequence search. Benchmarked against TADtree, directionality index, Arrowhead. ICE-normalized data brain data from Geschwind (human data) and Jiang (mouse data) studies. Computationally intensive. Python implementation. <details>
    <summary>Paper</summary>
    Norton, Heidi K., Daniel J. Emerson, Harvey Huang, Jesi Kim, Katelyn R. Titus, Shi Gu, Danielle S. Bassett, and Jennifer E. Phillips-Cremins. “Detecting Hierarchical Genome Folding with Network Modularity.” Nature Methods 15, no. 2 (February 2018): 119–22. https://doi.org/10.1038/nmeth.4560.
</details>

- [deDoc](https://github.com/yinxc/structural-information-minimisation) - TAD detection minimizing structural entropy of the Hi-C graph (structural information theory). Detects optimal resolution (= minimal entropy). Pooled 10 single-cell Hi-C analysis. Intro about TADs, a brief description of TAD callers, including hierarchical. Works best on raw, non-normalized data, highly robust to sparsity (0.1% of the original data sufficient). Compared with five TAD callers (Armatus, TADtree, Arrowhead, MrTADFinder, Domaincall (DI)), and a classical graph modularity detection algorithm. Enrichment in CTCF, housekeeping genes, H3K4me3, H4K20me1, H3K36me3. Other benchmarks - weighted similarity, number, length of TADs. Detects hierarchy over different passes. Java implementation (won't run on Mac). <details>
    <summary>Paper</summary>
    Li, Angsheng, Xianchen Yin, Bingxiang Xu, Danyang Wang, Jimin Han, Yi Wei, Yun Deng, Ying Xiong, and Zhihua Zhang. “Decoding Topologically Associating Domains with Ultra-Low Resolution Hi-C Data by Graph Structural Entropy.” Nature Communications 9, no. 1 (15 2018): 3265. https://doi.org/10.1038/s41467-018-05691-7.
</details>

- [CaTCH](https://github.com/zhanyinx/CaTCH_R) - identification of hierarchical TAD structure. Reciprocal insulation (RI) index. Benchmarked against Dixon's TADs (diTADs). CTCF enrichment as a benchmark, enrichment of TADs in differentially expressed genes. <details>
    <summary>Paper</summary>
    Zhan, Yinxiu, Luca Mariani, Iros Barozzi, Edda G. Schulz, Nils Blüthgen, Michael Stadler, Guido Tiana, and Luca Giorgetti. "Reciprocal Insulation Analysis of Hi-C Data Shows That TADs Represent a Functionally but Not Structurally Privileged Scale in the Hierarchical Folding of Chromosomes"  https://doi.org/10.1101/gr.212803.116 Genome Research 27, no. 3 (2017)
</details>

- [HiTAD](https://github.com/XiaoTaoWang/TADLib) - hierarchical TAD identification, different resolutions, correlation with chromosomal compartments, replication timing, gene expression. Adaptive directionality index approach. Data sources, methods for comparing TAD boundaries, reproducibility. H3K4me3 enriched and H3K4me1 depleted at boundaries. TAD boundaries (but not sub-TADs) separate replication timing, A/B compartments, gene expression. <details>
    <summary>Paper</summary>
    Wang, Xiao-Tao, Wang Cui, and Cheng Peng. "HiTAD: Detecting the Structural and Functional Hierarchies of Topologically Associating Domains from Chromatin Interactions"  https://doi.org/10.1093/nar/gkx735 Nucleic Acids Research 45, no. 19 (November 2, 2017)
</details>

- [IC-Finder](http://membres-timc.imag.fr/Daniel.Jost/DJ-TIMC/Software.html) - Segmentations of HiC maps into hierarchical interaction compartments. <details>
    <summary>Paper</summary>
    - Noelle Haddad, Cedric Vaillant, Daniel Jost. "IC-Finder: inferring robustly the hierarchical organization of chromatin folding" https://doi.org/10.1093/nar/gkx036 
</details>

- [ClusterTAD](https://github.com/BDM-Lab/ClusterTAD) - A clustering method for identifying topologically associated domains (TADs) from Hi-C data. <details>
    <summary>Paper</summary>
    Oluwadare, Oluwatosin, and Jianlin Cheng. "ClusterTAD: An Unsupervised Machine Learning Approach to Detecting Topologically Associated Domains of Chromosomes from Hi-C Data" https://doi.org/10.1186/s12859-017-1931-2 BMC Bioinformatics 18, no. 1 (November 14, 2017)
</details>

- [EAST](https://github.com/ucrbioinfo/EAST) - Efficient and Accurate Detection of Topologically Associating Domains from Contact Maps, Haar-like features (rectangles on images) and a function that quantifies TAD properties: frequency within is high, outside - low, boundaries must be strong. Objective - finding a set of contiguous non-overlapping domains maximizing the function. Restricted by the maximum length of TADs. Boundaries are enriched in CTCF, RNP PolII, H3K4me3, H3K27ac. <details>
    <summary>Paper</summary>
    Abbas Roayaei Ardakany, Stefano Lonardi, and Marc Herbstritt, "Efficient and Accurate Detection of Topologically Associating Domains from Contact Maps"  https://doi.org/10.4230/LIPIcs.WABI.2017.22 (Schloss Dagstuhl - Leibniz-Zentrum fuer Informatik GmbH, Wadern/Saarbruecken, Germany, 2017)
</details>

- [TADtree](http://compbio.cs.brown.edu/software/) - Hierarchical (nested) TAD identification. Two ways of TAD definition: 1D and 2D. Normalization by distance. Enrichment over the background. <details>
    <summary>Paper</summary>
    Weinreb, Caleb, and Benjamin J. Raphael. "Identification of Hierarchical Chromatin Domains"  https://doi.org/10.1093/bioinformatics/btv485 Bioinformatics (Oxford, England) 32, no. 11 (June 1, 2016)
</details>

- [TopDom](http://zhoulab.usc.edu/TopDom/) - An efficient and Deterministic Method for identifying Topological Domains in Genomes, Method is based on the general observation that within-TAD interactions are stronger than between-TAD. binSignal value as the average of nearby contact frequency, fitting a curve, finding local minima, test them for significance. Fast, takes linear time. Detects similar domains to HiCseq and Dixon's directionality index. Found expected enrichment in CTCF, histone marks. Housekeeping genes and overall gene density are close to TAD boundaries, differentially expressed genes are not. <details>
    <summary>Paper</summary>
    Shin, Hanjun, Yi Shi, Chao Dai, Harianto Tjong, Ke Gong, Frank Alber, and Xianghong Jasmine Zhou. "TopDom: An Efficient and Deterministic Method for Identifying Topological Domains in Genomes"  https://doi.org/10.1093/nar/gkv1505 Nucleic Acids Research 44, no. 7 (April 20, 2016)
</details>

- [TADtool](https://github.com/vaquerizaslab/tadtool) - wrapper for directionality index and insulation score TAD callers. <details>
    <summary>Paper</summary>
    Kruse, Kai, Clemens B. Hug, Benjamín Hernández-Rodríguez, and Juan M. Vaquerizas. "TADtool: Visual Parameter Identification for TAD-Calling Algorithms"  https://doi.org/10.1093/bioinformatics/btw368 Bioinformatics (Oxford, England) 32, no. 20 (15 2016)
</details>

- [Arboretum-Hi-C](https://bitbucket.org/roygroup/arboretum-hic) - a multitask spectral clustering method to identify differences in genomic architecture. Intro about the 3D genome organization, TAD differences, and conservation. Assessment of different clustering approaches using different distance measures, as well as raw contacts. Judging clustering quality by enrichment in genomic regulatory signals (Histone marks, LADs, early vs. late replication timing, TFs like POLII, TAF, TBP, CTCF, P300, CMYC, cohesin components, LADs, replication timing, SINE, LINE, LTR) and by numerical methods (Davies-Bouldin index, silhouette score, others). Although spectral clustering on contact counts performed best, spectral + Spearman correlation was chosen. Comparing cell types identifies biologically relevant differences as quantified by enrichment. Peak counts or average signal within regions were used for enrichment. [Data](https://zenodo.org/record/49767). <details>
    <summary>Paper</summary>
    Fotuhi Siahpirani, Alireza, Ferhat Ay, and Sushmita Roy. "A Multi-Task Graph-Clustering Approach for Chromosome Conformation Capture Data Sets Identifies Conserved Modules of Chromosomal Interactions"  https://doi.org/10.1186/s13059-016-0962-8 Genome Biology 17, no. 1 (December 2016). 
</details>

- [Armatus](https://github.com/kingsfordgroup/armatus) - TAD detection at different resolutions, Dynamic programming method. <details>
    <summary>Paper</summary>
    Filippova, Darya, Rob Patro, Geet Duggal, and Carl Kingsford. "Identification of Alternative Topological Domains in Chromatin" Algorithms for Molecular Biology 9, no. 1 (2014) https://doi.org/10.1186/1748-7188-9-14
</details>

- [HiCseg](https://cran.r-project.org/web/packages/HiCseg/index.html) - TAD detection by maximization of likelihood based block-wise segmentation model. 2D segmentation rephrased as 1D segmentation - not contours, but borders. Statistical framework, solved with dynamic programming. Dixon data as gold standard. [Hausdorff distance](https://en.wikipedia.org/wiki/Hausdorff_distance) to compare segmentation quality. Parameters (from TopDom paper): nb_change_max = 500, distrib = 'G' and model = 'Dplus'. <details>
    <summary>Paper</summary>
    Lévy-Leduc, Celine, M. Delattre, T. Mary-Huard, and S. Robin. "Two-Dimensional Segmentation for Analyzing Hi-C Data"  https://doi.org/10.1093/bioinformatics/btu443 Bioinformatics (Oxford, England) 30, no. 17 (September 1, 2014)
</details>

- [domaincaller](https://github.com/XiaoTaoWang/domaincaller) - A Python implementation of the original DI domain caller.

### Architectural stripes

- [Stripenn](https://github.com/vahedilab/stripenn) - a computer vision-based method for architectural stripes detection using Canny edge detection.Scores stripes by median p-value and stripiness based on the continuity of interaction signal. Input - .cool files, optionally normalized. Output - coordinates and scores of the predicted stripes. Applicable to Hi-C, HiChIP, Micro-C data. Introduction to the biology of architectural stripes, review of previous methods (Zebra from Vian et al. 2018, domainClassifyR, CHESS for comparing 3D domains and stripes). Analysis of stripes from B and T lymphocytes identifies stripe anchors enriched in the transcriptionally active compartments, architectural proteins mediating loop extrusion. Strips are strongly conserved, correspond to TAD boundaries, subtle changes are associated with transcriptional output. Python, three functions (compute, score seeimage). [Video 16m](https://www.youtube.com/watch?v=_TEomDYv2vk). <details>
    <summary>Paper</summary>
    Yoon, Sora, and Golnaz Vahedi. "Stripenn Detects Architectural Stripes from Chromatin Conformation Data Using Computer Vision"  https://doi.org/10.1101/2021.04.16.440239 Preprint. Bioinformatics, April 18, 2021
</details>

### Differential/timecourse TAD analysis

- [TADcompare](https://bioconductor.org/packages/TADCompare/) - R package for differential and time-course TAD boundary analysis. Uses [SpectralTAD](https://bioconductor.org/packages/SpectralTAD/) score - spectral decomposition of Hi-C matrices - to statistically detect five types of differential TAD boundaries: merge, split, complex, shifted, strength change. In the time-course analysis, detects six types of boundary score changes: highly common, early appearing, late appearing, early disappearing, late disappearing, and dynamic TAD boundaries. Returns genomic coordinated and types of TAD boundary changes in BED format. <details>
    <summary>Paper</summary>
    Cresswell, Kellen G., and Mikhail G. Dozmorov. "TADCompare: An R Package for Differential and Temporal Analysis of Topologically Associated Domains"  https://doi.org/10.3389/fgene.2020.00158 Frontiers in Genetics 11 (March 10, 2020)
</details>

- [InterTADs](https://github.com/nikopech/InterTADs) - TAD-centric integration of multi-omics (SNPs, gene expression, methylation) data by genomic coordinateы, proper data scaling, and differential analysis. Differential TAD analysis by interaction strength changes, the number of other differential events. [R scripts](https://github.com/nikopech/InterTADs), [Wiki](https://github.com/nikopech/InterTADs/wiki/Usage). <details>
    <summary>Paper</summary>
    - Tsagiopoulou, Maria, Nikolaos Pechlivanis, and Fotis Psomopoulos. "InterTADs: Integration of Multi-Omics Data on Topological Associated Domains"  https://doi.org/10.21203/rs.3.rs-54194/v1 Preprint. In Review, August 12, 2020
</details>

- [BPscore](https://github.com/rz6/bp-metric) metric to compare two TAD segmentations. Formula, methods. More stable to Variation of Information (VI) and Jaccard Index (JI). Python implementation for calculating all three metrics. <details>
    <summary>Paper</summary>
    Zaborowski, Rafał, and Bartek Wilczyński. "BPscore: An Effective Metric for Meaningful Comparisons of Structural Chromosome Segmentations"  https://doi.org/10.1089/cmb.2018.0162 Journal of Computational Biology 26, no. 4 (April 2019)
</details>

- Sauerwald, Natalie, Akshat Singhal, and Carl Kingsford. "Analysis of the Structural Variability of Topologically Associated Domains as Revealed by Hi-C"  https://doi.org/10.1093/nargab/lqz008 NAR Genomics and Bioinformatics, 30 September 2019 - TAD variability among 137 Hi-C samples (including replicates, 69 if not) from 9 studies. HiCrep, Jaccard, TADsim to measure similarity. Variability does not come from genetics. Introduction to TADs. 10-70% of TAD boundaries differ between replicates. 20-80% differ between biological conditions. Much less variation across individuals than across tissue types. Lab -specific source of variation - in situ vs. dilution ligation protocols, restriction enzymes not much. HiCpro to 100kb data, ICE-normalization, Armatus for TAD calling. Table 1 - all studies and accession numbers.

- Sauerwald, Natalie, and Carl Kingsford. "Quantifying the Similarity of Topological Domains across Normal and Cancer Human Cell Types"  https://doi.org/10.1093/bioinformatics/bty265 Bioinformatics (Oxford, England), (July 1, 2018) - Analysis of TAD similarity using variation of information (VI) metric as a local distance measure. Defining structurally similar and variable regions. Comparison with previous studies of genomic similarity. Cancer-normal comparison - regions containing pan-cancer genes are structurally conserved in normal-normal pairs, not in cancer-cancer. [Kingsford-Group/localtadsim](https://github.com/Kingsford-Group/localtadsim). 23 human Hi-C datasets, Hi-C Pro processed into 100kb matrices, Armatus to call TADs. 

- [DiffTAD](https://bitbucket.org/rzaborowski/differential-analysis) - differential contact frequency in TADs between two conditions. Two - permutation-based comparing observed vs. expected median interactions, and parametric test considering the sign of the differences within TADs. Both tests account for distance stratum. <details>
    <summary>Paper</summary>
    Zaborowski, Rafal, and Bartek Wilczynski. "DiffTAD: Detecting Differential Contact Frequency in Topologically Associating Domains Hi-C Experiments between Conditions"  https://doi.org/10.1101/093625 BioRxiv, January 1, 2016
</details>

## Prediction of 3D features

- [DL2021_HI-C](https://github.com/koritsky/DL2021_HI-C) - deep-learning approach for increasing Hi-C data resolution by appending additional information about genome sequence. Two algorithms: the image-to-image model (modified after [VEHiCLE](https://github.com/Max-Highsmith/VEHiCLE)), which enhances Hi-C resolution by itself, and the sequence-to-image model (modified after [Akita](https://github.com/calico/basenji/tree/master/manuscripts/akita)), which uses additional information about the underlying genome sequence for further resolution improvement. Both models are combined with the simple head model (Figure 4). Details of network architecture, training, testing, validation (5 metrics). Various architecture modifications. VEHiCLE by itself performs well. <details>
    <summary>Paper</summary>
    Kriukov, Dmitrii, Mark Zaretckii, Igor Kozlovskii, Mikhail Zybin, Nikita Koritskiy, Mariia Bazarevich, and Ekaterina Khrameeva. "Hi-C Resolution Enhancement with Genome Sequence Data"  https://doi.org/10.1101/2021.10.25.465745 Preprint. Systems Biology, October 26, 2021. 
</details>

- [L-HiC-Reg](https://github.com/Roy-lab/Roadmap_RegulatoryVariation) (Local HiC-Reg) - a Random Forests based regression method to predict high-resolution contact counts in new cell lines, and a network-based framework to identify candidate cell line-specific gene networks targeted by a set of variants from a Genome-wide association study (GWAS). Trained on chromosome-specific 1Mb segments in one cell line to predict in another. 55 cell lines, 10 annotations (CTCF, RAD21, TBP, histone marks, DNAse), imputing missing annotations with Avocado. Outperforms GeneHancer and JEME, Networks for 15 GWASs in all cell lines are [available](https://pages.discovery.wisc.edu/~bbaur/Roadmap_RegulatoryVariation/) <details>
    <summary>Paper</summary>
    - Baur, Brittany, Jacob Schreiber, Junha Shin, Shilu Zhang, Yi Zhang, Jun S Song, William Stafford Noble, and Sushmita Roy. "Leveraging Epigenomes and Three-Dimensional Genome Organization for Interpreting Regulatory Variation"  https://doi.org/10.1101/2021.08.29.458098 biorXiv, August 30, 2021
</details>

- [CCIP](https://github.com/GaoLabXDU/CCIP) (CTCF-mediated Chromatin Interaction Prediction) - predicting CTCF-mediated convergent and tandem loops with transitivity. Transitivity definition from the network of multiple CTCF-interacting regions, convergent and tandem. Incorporating the GCP (graph connecting probability) score, together with CTCF, RAD21, directional CTCF motif one-hot encoding into random forest. GCP is the most important predictive feature. Compared with Lollipop and CTCF-MP. <details>
    <summary>Paper</summary>
    Wang, Weibing, Lin Gao, Yusen Ye, and Yong Gao. "CCIP: Predicting CTCF-Mediated Chromatin Loops with Transitivity"  https://doi.org/10.1093/bioinformatics/btab534 Bioinformatics, 20 July 2021.
</details>

- [ChINN](https://github.com/caofan/chinn) - chromatin interaction neural network, predicting chromatin interactions from DNA sequence. Trained on CTCF- and RNA PolII-mediated loops, as well as on Hi-C data. Gradient boosting trained on functional annotation, distance, or both as predictors. ChINN - CNN trained on sequence. Convergent CTCF orientation is an important predictor, other motifs complement predictive power. Applied to 6 new chronic lymphocytic leukemia samples, patient-specific interactions, vaildated by Hi-C and 4C. <details>
    <summary>Paper</summary>
    Cao, Fan, Yu Zhang, Yichao Cai, Sambhavi Animesh, Ying Zhang, Semih Can Akincilar, Yan Ping Loh, et al. "Chromatin Interaction Neural Network (ChINN): A Machine Learning-Based Method for Predicting Chromatin Interactions from DNA Sequences"  https://doi.org/10.1186/s13059-021-02453-5 Genome Biology, (December 2021)
</details>

- [compartmap](https://bioconductor.org/packages/compartmap/) - A/B compartment reconstruction from bulk and scRNA-seq/scATAC-seq. Steps: preprocessing and summarizing the single-cell assay data; eBayes shrinkage of summarized features towards a global or local target; computing the shrinkage correlation estimate of summarized features; computing domains via SVD (Methods). Also detects genomic rearrangements. Applied to K562 data. [Bioconductor](https://bioconductor.org/packages/compartmap/), [GitHub](https://github.com/biobenkj/compartmap), [Tweet](https://twitter.com/biobenkj/status/1395014386545201152?s=20). <details>
    <summary>Paper</summary>
    Johnson, Benjamin K, Jean-Philippe Fortin, Kasper D Hansen, Hui Shen, and Triche Jr. "Compartmap Enables Inference of Higher-Order Chromatin Structure in Individual Cells from ScRNA-Seq and ScATAC-Seq"  https://doi.org/10.1101/2021.05.17.444465 preprint, May 18, 2021
</details>

- [SCI](https://github.com/TheJacksonLaboratory/sci) - A/B sub-compartment prediction from Hi-C data, graph embedding (adaptation of LINE method, better than HOPE and DeepWalk) and k-means clustering. Five subcompartments, informed by eipgenetic modifications. Compared with compartments predicted by HMM (Rao 2014) and k-means clustering by Yaffe-Tanay 2011. Improved network centrality, clustering metrics, enrichment in relevant epigenomic marks, higher intra-loop vs. inter-loop ratio, coordinated gene expression, TF enrichment. XGBoost/RF (allowing feature selection), neural network to predict subcompartments from epigenomics, methylation, sequence-based data, replication timing. Predictions confirmed by ChIA-PET data. GM12878 and K562 data. Python implementation. [sci-DNN](https://github.com/TheJacksonLaboratory/sci-DNN), [News](https://www.jax.org/news-and-insights/2020/march/unfold-the-3d-genome). <details>
    <summary>Paper</summary>
    Ashoor, Haitham, Xiaowen Chen, Wojciech Rosikiewicz, Jiahui Wang, Albert Cheng, Ping Wang, Yijun Ruan, and Sheng Li. “Graph Embedding and Unsupervised Learning Predict Genomic Sub-Compartments from HiC Chromatin Interaction Data.” Nature Communications 11, no. 1 (December 2020): 1173. https://doi.org/10.1038/s41467-020-14974-x.
</details>

- [Hi-ChIP-ML](https://github.com/MichalRozenwald/Hi-ChIP-ML) - machine learning models for TAD boundary prediction using epigenomic data (ChIP-seq, Histone-seq signal, 5 and 18 feature sets) in Drosophila. Linear regression with 4 regularization types, gradient boosting, bidirectional (to capture both sides around a boundary) LSTM. Methods describe data construction, loss function, model architectures, machine learning framework. One feature at a time to measure feature importance. Chriz factor is the top predictor, then H3K4me1, H3K27me1. Python, sklearn, keras. [Colab notebook](https://colab.research.google.com/drive/1_VEcL2qaMAmd0XyGWriXnii16Lqrsd3c?usp=sharing). <details>
    <summary>Paper</summary>
    Rozenwald, Michal B, Aleksandra A Galitsyna, Grigory V Sapunov, Ekaterina E Khrameeva, and Mikhail S Gelfand. "A Machine Learning Framework for the Prediction of Chromatin Folding in Drosophila Using Epigenetic Features"  https://doi.org/10.7717/peerj-cs.307 PeerJ Comput Sci. 2020 Nov 30
</details>

- [3DPredictor](https://github.com/labdevgen/3DPredictor) - Prediction of enhnancer-promoter interactions from gene expression, CTCF binding and orientation, distance between interacting loci. Also predict changes in 3D genome organization - genomic rearrangements. Benchmarking of TargetFinder, its performance is overestimated. Class balance slightly improves performance. Two random chromosomes for validation, the rest - for training (10-90% split). Gradient boosting for prediction, significantly better than Random Forest. Multiple performance metrics. Model trained in one cell type can predict in another. Predict quantitative level of interactions. Other tools - EP2Vec, CTCF-MP, HiC-Reg. [GitHub](https://github.com/labdevgen/3DPredictor), [Web tool](https://genedev.bionet.nsc.ru/Web_3DPredictor/). <details>
    <summary>Paper</summary>
    Belokopytova, Polina S., Miroslav A. Nuriddinov, Evgeniy A. Mozheiko, Daniil Fishman, and Veniamin Fishman. "Quantitative prediction of enhancer–promoter interactions." Genome research 30, no. 1 (2020): 72-84. https://doi.org/10.1101/gr.249367.119
</details>

- [Akita](https://github.com/calico/basenji/tree/tf2_hic/manuscripts/akita) - Chromatin interaction prediction from sequence only using CNN. Takes in 1Mb sequence and predicts interactions at 2Kb resolution. Includes Distance between interacting regions included. Allows for understanding the effect of mutations. Tested on Rao Hi-C datasets, Micro-C data. [Basenji](https://github.com/calico/basenji/tree/tf2_hic/,) network architecture. 80/10/10 training, validation, test sets. <details>
    <summary>Paper</summary>
    Fudenberg, Geoff, David R Kelley, and Katherine S Pollard. "Predicting 3D Genome Folding from DNA Sequence"  https://doi.org/10.1038/s41592-020-0958-x Nature Methods, 12 October 2020
</details>

- [3D-GNOME 2.0](https://3dgnome.cent.uw.edu.pl/) - modeling 3D structure changes due to structural variants (SVs). Reference data - GM12878 ChIA-PET data (CTCF, RNAPII). Changes are modeled by removing or adding contacts between chromatin interaction anchors depending on SV (deletion, duplication, insertion, inversion). [Web tool](https://3dgnome.cent.uw.edu.pl/), [Bitbucket](https://bitbucket.org/4dnucleome/spatial_chromatin_architecture/). <details>
    <summary>Paper</summary>
    Wlasnowolski, Michal, Michal Sadowski, Tymon Czarnota, Karolina Jodkowska, Przemyslaw Szalaj, Zhonghui Tang, Yijun Ruan, and Dariusz Plewczynski. "3D-GNOME 2.0: A Three-Dimensional Genome Modeling Engine for Predicting Structural Variation-Driven Alterations of Chromatin Spatial Structure in the Human Genome"  https://doi.org/10.1093/nar/gkaa388 Nucleic Acids Research, (July 2, 2020)
</details>

- [HiC-Reg](https://github.com/Roy-lab/HiC-Reg) - Predicting Hi-C contact counts from one-dimensional regulatory signals (Histone marks, CTCF, RAD21, Tbp, DNAse). Random Forest regression. Feature encoding - distance between two regions, pair-concat, window, multi-cell. Works across chromosomes (some chromosomes are worse than others) and cell lines (Gm12878, K562, Huvec, Hmec, Nhek, can be used to predict interactions on new cell lines). Selection of the most important features using multi-task group LASSO (distance, CTCF, Tbp, H4K20me1, DNAse, others). Predicted contacts correspond well to the original contacts (distance-stratified Pearson correlation), define TADs similar to the originals (Jaccard), define significant contacts (Fit-Hi-C) more enriched in CTCF binding. Validated on HBA1 and PAPPA gene promoters. Hi-C normalization doesn't have much effect. <details>
    <summary>Paper</summary>
    Zhang, Shilu, Deborah Chasman, Sara Knaack, and Sushmita Roy. "In Silico Prediction of High-Resolution Hi-C Interaction Matrices"  https://doi.org/10.1038/s41467-019-13423-8 Nature Communications 10, no. 1 (December 2019)
</details>

- [TADBoundaryDectector](https://github.com/lincshunter/TADBoundaryDectector) - TAD boundary prediction from sequence only using deep learning models. 12 architectures tested, with three convolutional and an LSTM layer performed best. Methods, Implementation in Keras-TensorFlow. Model evaluation using different criteria, 96% accuracy reported. Deep learning outperforms feature-based models, among which Boosted Trees, Random Forest, elastic net logistic regression are the best performers. Data augmentation (aka feature engineering) by randomly shifting TAD boundary regions by som base pairs of length (0-100). Tested on Drosophila data. <details>
    <summary>Paper</summary>
    Henderson, John, Vi Ly, Shawn Olichwier, Pranik Chainani, Yu Liu, and Benjamin Soibam. "Accurate Prediction of Boundaries of High Resolution Topologically Associated Domains (TADs) in Fruit Flies Using Deep Learning"  https://doi.org/10.1093/nar/gkz315 Nucleic Acids Research, May 3, 2019. 
</details>

- [3DEpiLoop](https://bitbucket.org/4dnucleome/3depiloop) - prediction of 3D interactions from 1D epigenomic profiles using Random Forest trained on CTCF peaks (histone modifications are the most important predictors and TFBSs). <details>
    <summary>Paper</summary>
    Al Bkhetan, Ziad, and Dariusz Plewczynski. "Three-Dimensional Epigenome Statistical Model: Genome-Wide Chromatin Looping Prediction"  https://doi.org/10.1038/s41598-018-23276-8 Scientific Reports 8, no. 1 (December 2018). 
</details>

- `PRISMR` - a polymer-based method (strings and binders switch SBS polymer model) to model 3D chromatin folding, to predict enhancer-promoter contacts, and to model the effect of structural variations (deletions, duplications, inversions) on the 3D genome organization. Input - Hi-C data. Infers minimal factors that shape chromatin folding and its equilibrium under the laws of physics, without prior assumptions or tunable parameters. Simulated annealing Monte Carlo optimization procedure that minimizes the distance between the predicted polymer model and the input contact matrix under a Bayesian weighting factor to avoid overfitting. Tested on a EPHA4 locus associated with limb malformations, and more. [Newly generated capture Hi-C of mouse limb buds at embryonic day 11.5, and human skin fibroblasts, GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE92294). Public murine CH12-LX cells and human IMR90 cells. Implementation - the [LAMMPS package](https://lammps.sandia.gov/), code not available. <details>
    <summary>Paper</summary>
    Bianco, Simona, Darío G. Lupiáñez, Andrea M. Chiariello, Carlo Annunziatella, Katerina Kraft, Robert Schöpflin, Lars Wittler, et al. "Polymer Physics Predicts the Effects of Structural Variants on Chromatin Architecture"  https://doi.org/10.1038/s41588-018-0098-8 Nature Genetics, (May 2018)
</details>

- Predicting TAD boundaries using training data and making new predictions. Bayesian network (BNFinder method), random forest vs. basic k-means clustering, ChromHMM, cdBEST. Using sequence k-mers and ChIP-seq data from modENCODE for prediction - CTCF ChIP-seq performs best. Used Boruta package for feature selection. The Bayesian network performs best. <details>
    <summary>Paper</summary>
    Bednarz, Paweł, and Bartek Wilczyński. "Supervised Learning Method for Predicting Chromatin Boundary Associated Insulator Elements](http://www.worldscientific.com/doi/pdf/10.1142/S0219720014420062 Journal of Bioinformatics and Computational Biology 12, no. 06 (December 2014)
</details>

## SNP-oriented

- [iRegNet3D](http://iregnet3d.yulab.org/index/) - Integrated Regulatory Network 3D (iRegNet3D) is a high-resolution regulatory network comprised of interfaces of all known transcription factor (TF)-TF, TF-DNA interaction interfaces, as well as chromatin-chromatin interactions and topologically associating domain (TAD) information from different cell lines. Goal: SNP interpretation. Input: One or several SNPs, rsIDs, or genomic coordinates. Output: For one or two SNPs, on-screen information of their disease-related info, connection over TF-TF and chromatin interaction networks, and whether they interact in 3D and located within TADs. For multiple SNPs, the same info downloadable as text files. <details>
    <summary>Paper</summary>
    - Liang, Siqi, Nathaniel D. Tippens, Yaoda Zhou, Matthew Mort, Peter D. Stenson, David N. Cooper, and Haiyuan Yu. "IRegNet3D: Three-Dimensional Integrated Regulatory Network for the Genomic Analysis of Coding and Non-Coding Disease Mutations"  https://doi.org/10.1186/s13059-016-1138-2 Genome Biology 18, no. 1 (December 2017)
</details>

- [3DSNP](http://cbportal.org/3dsnp/) -  3DSNP database integrating SNP epigenomic annotations with chromatin loops. Linear closest gene, 3D interacting gene, eQTL, 3D interacting SNP, chromatin states, TFBSs, conservation. For individual SNPs. <details>
    <summary>Paper</summary>
    - Lu, Yiming, Cheng Quan, Hebing Chen, Xiaochen Bo, and Chenggang Zhang. "3DSNP: A Database for Linking Human Noncoding SNPs to Their Three-Dimensional Interacting Genes"  https://doi.org/10.1093/nar/gkw1022 Nucleic Acids Research 45, no. D1 (January 4, 2017)
</details>

- [HUGIn](http://yunliweb.its.unc.edu/HUGIn/) - tissue-specific Hi-C linear display of anchor position and around. Overlay gene expression and epigenomic data. Association of SNPs with genes based on Hi-C interactions. Tissue-specific. <details>
    <summary>Paper</summary>
    - Martin, Joshua S, Zheng Xu, Alex P Reiner, Karen L Mohlke, Patrick Sullivan, Bing Ren, Ming Hu, and Yun Li. "HUGIn: Hi-C Unifying Genomic Interrogator"  https://doi.org/10.1093/bioinformatics/btx359 Edited by Inanc Birol. Bioinformatics 33, no. 23 (December 1, 2017)
</details>

## CNV and Structural variant detection

- [hicpipe](https://github.com/ChenFengling/HiCpipe) and, alternatively, [HiCnorm](http://www.people.fas.harvard.edu/~junliu/HiCNorm/) normalization preserves CNVs in Hi-C data. From Zhang et al., "Local and Global Chromatin Interactions Are Altered by Large Genomic Deletions Associated with Human Brain Development"  https://doi.org/10.1038/s41467-018-07766-x 

- [hic_breakfinder](https://github.com/dixonlab/hic_breakfinder) - Detection of structural variants (SV) by integrating optical mapping, Hi-C, and WGS. Custom pipeline using LUMPY, Delly, Control-FREEC software. New Hi-C data on 14 cancer cell lines and 21 previously published datasets. Integration of the detected SVs with genomic annotations, including replication timing. Supplementary data with SVs resolved by individual methods and integrative approaches. <details>
    <summary>Paper</summary>
    - Dixon, Jesse R., Jie Xu, Vishnu Dileep, Ye Zhan, Fan Song, Victoria T. Le, Galip Gürkan Yardımcı, et al. "Integrative Detection and Analysis of Structural Variation in Cancer Genomes"  https://doi.org/10.1038/s41588-018-0195-8 Nature Genetics, September 10, 2018.  
</details>

- [HiCnv](https://github.com/ay-lab/HiCnv), [HiTrans](https://github.com/ay-lab/HiCtrans) - CNV, translocation calling from Hi-C data. CNV calling using HMM on per-restriction site quantified data and 1D-normalized accounting for low GC-content (<0.2), mappability (<0.5). Translocation calling on inter-chromosomal matrices, binned. <details>
    <summary>Paper</summary>
    - Chakraborty, Abhijit, and Ferhat Ay. "Identification of Copy Number Variations and Translocations in Cancer Cells from Hi-C Data"  https://doi.org/10.1093/bioinformatics/btx664 Edited by Christina Curtis. Bioinformatics 34, no. 2 (January 15, 2018)
</details>

- [HiNT](https://github.com/parklab/HiNT) - CNV and translocation detection from \~10-20% ambiguous chimeric reads in Hi-C data. Three tools: HiNT-Pre - preprocessing of Hi-C data; HiNT-CNV and HiNT-TL - CNV and translocation detection, respectively (accept HiC-Pro output). Tested on K562 (cancer) and Gm12878 (normal) data. Removal of known biases using a GAM with Poisson function. Outperforms Delly, Meerkat, hic_breakfinder, HiCtrans. Relatively little overlap with CNVs from WGS (BIC-seq2). Gold-standard - FISH data from Dixon et al., “Integrative Detection and Analysis of Structural Variation in Cancer Genomes.” <details>
    <summary>Paper</summary>
    - Wang, Su, Soohyun Lee, Chong Chu, Dhawal Jain, Geoff Nelson, Jennifer M. Walsh, Burak H. Alver, and Peter J. Park. "HiNT: A Computational Method for Detecting Copy Number Variations and Translocations from Hi-C Data"  https://doi.org/10.1101/657080 Preprint. Bioinformatics, June 3, 2019
</details>

- [TAD fusion score](https://github.com/HormozdiariLab/TAD-fusion-score) - quantifying the effect of deletions on Hi-C interactions. Intro about TAD fusion effect on genome structure. TAD fusion score - the expected total number of changes in pairwise genomic interactions as a result of the deletion. TAD fusion events are negatively selected. <details>
    <summary>Paper</summary>
    - Huynh, Linh, and Fereydoun Hormozdiari. "Contribution of Structural Variation to Genome Structure: TAD Fusion Discovery and Ranking"  https://doi.org/10.1101/279356 BioRxiv, March 9, 2018. 
</details>

## Visualization

- [plotgardener](https://github.com/PhanstielLab/plotgardener) - R/Bioconductor package for multi-panel genomic and non-genomic data visualization. 45 functions for plotting and annotating multiple genomic data formats: genome sequences, gene/transcript annotations, chromosome ideograms, signal tracks, GWAS Manhattan plots, genomic ranges (e.g. peaks, reads, contact domains, etc), paired ranges (e.g. paired-end reads, chromatin loops, structural rearrangements, QTLs, etc), and 3D chromatin contact frequencies. Auto-recognizes .bam, .bigWig, .hic formats, converts genomic data into standard R objects (e.g., data.frame, tibble, GInteractions). Includes 29 genomes, more through Bioconductor integration. [Documentation](https://phanstiellab.github.io/plotgardener/), [Tweet 1](https://twitter.com/dphansti/status/1436417383732813829?s=20), [Tweet 2](https://twitter.com/mikelove/status/1437388358754443274?s=20). <details>
    <summary>Paper</summary>
    - Kramer, Nicole E, Eric S Davis, Craig D Wenger, Erika M Deoudes, Sarah M Parker, Michael I Love, and Douglas H Phanstiel. "Plotgardener: Cultivating Precise Multi-Panel Figures in R"  https://doi.org/10.1101/2021.09.08.459338 Preprint. Bioinformatics, September 10, 2021. 
</details>

- [CoolBox](https://github.com/GangCaoLab/CoolBox) - a pyGenomeTracks-based Hi-C data visualization in Jupyter and command line, matplotlib plotting system. Works with .hic and .m/cool input, plus .bed, .pairs etc. [Documentation and examples](https://gangcaolab.github.io/CoolBox/gallery.html). <details>
    <summary>Paper</summary>
    - Xu, Weize, Quan Zhong, Da Lin, Guoliang Li, and Gang Cao. "CoolBox: A Flexible Toolkit for Visual Analysis of Genomics Data"  https://doi.org/10.1101/2021.04.15.439923 Preprint. Bioinformatics, April 16, 2021
</details>

- Hi-C data visualization review. Good introduction into the 3D genome organization, 115 key references. [Table 2. Hi-C visualization tools](https://dev.biologists.org/highwire/markup/1255595/expansion?width=1000&height=500&iframe=true&postprocessors=highwire_tables%2Chighwire_reclass%2Chighwire_figures%2Chighwire_math%2Chighwire_inline_linked_media%2Chighwire_embed). <details>
    <summary>Paper</summary>
    - Ing-Simmons, Elizabeth, and Juan M. Vaquerizas. "Visualising Three-Dimensional Genome Organisation in Two Dimensions"  https://doi.org/10.1242/dev.177162 Development 146, no. 19 (October 1, 2019)
</details>

- [circHiC](https://github.com/TrEE-TIMC/circHiC) - circular representation of Hi-C data, projection into polar coordinates. Linear relationship between the radius of a circle and the corresponding genomic distance. Predominantly for bacterial chromosomes. Python implementation. [Documentation](https://tree-timc.github.io/circhic/). <details>
    <summary>Paper</summary>
    - Junier, Ivan, and Nelle Varoquaux. "CircHiC: Circular Visualization of Hi-C Data and Integration of Genomic Data"  https://doi.org/10.1101/2020.08.13.249110 Preprint. Bioinformatics, August 14, 2020. 
</details>

- [GENOVA](https://github.com/dewitlab/GENOVA) - an R package for the most common Hi-C analyses and visualization. Quality control - cis/trans ratio, checking for translocations; A/B compartments - single and differential compartment signal (H3K4me1 for compartment assignment); TADs - insulation score and directionality index; Genomic annotations - ChIP-seq signal, gene information; Distance decay, and differential analysis; Saddle plot; Aggregate region/peak/TAD/loop analysis, and differential analysis; Aggregated signal (tornado) plots; Intra-inter-TAD interaction differences; PE-SCAn (paired-end Spatial Chromatin Analysis) and C-SCAn enhancer-promoter aggregation. Data for statistical tests can be extracted from the discovery objects. Applied to Hi-C data from Hap1 cells, WT and deltaWAPL (published) and knockdown cohesin-SA1/SA2 conditions (HiC-pro, hg19, HiCCUPS). Input - HiC-pro, Juicer, .cool files. Storage - compressed sparse triangle format and the user-added metadata. All tools return the "discovery object". [GitHub](https://github.com/dewitlab/GENOVA), [Vignette](https://github.com/robinweide/GENOVA/blob/master/vignettes/GENOVA_vignette.pdf). <details>
    <summary>Paper</summary>
    - Weide, Robin H. van der, Teun van den Brand, Judith H.I. Haarhuis, Hans Teunissen, Benjamin D. Rowland, and Elzo de Wit. "Hi-C Analyses with GENOVA: A Case Study with Cohesin Variants"  https://doi.org/10.1101/2021.01.22.427620 Preprint. Genomics, January 24, 2021.
</details>

- [HiCeekR](https://github.com/lucidif/HiCeekR) - Shiny app and GUI for Hi-C data analysis and interpretation. Input - aligned BAM file, with marked duplicates, restriction enzyme cutting sites (HRF5), genome in FASTQ, optionally ChIP-seq BAM, or RNA-seq gene expression (TSV). The workflow includes filtering (PCR artifacts, self-circle, dangling end fragments, using diffHiC) with diagnostic plots, binning interaction matrices in BED (coordinates) and TSV (counts) formats, normalization (ICE, WavSiS, using chromoR), calling A/B compartments (PCA, using HiTC), TADs (directionality index, TopDom, HiCseg), gene expression/epigenomic integration, network analysis and enrichment in GO, KEGG, other databases (using gProfileR). Visualization of zoomable heatmaps, networks (ggplot2, plotly, heatmaply, networkD3). Starts with creating configuration file. Compared with GITAR, HiCPro, HiC-bench, HiCdat, HiCexplorer, not Juicer or HiGlass. Illustrated using Rao2014 Gm12878 data. 32Gb RAM (minimal 16Gb) is sufficient, preprocessing of BAM files (Hi-C or ChIP-seq) is the longest. <details>
    <summary>Paper</summary>
    - Di Filippo, Lucio, Dario Righelli, Miriam Gagliardi, Maria Rosaria Matarazzo, and Claudia Angelini. "HiCeekR: A Novel Shiny App for Hi-C Data Analysis"  https://doi.org/10.3389/fgene.2019.01079 Frontiers in Genetics 10 (November 4, 2019): 1079. 
</details>

- [HiCBricks](https://bioconductor.org/packages/HiCBricks/) - data format and visualization package. hdf5-based data storage format to handle large Hi-C matrices. Visualization of one or two Hi-C matrices, adding annotations. <details>
    <summary>Paper</summary>
    - Pal, Koustav, Ilario Tagliaferri, Carmen M Livi, and Francesco Ferrari. "HiCBricks: Building Blocks for Efficient Handling of Large Hi-C Datasets"  https://doi.org/10.1093/bioinformatics/btz808 Edited by Inanc Birol. Bioinformatics, November 7, 2019
</details>

- [3D Genome Browser](http://promoter.bx.psu.edu/hi-c/) - visualizing existing Hi-C and other chromatin conformation capture data. Alongside with genomic and epigenomic data. Own data can be submitted in BUTLR format. <details>
    <summary>Paper</summary>
    - Wang, Yanli, Fan Song, Bo Zhang, Lijun Zhang, Jie Xu, Da Kuang, Daofeng Li, et al. "The 3D Genome Browser: A Web-Based Browser for Visualizing 3D Genome Organization and Long-Range Chromatin Interactions"  https://doi.org/10.1186/s13059-018-1519-9 Genome Biology 19, no. 1 (December 2018)
</details>

- [DNARchitect](https://github.com/alosdiallo/DNA_Rchitect) - a Shiny App for visualizing genomic data (HiC, mRNA, ChIP, ATAC, etc.) in bed, bedgraph, and bedpe formats. Wraps Sushi R package. [Web-version](http://shiny.immgen.org/DNARchitect/). <details>
    <summary>Paper</summary>
    - Ramirez, R N, K Bedirian, S M Gray, and A Diallo. "DNA Rchitect: An R Based Visualizer for Network Analysis of Chromatin Interaction Data"  https://doi.org/10.1093/bioinformatics/btz608 Edited by John Hancock. Bioinformatics, August 2, 2019
</details>

- [HiGlass](http://higlass.io/) - visualization server for Google maps-style navigation of Hi-C maps. Overlay genes, epigenomic tracks. "Composable linked views" synchronizing exploration of multiple Hi-C datasets linked by location/zoom. [GitHub](https://github.com/higlass/higlass), [documentation](https://docs.higlass.io/), [links and resources](https://higlass.io/about). <details>
    <summary>Paper</summary>
    - Kerpedjiev, Peter, Nezar Abdennur, Fritz Lekschas, Chuck McCallum, Kasper Dinkla, Hendrik Strobelt, Jacob M. Luber, et al. "HiGlass: Web-Based Visual Exploration and Analysis of Genome Interaction Maps"  https://doi.org/10.1186/s13059-018-1486-1 Genome Biology, (December 2018).
</details>

- [HiPiler](http://hipiler.higlass.io/) - exploration and comparison of loops and domains as snippets-heatmaps of data. [GitHub](https://github.com/flekschas/hipiler), [documentation](http://hipiler.higlass.io/docs). <details>
    <summary>Paper</summary>
    - Lekschas, Fritz, Benjamin Bach, Peter Kerpedjiev, Nils Gehlenborg, and Hanspeter Pfister. "HiPiler: Visual Exploration of Large Genome Interaction Matrices with Interactive Small Multiples"  https://doi.org/10.1109/TVCG.2017.2745978 IEEE Transactions on Visualization and Computer Graphics 24, no. 1 (January 2018). TechBlog: [HiPiler simplifies chromatin structure analysis](http://blogs.nature.com/naturejobs/2017/09/11/techblog-hipiler-simplifies-chromatin-structure-analysis/)
</details>

- [HiCPlotter](https://github.com/kcakdemir/HiCPlotter) - Hi-C visualization tool, allows for integrating various data tracks. Python implementation. <details>
    <summary>Paper</summary>
    - Akdemir, Kadir Caner, and Lynda Chin. "HiCPlotter Integrates Genomic Data with Interaction Matrices"  https://doi.org/10.1186/s13059-015-0767-1 Genome Biology 16 (2015)
</details>

- [NAT](https://github.com/laseaman/4D_Nucleome_Analysis_Toolbox) - the 4D Nucleome Analysis Toolbox, for Hi-C data (text, cool format) normalization (ICE, Toeplitz, CNV-Toeplitz), TAD calling (Directionality index, Armatus, custom), karyotype abnormalities visualization on inter-chromosomal matrices, time-course visualization. Matlab. <details>
    <summary>Paper</summary>
    - Seaman, Laura, and Indika Rajapakse. "4D Nucleome Analysis Toolbox: Analysis of Hi-C Data with Abnormal Karyotype and Time Series Capabilities"  https://doi.org/10.1093/bioinformatics/btx484 Bioinformatics (Oxford, England) 34, no. 1 (01 2018)
</details>

- [HiC-3DViewer](https://bitbucket.org/nadhir/hic3dviewer/src/master/) - HiC-3DViewer is an interactive web-based tool designed to provide an intuitive environment for investigators to facilitate the 3D exploratory analysis of Hi-C data. It based on Flask and can be run directly or as a docker container. <details>
    <summary>Paper</summary>
    - Mohamed Nadhir, Djekidel, Wang, Mengjie, Michael Q. Zhang, Juntao Gao. "HiC-3DViewer: a new tool to visualize Hi-C data in 3D space"  https://doi.org/10.1007/s40484-017-0091-8 Quantitative Biology (2017)
</details>

- [NuChart](ftp://fileserver.itb.cnr.it/nuchart/) - gene-centric network of genes interacting in 3D. Integration of epigenomic features. Statistical network analysis. <details>
    <summary>Paper</summary>
    - Merelli, Ivan, Pietro Liò, and Luciano Milanesi. “NuChart: An R Package to Study Gene Spatial Neighbourhoods with Multi-Omics Annotations.” PloS One 8, no. 9 (2013): e75146. https://doi.org/10.1371/journal.pone.0075146
</details>

- [HiTC](https://bioconductor.org/packages/HiTC/) - R package for High Throughput Chromosome Conformation Capture analysis, Processed data import from TXT/BED into GRanges. Quality control, visualization. Normalization, 45-degree rotation and visualization of triangle TADs. Adding annotation at the bottom. PCA to detect A/B compartments. <details>
    <summary>Paper</summary>
    - Servant, Nicolas, Bryan R. Lajoie, Elphège P. Nora, Luca Giorgetti, Chong-Jian Chen, Edith Heard, Job Dekker, and Emmanuel Barillot. "HiTC: Exploration of High-Throughput ‘C’ Experiments"  https://doi.org/10.1093/bioinformatics/bts521 Bioinformatics (Oxford, England) 28, no. 21 (November 1, 2012)
</details>

- [pyGenomeTracks](https://github.com/deeptools/pyGenomeTracks) - python module to plot beautiful and highly customizable genome browser tracks.

- [TADKit](https://github.com/3DGenomes/TADkit) - 3D Genome Browser.[ Main web site](http://sgt.cnag.cat/3dg/tadkit/), and [GitHub](https://github.com/3DGenomes/TADkit)



## De novo genome scaffolding

- [EndHiC](https://github.com/fanagislab/EndHiC) - chromosome scaffolding using Hi-C links from contig ends. Requires contigs from PacBio's HiFiasm technology (assembled by HiCanu), and Hi-C data processed by HiC-Pro. Applied to human, rice, Arabidopsis, achieves higher accuracy than LACHESIS, ALLHiC, 3D-DNA. Perl scripts. <details>
    <summary>Paper</summary>
    Wang, Sen, Hengchao Wang, Fan Jiang, Anqi Wang, Hangwei Liu, Hanbo Zhao, Boyuan Yang, Dong Xu, Yan Zhang, and Wei Fan. "EndHiC: Assemble Large Contigs into Chromosomal-Level Scaffolds Using the Hi-C Links from Contig Ends](https://arxiv.org/abs/2111.15411 ArXiv, 30 Nov 2021
</details>

- [instaGRAAL](https://github.com/koszullab/instaGRAAL) - reimplementation of GRAAL genome assembler (chromosome level) for large genomes. Similar MCMC approach, implemented on NVIDIA GPU. Tested, among others, on segments of the human genome. <details>
    <summary>Paper</summary>
    - Baudry, Lyam, Nadège Guiglielmoni, Hervé Marie-Nelly, Alexandre Cormier, Martial Marbouty, Komlan Avia, Yann Loe Mie, et al. "InstaGRAAL: Chromosome-Level Quality Scaffolding of Genomes Using a Proximity Ligation-Based Scaffolder"  https://doi.org/10.1186/s13059-020-02041-z Genome Biology 21, no. 1 (December 2020)
</details>

- [HiCAssembler](https://github.com/maxplanck-ie/HiCAssembler) - Hi-C scaffolding tool combining assembly using Hi-C data with scaffolds from regular sequencing (short or long sequencing). Uses strategies from LACHESIS and 3D-DNA. Visual adjustment of scaffolding errors. Automatic and manual misassembly correction. <details>
    <summary>Paper</summary>
    - Renschler, Gina, Gautier Richard, Claudia Isabelle Keller Valsecchi, Sarah Toscano, Laura Arrigoni, Fidel Ramirez, and Asifa Akhtar. "Hi-C Guided Assemblies Reveal Conserved Regulatory Topologies on X and Autosomes despite Extensive Genome Shuffling"  https://doi.org/10.1101/580969 BioRxiv, March 18, 2019. 
</details>

- [bin3C](https://github.com/cerebis/bin3C) - resolving metagenome-assembled genomes from Hi-C data. Metagenomic assembly using [SPAdes](http://cab.spbu.ru/software/spades/). Tested using simulated (Sim3C and MetaART) and real-life data. Performance metrics: adjusted mutual information, weighted Bcubed. Contact matrix where bins are contigs. Infomap method for clustering the whole-contig graph. Compared with ProxiMeta (Phase Genomics). <details>
    <summary>Paper</summary>
    - DeMaere, Matthew Z., and Aaron E. Darling. "Bin3C: Exploiting Hi-C Sequencing Data to Accurately Resolve Metagenome-Assembled Genomes"  https://doi.org/10.1186/s13059-019-1643-1 Genome Biology 20, no. 1 (December 2019)
</details>

- [3D-DNA](https://github.com/theaidenlab/3D-DNA) Hi-C genome assembler and its application/validation. Methods are in the supplemental. <details>
    <summary>Paper</summary>
    - Dudchenko, Olga, Sanjit S. Batra, Arina D. Omer, Sarah K. Nyquist, Marie Hoeger, Neva C. Durand, Muhammad S. Shamim, et al. "De Novo Assembly of the Aedes Aegypti Genome Using Hi-C Yields Chromosome-Length Scaffolds"  https://doi.org/10.1126/science.aal3327 Science (New York, N.Y.) 356, no. 6333 (07 2017)
</details>

- [GRAAL](https://github.com/koszullab/GRAAL) - Genome (Re)Assembly Assessing Likelihood - genome assembly from Hi-C data. Gaps in genome assembly that can be filled by scaffolding. Superior to Lachesis and dnaTri, which are sensitive to duplications, clustering they use to initially arrange the scaffolds, parameters, unknown reliability. A Bayesian approach, prior assumptions are that cis-contact probabilities follow a power-law decay and that counts in the interaction matrix are Poisson. Multiple genomic structures tested using MCMC (Multiple-Try Metropolis algorithm) to maximize the likelihood of data given a genomic structure. <details>
    <summary>Paper</summary>
    - Marie-Nelly, Hervé, Martial Marbouty, Axel Cournac, Jean-François Flot, Gianni Liti, Dante Poggi Parodi, Sylvie Syan, et al. "High-Quality Genome (Re)Assembly Using Chromosomal Contact Data"  https://doi.org/10.1038/ncomms6695 Nature Communications 5 (December 17, 2014)
</details>

- [dnaTri](https://github.com/NoamKaplan/dna-triangulation) - genome scaffolding via probabilistic modeling using two constraints of Hi-C data - distance-dependent decay and cis-trans ratio. Using known chromosome scaffolds and de novo assembly. Naive Bayes classifier to distinguish chromosome-specific vs. on different chromosomes contigs. Average linkage clustering to assemble contigs into 23 groups of chromosomes. Completed 65 previously unplaced contigs. [Data](http://my5c.umassmed.edu/triangulation/). <details>
    <summary>Paper</summary>
    - Kaplan, Noam, and Job Dekker. "High-Throughput Genome Scaffolding from in Vivo DNA Interaction Frequency"  https://doi.org/10.1038/nbt.2768 Nature Biotechnology 31, no. 12 (December 2013)
</details>

- [Lachesis](https://github.com/shendurelab/LACHESIS) - a three-step genome scaffolding tool: 1) graph clustering of scaffolds to chromosome groups, 2) ordering clustered scaffolds (minimum spanning tree, reassembling longest-to-shortest branches), 3) assigning orientation (exact position and the decay of interactions). Duplications and repeat regions may be incorrectly ordered/oriented. Tested on a normal human, mouse, drosophila genomes, and on the HeLa cancer genome. <details>
    <summary>Paper</summary>
    - Burton, Joshua N., Andrew Adey, Rupali P. Patwardhan, Ruolan Qiu, Jacob O. Kitzman, and Jay Shendure. "Chromosome-Scale Scaffolding of de Novo Genome Assemblies Based on Chromatin Interactions"  https://doi.org/10.1038/nbt.2727 Nature Biotechnology 31, no. 12 (December 2013)
</details>

- [Genome-Assembly-Cookbook](https://github.com/theaidenlab/Genome-Assembly-Cookbook) - Genome assembly from Hi-C data, pipeline and instructions from the Aiden Lab. [Download PDF](https://www.dropbox.com/s/dk5gmptvtl1f5hf/manual_180319.docx?dl=0), [another PDF](https://aidenlab.org/assembly/manual_180322.pdf)

- [YaHS](https://github.com/c-zhou/yahs) - yet another Hi-C scaffolding tool. It relies on a new algothrim for contig joining detection which considers the topological distribution of Hi-C signals aiming to distingush real interaction signals from mapping nosies. Implemented in C, very fast.


## 3D modeling

- [Pastis-NB](https://github.com/hiclib/pastis) - an extrension of Pastis 3D modeling tool with negative binomial distribution-based modeling. Compared with MDS-based methods (ShRec3D, ChromSDE, Pastis-MDS) and Pastis- PM (Poisson model). More accurate and stable results. [Supplementary material](https://nellev.github.io/pastisnb/). <details>
    <summary>Paper</summary>
    - Nelle Varoquaux, William Stafford Noble, Jean-Phillipe Vert. "[Inference of genome 3D architecture by modeling overdispersion of Hi-C data"  https://doi.org/10.1101/2021.02.04.429864 bioRxiv. February 05, 2021
</details>

- [4DMax](https://github.com/Max-Highsmith/4DMax) - 3D modeling over time, predicts dynamic chromosome conformation using time course Hi-C data. In contrast to TADdyn, models entire chromosomes, uses gradient descent optimization of a spatial restraint-based maximum-likelihood function. In contrast to TADdyn that focuses on approx. 2Mb retions, 4DMax models whole chromosomes. Tested on simulate Hi-C progression over 6 time points, and 10-day time course of induced stem cell pluripotency in mice. Preserves and predicts A/B compartments, TADs. Output - video of chromosome dynamics

- [TADdyn](https://github.com/3DGenomes/TADbit/tree/TADdyn) - studying time-dependent dynamics of chromatin domains during natural and induced cell processes by simulating smooth 3D transitions of chromosome structure. A part of TADBit, developed by the Marti-Renom group. Tested on in situ Hi-C time course experiment, reprogramming of murine B cells to pluripotent cells, changes of 21 genomic loci. [Data and video](http://sgt.cnag.cat/3dg/datasets/). <details>
    <summary>Paper</summary>
    - Di Stefano, Marco, Ralph Stadhouders, Irene Farabella, David Castillo, François Serra, Thomas Graf, and Marc A. Marti-Renom. "Transcriptional Activation during Cell Reprogramming Correlates with the Formation of 3D Open Chromatin Hubs"  https://doi.org/10.1038/s41467-020-16396-1 Nature Communications 11, no. 1 (December 2020)
</details>

- [StoH-C](https://github.com/kimmackay/StoHi-C) - 3D genome reconstruction using tSNE. Python scripts for 3D embedding and visualization (plot-ly, matplotlib, Chart Studio). Visually tested on fission yeast genome as compared with MDS-reconstructed genome (wild type, G1-arrested, rad21 mutation, clr4 deletion). <details>
    <summary>Paper</summary>
    - MacKay, Kimberly, and Anthony Kusalik. "StoHi-C: Using t-Distributed Stochastic Neighbor Embedding (t-SNE) to Predict 3D Genome Structure from Hi-C Data"  https://doi.org/10.1101/2020.01.28.923615 Preprint. Bioinformatics, January 29, 2020. 
</details>

- [Hierarchical3DGenome](https://github.com/BDM-Lab/Hierarchical3DGenome) - high-resolution (5kb) reconstruction of the 3D structure of the genome. Using LorDG (https://github.com/BDM-Lab/LorDG), first, assemble the 3D model at the level of TADs, then inside individual TADs. Gm12878 cell line, Arrowhead for TAD calling, KR and ICE normalization, benchmarking against miniMDS, five tests including comparison with FISH. <details>
    <summary>Paper</summary>
    - Trieu, Tuan, Oluwatosin Oluwadare, and Jianlin Cheng. "Hierarchical Reconstruction of High-Resolution 3D Models of Large Chromosomes"  https://doi.org/10.1038/s41598-019-41369-w Scientific Reports 9, no. 1 (March 21, 2019): 4971. 
</details>

- [CSynth](http://csynth.org/) - 3D genome interactive modeling on GPU, and visualization. <details>
    <summary>Paper</summary>
    - Todd, Stephen, Peter Todd, Simon J McGowan, James R Hughes, Yasutaka Kakui, Frederic Fol Leymarie, William Latham, and Stephen Taylor. "CSynth: A Dynamic Modelling and Visualisation Tool for 3D Chromatin Structure"  https://doi.org/10.1101/499806 BioRxiv, January 1, 2019
</details>

- [GenomeFlow](https://github.com/jianlin-cheng/GenomeFlow) - a complete set of tools for Hi-C data alignment, normalization, 2D visualization, 3D genome modeling and visualization. ClusterTAD for TAD identification. LorDG and 3DMax for 3D genome reconstruction. <details>
    <summary>Paper</summary>
    - Trieu, Tuan, Oluwatosin Oluwadare, Julia Wopata, and Jianlin Cheng. "GenomeFlow: A Comprehensive Graphical Tool for Modeling and Analyzing 3D Genome Structure"  https://doi.org/10.1093/bioinformatics/bty802 Bioinformatics (Oxford, England), September 12, 2018. 
</details>

- [ShRec3D](https://sites.google.com/site/julienmozziconacci/home/softwares) - shortest-path reconstruction in 3D. Genome reconstruction by translating a Hi-C matrix into a distance matrix, then multidimensional scaling. Uses binary contact maps. <details>
    <summary>Paper</summary>
    - Lesne, Annick, Julien Riposo, Paul Roger, Axel Cournac, and Julien Mozziconacci. "3D Genome Reconstruction from Chromosomal Contacts"  https://doi.org/10.1038/nmeth.3104 Nature Methods 11, no. 11 (November 2014): 1141–43. 
</details>

## Deconvolution

- [THUNDER](https://github.com/brycerowland/thundeR) - cell-type deconvolution of Hi-C data. NMF, uses informative interactions within and between chromosomes (top 1000 features by Fano factor), reformatted into matrix form by concatenation. Needs number of cell types k. Tested on in silico mixture of cell types. Outperforms TOAST, CIBERSORT. R implementation. <details>
    <summary>Paper</summary>
    - Rowland, Bryce and Huh, Ruth and Hou, Zoey and Hu, Ming and Shen, Yin and Li, Yun "THUNDER: A Reference-Free Deconvolution Method to Infer Cell Type Proportions from Bulk Hi-C Data"  https://doi.org/10.1101/2020.11.12.379941 bioRxiv, November 12, 2020
</details>

## Haplotype separation

- [HaploHiC](https://github.com/Nobel-Justin/HaploHiC) - Hi-C phasing using SNPs/InDels, placement of unphased reads inferred from the nearby phased reads. <details>
    <summary>Paper</summary>
    - Lindsly, Stephen, Wenlong Jia, Haiming Chen, Sijia Liu, Scott Ronquist, Can Chen, Xingzhao Wen, et al. "Functional Organization of the Maternal and Paternal Human 4D Nucleome"  https://doi.org/10.1101/2020.03.15.992164 bioRxiv, June 17, 2021. Supplementary note 2 - algorithm details.
</details>

## Papers

- [3D Genome, from technology to visualization](https://zhonglab.gitbook.io/3dgenome/preface) - a GitBook by Xingzhao Wen and Sheng Zhong covering biological and computational aspects of 3D genomics and RNA-genome interactions

- [Pairix](https://github.com/4dn-dcic/pairix) - a tool to index and query files in [Pairs format](https://github.com/4dn-dcic/pairix/blob/master/pairs_format_specification.md), a block-compressed text file format for storing paired genomic coordinates (header plus 7 columns: readID, chr1, pos1, chr2, pos2, strand1, strand2). Bgzipped sorted files (chr1, chr2, pos1, then pos2 sorting order) are indexed (less than a second for million lines) by pairix (similar in functionality, but incompatible with tabix). Command-line, R ([Rpairix](https://github.com/4dn-dcic/Rpairix)), Python implementations. Supplementary scripts like bam2pairs, merged_nodups2pairs.pl, pairs_merger are available. [pairsqc](https://github.com/4dn-dcic/pairsqc) - QC report generator for pairs files. Standard of the 4D Nucleome consortium, supported by [Juicer](https://github.com/aidenlab/juicer), [cooler](https://github.com/open2c/cooler), [pairtools](https://github.com/open2c/pairtools) <details>
    <summary>Paper</summary>
    Lee, Soohyun, Carl Vitzthum, Burak H. Alver, and Peter J. Park. "Pairs and Pairix: A File Format and a Tool for Efficient Storage and Retrieval for Hi-C Read Pairs"  https://doi.org/10.1101/2021.08.24.457552 Bioinformatics preprint, August 26, 2021.
</details>

### Methodological Reviews

- [pipelines_list.csv](pipelines_list.csv) - A list of available pipelines, URLs, from Miura et al., “[Practical Analysis of Hi-C Data](https://link.springer.com/protocol/10.1007%2F978-1-4939-8766-5_16)”
- [pipeline_comparison.csv](pipeline_comparison.csv) - Available analysis options in each pipeline, from Miura et al., “[Practical Analysis of Hi-C Data](https://link.springer.com/protocol/10.1007%2F978-1-4939-8766-5_16)”
- [Table summarizing functionality of Hi-C data analysis tools](https://www.sciencedirect.com/science/article/pii/S1672022918304339?via%3Dihub#t0005), from Calandrelli et al., “[GITAR: An Open Source Tool for Analysis and Visualization of Hi-C Data](https://www.sciencedirect.com/science/article/pii/S1672022918304339)”

- Ay, Ferhat, and William S. Noble. “[Analysis Methods for Studying the 3D Architecture of the Genome](https://doi.org/10.1186/s13059-015-0745-7).” Genome Biology 16 (September 2, 2015) - Hi-C technology and methods review. [Table 1](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0745-7#Tab1) - list of tools. Biases, normalization, matrix balancing. Extracting significant contacts, obs/exp ratio, parametric (power-law, neg binomial, double exponential), non-parametric (splines). 3D enrichment. References. TAD identification, directionality index. Outlook, the importance of comparative analysis

- Chang, Pearl, Moloya Gohain, Ming-Ren Yen, and Pao-Yang Chen. “[Computational Methods for Assessing Chromatin Hierarchy](https://doi.org/10.1016/j.csbj.2018.02.003).” Computational and Structural Biotechnology Journal 16 (2018) - Review of higher-order (chromatin conformation capture) and primary order (DNAse, ATAC) technologies and analysis tools. Table 1 - technology summaries. Table 2 - tool summaries. Inter-chromosomal calls using Binarized contact maps. Visualization. Primary order technologies - details and peak calling.

- Nicoletti, Chiara, Mattia Forcato, and Silvio Bicciato. “[Computational Methods for Analyzing Genome-Wide Chromosome Conformation Capture Data](https://doi.org/10.1016/j.copbio.2018.01.023).” Current Opinion in Biotechnology 54 (December 2018) - 3C-Hi-C tools review, Table 1 lists categorizes main tools, Figure 1 displays all steps in technology and analysis (alignment, resolution, normalization, including accounting for CNVs, A/B compartments, TAD detection, visualization). A concise description of all tools.

- Pal, Koustav, Mattia Forcato, and Francesco Ferrari. “[Hi-C Analysis: From Data Generation to Integration](https://doi.org/10.1007/s12551-018-0489-1).” Biophysical Reviews, December 20, 2018.  - Hi-C technology, data, 3D structures, analysis, and tools. Technology improvement and increasing resolution. FASTQ processing steps ("Hi-C data analysis: from FASTQ to interaction maps" section), pipelines, finding minimum resolution, normalization. Downstream analysis: A/B compartment detection, TAD callers, Hierarchical TADs, interaction callers. Data formats (pairix, sparse matrix format, cool, hic, butlr, hdf5, pgl). Hi-C visualization tools. [Table 2 - summary and comparison of all tools](https://link.springer.com/article/10.1007%2Fs12551-018-0489-1#Tab2)

- Yardımcı, Galip Gürkan, and William Stafford Noble. “[Software Tools for Visualizing Hi-C Data](https://doi.org/10.1186/s13059-017-1161-y).” Genome Biology 18, no. 1 (December 2017). - Hi-C technology, data, and visualization review. Suggestions about graph representation.

- Waldispühl, Jérôme, Eric Zhang, Alexander Butyaev, Elena Nazarova, and Yan Cyr. “[Storage, Visualization, and Navigation of 3D Genomics Data](https://doi.org/10.1016/j.ymeth.2018.05.008).” Methods, May 2018 - Review of tools for visualization of 3C-Hi-C data, challenges, analysis (Table 1). Data formats (hic, cool, BUTLR, ccmap). Database to quickly access 3D data. Details of each visualization tool in Section 4

- Oluwadare, Oluwatosin, Max Highsmith, and Jianlin Cheng. “[An Overview of Methods for Reconstructing 3-D Chromosome and Genome Structures from Hi-C Data.](https://doi.org/10.1186/s12575-019-0094-0)” Biological Procedures Online 21, no. 1 (December 2019) - 3D genome reconstruction review. Intro into equilibrium/fractal globule models. Classification of reconstruction methods: distance-, contact-. and probability-based. [Table 1](https://biologicalproceduresonline.biomedcentral.com/articles/10.1186/s12575-019-0094-0#Tab1) summarizes many tools, methods, and references.


### General Reviews

- Bouwman, Britta A. M., and Wouter de Laat. “[Getting the Genome in Shape: The Formation of Loops, Domains and Compartments](https://doi.org/10.1186/s13059-015-0730-1).” Genome Biology 16 (August 10, 2015) - TAD/loop formation review. Convergent CTCF, cohesin, mediator, different scenarios of loop formation. Stability and dynamics of TADs. Rich source of references.

- Chakraborty, Abhijit, and Ferhat Ay. “[The Role of 3D Genome Organization in Disease: From Compartments to Single Nucleotides](https://doi.org/10.1016/j.semcdb.2018.07.005).” Seminars in Cell & Developmental Biology 90 (June 2019): 104–13. - 3D genome structure and disease. Evolution of technologies from FISH to variants of chromatin conformation capture. Hierarchical 3D organization, Table 1 summarizes each layer and its involvement in disease. Rearrangement of TADs/loops in cancer and other diseases. Specific examples of the biological importance of TADs, loops as means of distal communication.

- Zheng, H., and Xie, W. (2019). "[The role of 3D genome organization in development and cell differentiation](https://www.nature.com/articles/s41580-019-0132-4)." Nat. Rev. Mol. Cell Biol. - 3D structure of the genome and its changes during gametogenesis, embryonic development, lineage commitment, differentiation. Changes in developmental disorders and diseases. Chromatin compartments and TADs. Chromatin changes during X chromosome inactivation. Promoter-enhancer interactions established during development are accompanied by gene expression changes. Polycomb-mediated interactions may repress developmental genes. References to many studies.

- Yu, Miao, and Bing Ren. “[The Three-Dimensional Organization of Mammalian Genomes](https://doi.org/10.1146/annurev-cellbio-100616-060531).” Annual Review of Cell and Developmental Biology 33 (06 2017) - 3D genome structure review. The role of gene promoters, enhancers, and insulators in regulating gene expression. Imaging-based tools, all flavors of chromatin conformation capture technologies. 3D features - chromosome territories, topologically associated domains (TADs), the association of TAD boundaries with replication domains, CTCF binding, transcriptional activity, housekeeping genes, genome reorganization during mitosis. Use of 3D data to annotate noncoding GWAS SNPs. 3D genome structure change in disease.

- Fraser, J., C. Ferrai, A. M. Chiariello, M. Schueler, T. Rito, G. Laudanno, M. Barbieri, et al. “[Hierarchical Folding and Reorganization of Chromosomes Are Linked to Transcriptional Changes in Cellular Differentiation](http://msb.embopress.org/content/msb/11/12/852.full.pdf).” Molecular Systems Biology 11, no. 12 (December 23, 2015) - 3D genome organization parts. Well-written and detailed. References. Technologies: FISH, 3C. 4C, 5C, Hi-C, GCC, TCC, ChIA-PET. Typical resolution - 40bp to 1Mb. LADs - conserved, but some are cell type-specific. Chromosome territories. Cell type-specific. Inter-chromosomal interactions may be important to define cell-specific interactions. A/B compartments identified by PCA. Chromatin loops, marked by CTCF and Cohesin binding, sometimes, with Mediator. Transcription factories

- Dekker, Job, Marc A. Marti-Renom, and Leonid A. Mirny. “[Exploring the Three-Dimensional Organization of Genomes: Interpreting Chromatin Interaction Data](https://doi.org/10.1038/nrg3454).” Nature Reviews. Genetics 14, no. 6 (June 2013) - 3D genome review. Chromosomal territories, transcription factories. Details of each 3C technology. Exponential decay of interaction frequencies. Box 2: A/B compartments (several Mb), TAD definition, size (hundreds of kb). TADs are largely stable, A/B compartments are tissue-specific. Adjacent TADs are not necessarily of opposing signs, may jointly form A/B compartments. Genes co-expression, enhancer-promoters interactions are confined to TADs. 3D modeling.

- Witten, Daniela M., and William Stafford Noble. “[On the Assessment of Statistical Significance of Three-Dimensional Colocalization of Sets of Genomic Elements](https://doi.org/10.1093/nar/gks012).” Nucleic Acids Research 40, no. 9 (May 2012)

### Technology

- [4D Nucleome Protocols](https://www.4dnucleome.org/protocols.html) - Collection of genomic technologies currently in use or being developed in the 4DN network - links to wet-lab protocols and papers. [4DN portal blog](https://www.4dnucleome.org/outreach.html)

- Hi-C 3.0 protocol. Evaluation of 12 experimental Hi-C protocols - they capture different 3D genome features with different efficiencies. Additional crosslinking with DSG improves signal-to-noise, loop detection, reduced compartment detection. Evaluating 4 restriction enzymes, MNase, DdeI, DpnII, HindIII. 4 cell lines - H1-hESCs, differentiated endoderms, HFF, HeLa (two cell cycle stages). 63 libraries total. All protocols detect cell type-specific differences, A/B compartments, insulation strength. MNase digestion improves loop detection. Anchors for multi-loop interactions can be detected. Double enzyme use improves loop detection. Evaluation of enrichment of CTCF, SMC3, H3K4me3, H3K27ac at loop boundaries. Ultra-deeply sequenced maps using Hi-C, Micro-C, and Hi-C 3.0 protocols (not yet available). [cLIMS](https://github.com/dekkerlab/cLIMS-docker) Hi-C data management system. [Scripts to reproduce results](https://github.com/dekkerlab/matrix_paper). [Tweet](https://twitter.com/job_dekker/status/1343529467277430784?s=20). <details>
    <summary>Paper</summary>
    - Oksuz, Betul Akgol, Liyan Yang, Sameer Abraham, Sergey V. Venev, Nils Krietenstein, Krishna Mohan Parsi, Hakan Ozadam, et al. "Systematic Evaluation of Chromosome Conformation Capture Assays"  https://doi.org/10.1101/2020.12.26.424448 Preprint. Genomics, December 27, 2020.
</details>

- Chromatin conformation capture technologies, from 3C to imaging. 3D structures (nucleolus, nuclear speckles, polycomb bodies, chromosome territories, A/B compartments, TADs, loops), their roles in gene expression (sometimes, conflicting), replication timing, DNA repair. Agreement (and disagreement) examples between 3C methods and FISH. Description of libation-based (3C - Hi-C) and ligation-free (GAM, SPRITE, DamC) technologies. Multiway interactions, primarily occur within TADs. TAD formation, loop extrusion mechanisms. Association between replication timing and A/B compartments. Effect of mechanical forces on chromosome folding. <details>
    <summary>Paper</summary>
    - McCord, Rachel Patton, Noam Kaplan, and Luca Giorgetti. "Chromosome Conformation Capture and Beyond: Toward an Integrative View of Chromosome Structure and Function"  https://doi.org/10.1016/j.molcel.2019.12.021 Molecular Cell, January 2020
</details>

![](/img/3C_technologies.png)

- Review of Hi-C, Capture-C, and Capture-C technologies, their computational preprocessing. Experimental protocols, similarities and differences, types of reads (figures), details of alignment, read orientation, elimination of artifacts, quality metrics. A brief overview of preprocessing tools. Example preprocessing of three types of data. Java tool for preprocessing all types of data, [Diachromatic](https://github.com/TheJacksonLaboratory/diachromatic) (Differential Analysis of Chromatin Interactions by Capture), [GOPHER](https://github.com/TheJacksonLaboratory/Gopher) (Generator Of Probes for capture Hi-C Experiments at high Resolution) for genome cutting, probe design. <details>
    <summary>Paper</summary>
    - Hansen, Peter, Michael Gargano, Jochen Hecht, Jonas Ibn-Salem, Guy Karlebach, Johannes T. Roehr, and Peter N. Robinson. "Computational Processing and Quality Control of Hi-C, Capture Hi-C and Capture-C Data"  https://doi.org/10.3390/genes10070548 Genes 10, no. 7 (July 18, 2019): 548. 
</details>

- Chromosome conformation capture technologies, 4C, 5C, Hi-C, ChIP-loop, ChIA-PET. From microscopy observations (constrained movement of genomic loci, LADs, preferential stability of chromosome conformation and its independence from transcription), to technology details (Figure 1). Examples of alpha- and beta-globin locus studies by different technologies, X chromosome inactivation, HOXA-d gene clusters. The future vision of single-cell, single-allele investigation of chromatin interactions. <details>
    <summary>Paper</summary>
    - Wit, E. de, and W. de Laat. "A Decade of 3C Technologies: Insights into Nuclear Organization"  https://doi.org/10.1101/gad.179804.111 Genes & Development 26, no. 1 (January 1, 2012)
</details>

- Review of technologies for studying the 3D structure of the genome. From microscopy to 3C techniques revealing CTCF and cohesin as the key proteins for establishing chromatin loops.TADs are unlikely over large distances >>1Mb. Details of 3C, 4C, 5C, Hi-C, ChIP-PET, and other derivatives. A/B compartments and their subdivision. TADs, their conservation, \~35-50% still seem to change. CTCF (directionality of binding important) and cohesin. Diseases and the 3D genome, examples. Key steps in data analysis and interpretation, software, visualization. Hi-C data specifics - chimeric reads, mapping, data representation as fixed or enzyme-sized bins, normalization, detection of A/B compartments and TAD boundaries, significant interactions. Hi-C analysis tools: HiC-Pro, HiCUP, HOMER, Juicer. Tools for 3D modeling. <details>
    <summary>Paper</summary>
    - Denker, Annette, and Wouter de Laat. "The Second Decade of 3C Technologies: Detailed Insights into Nuclear Organization"  https://doi.org/10.1101/gad.281964.116 Genes & Development 30, no. 12 (June 15, 2016)
</details>

- **RedChIP** technology for identifying RNA-DNA interactions mediated by a particular protein. Combines RNA-DNA proximity ligation and ChIP. EZH2 in human ESCs and CTCF in K562. An input fraction without IP sequenced in parallel. [GEO GSE174474](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?&hx0026;acc=GSE174474) - RedChIP replicates (EZH2/CTCF samples and input). [GitHub](https://github.com/agalitsyna/RedClib) - RedClib processing pipeline. See the [RedC paper](https://doi.org/10.1093/nar/gkaa457) for more details. <details>
    <summary>Paper</summary>
    Gavrilov, Alexey A., Rinat I. Sultanov, Mikhail D. Magnitov, Aleksandra A. Galitsyna, Erdem B. Dashinimaev, Erez Lieberman Aiden, and Sergey V. Razin. “RedChIP Identifies Noncoding RNAs Associated with Genomic Sites Occupied by Polycomb and CTCF Proteins.” Proceedings of the National Academy of Sciences 119, no. 1 (January 4, 2022): e2116222119. https://doi.org/10.1073/pnas.2116222119.
</details>

- **RD-SPRITE** (RNA & DNA SPRITE) technology to map the spatial organization of RNA and DNA (improved efficiency of the RNA-tagging steps). Noncoding RNAs form high-concentration territories throughout the nucleus (ncRNAs involved in rRNA processing organize around rRNA genes, splicing ncRNAs are concentrated near PolII sites, more examples). In general, (noncoding) RNA-chromatin structures are associated with three functional classes: RNA processing, heterochromatin assembly, gene regulation. [GSE GEO151515](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE151515) - RD-SPRITE data (clusters information) on mouse ESCs, naive and treated with Actinomycin D. [GitHub 1](https://github.com/GuttmanLab/sprite2.0-pipeline), [GitHub 2](https://github.com/GuttmanLab/sprite-pipeline) - pipelines. <details>
    <summary>Paper</summary>
    Quinodoz, Sofia A., Joanna W. Jachowicz, Prashant Bhat, Noah Ollikainen, Abhik K. Banerjee, Isabel N. Goronzy, Mario R. Blanco, et al. “RNA Promotes the Formation of Spatial Compartments in the Nucleus.” Cell 184, no. 23 (November 2021): 5775-5790.e30. https://doi.org/10.1016/j.cell.2021.10.014.
</details>

- **Hi-CO** - chromatin conformation capture with nucleosome orientation technology. Ligation of DNA entry or exit points at every nucleosome locus in a micrococcal nuclease (MNase)-fragmented genome. Produces \~300M reads. Computational analysis - simulated annealing - molecular dynamics, determines 3D positions and orientation of every nucleosome. Not suitable for single-cell genome analysis, only detects pairwise ligations. Applied to the S. cerevisiae genome. Protocol. [Example data and tutorial](https://figshare.com/articles/software/Hi-CO_3D_genome_structure_analysis_with_nucleosome_resolution/13176101/1). <details>
    <summary>Paper</summary>
    - Ohno, Masae, Tadashi Ando, David G. Priest, and Yuichi Taniguchi. "Hi-CO: 3D Genome Structure Analysis with Nucleosome Resolution"  https://doi.org/10.1038/s41596-021-00543-z Nature Protocols, May 28, 2021. 
</details>

- [RADICL-seq](https://github.com/fagostini/RADICL_analysis) - RNA And DNA Interacting Complexes Ligated and sequenced - RNA-chromatin interaction profiling in intact nuclei. Crosslinking, digesting withDNAse I, RNAse H treatment (reduces ribosomal contamination), a bridge adapter specifically ligating RNA and DNA, reverse crosslinking, conversion to double-stranded DNA, cutting to 25-27bp length with EcoP15I enzyme. RNA- and DNA tags mapped, quantified by distance. Improvement over other technologies (MARGI, GRID-seq, SPRITE) - less cells, less spurious interactions, more trans interactions (lncRNAs in particular), more long-distance interactions. Four technology advantages in Discussion. Analysis - accounts for coverage, one-sided binomial test to call significant interactions. Data - mESC, oli-neu (from mOPCs). Visualization as 25kb contact matrix. Several noncoding transcripts interact in trans. Integration with CAGE data, comparison with Hi-C, association with TAD boundaries, A/B compartments, repeat elements. Differential analysis, Cell-type-specific interactions. [Code](https://github.com/fagostini/RADICL_analysis), [data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE132192). <details>
    <summary>Paper</summary>
    - Bonetti, Alessandro, Federico Agostini, Ana Maria Suzuki, Kosuke Hashimoto, Giovanni Pascarella, Juliette Gimenez, Leonie Roos, et al. "RADICL-Seq Identifies General and Cell Type–Specific Principles of Genome-Wide RNA-Chromatin Interactions"  https://doi.org/10.1038/s41467-020-14337-6 Nature Communications, (December 2020)
</details>

- **tagHi-C** - low-input tagmentation-based Hi-C. Applied to mouse hematopoiesis 10 major blood cell types. Changes in compartments and the Rabl configuration defining chromatin condensation. Gene-body-associating domains are a general property of highly-expressed genes. Spatial chromatin loops link GWAS SNPs to candidate blood-phenotype genes. HiC-Pro to Juicer. [GEO GSE142216](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE142216) - RNA-seq, replicates, [GEO GSE152918](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE152918) - tagHi-C data, replicates, combined .hic files. <details>
    <summary>Paper</summary>
    - Zhang C, Xu Z, Yang S, Sun G, Jia L, Zheng Z, Gu Q, Tao W, Cheng T, Li C, Cheng H. "[tagHi-C Reveals 3D Chromatin Architecture Dynamics during Mouse Hematopoiesis"  https://doi.org/10.1016/j.celrep.2020.108206 Cell Rep. 2020 Sep 29 
</details>

- [scsHi-C](https://github.com/gerlichlab/scshic_analysis) - sister-chromatid-sensitive Hi-C to explore interactions between the sister chromatids. Distinguishing cis from trans sister contacts based on 4-thio-thymidine (4sT) labeling. Paired organization of sister chromatins in interphase and complete separation in mitosis. TADs that exhibit tight pairing are heterochromatin marked by H3K27me3. Chromatids are predominantly linked at TAD boundaries, within TADs - more flexible. Investigation of looping mechanism - NIPBL-depletion, Sororin degradation. Jupyter notebooks for each analysis. <details>
    <summary>Paper</summary>
    - Mitter, Michael, Catherina Gasser, Zsuzsanna Takacs, Christoph C. H. Langer, Wen Tang, Gregor Jessberger, Charlie T. Beales, et al. "Sister-Chromatid-Sensitive Hi-C Reveals the Conformation of Replicated Human Chromosomes"  https://doi.org/10.1101/2020.03.10.978148 Preprint. Cell Biology, March 11, 2020. 
</details>

- 4C technology, wet-lab protocol, and data analysis and visualization. R-based processing pipeline [pipe4C](https://github.com/deLaatLab/pipe4C), configuration parameters. <details>
    <summary>Paper</summary>
    - Krijger, Peter H.L., Geert Geeven, Valerio Bianchi, Catharina R.E. Hilvering, and Wouter de Laat. "4C-Seq from Beginning to End: A Detailed Protocol for Sample Preparation and Data Analysis"  https://doi.org/10.1016/j.ymeth.2019.07.014 Methods 170 (January 2020)
</details>

- SisterC Hi-C technology to test interactions between sister chromatids. Uses BrdU incorporation in S-phase and single-strand degradation by UV/Hoechst treatment to obtain inter-sister or intra-sister interactions. Findings about the alignment of chromatids, strong at centromeres, looser (\~35kb spaced) interactions along arms, loops up to 50kb. Tested on the S. cerevisiae genome. distiller-nf, pairtools, cooltools for processing. <details>
    <summary>Paper</summary>
    - "Detecting Chromatin Interactions along and between Sister Chromatids with SisterC](http://biorxiv.org/content/early/2020/03/11/2020.03.10.986208.abstract bioRxiv 2020.03.10
</details>

- Pore-C chromatin conformation capture using Oxford Nanopore Technologies, direct sequencing of multi-way chromatin contacts without amplification (concatemers, HOLR - high-order and long-range contacts). >18 times higher efficiency as compared with SPRITE, enrichment in concatemers. Tested on the Gm12878 cell line. Hi-C matrix from Pore-C well resembles published data. Concatemers show significantly lower distance decay. Concatemers better resolve complex cancer rearrangements, well-suited for de novo genome scaffolding. [Pore-C tools](https://github.com/nanoporetech/pore-c/) and a [Snakemake pipeline](https://github.com/nanoporetech/Pore-C-Snakemake), [detection of multi-way interactions](https://github.com/mskilab/GxG). <details>
    <summary>Paper</summary>
    - Ulahannan, Netha, Matthew Pendleton, Aditya Deshpande, Stefan Schwenk, Julie M. Behr, Xiaoguang Dai, Carly Tyer, et al. "Nanopore Sequencing of DNA Concatemers Reveals Higher-Order Features of Chromatin Structure"  https://doi.org/10.1101/833590 Preprint. Genomics, November 7, 2019. 
</details>

- Tiled-C low-input 3C technology, requiring >20,000 cells. Applied for in vivo mouse erythroid differentiation, alpha-globin genes. TADs are pre-existing, regulatory interactions gradually form during differentiation. Integration with scRNA-seq data (CITE-seq technology) and ATAC-seq data. Analyzed using [CCseqBasic pipeline](https://github.com/Hughes-Genome-Group/CCseqBasicF/) and [TiledC](https://github.com/oudelaar/TiledC). [Data (Tiled-C, CITE-seq, ATAC-seq)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE137477). <details>
    <summary>Paper</summary>
    - Oudelaar, A. Marieke, Robert A. Beagrie, Matthew Gosden, Sara de Ornellas, Emily Georgiades, Jon Kerry, Daniel Hidalgo, et al. "Dynamics of the 4D Genome during Lineage Specification, Differentiation and Maturation in Vivo"  https://doi.org/10.1101/763763 Preprint. Genomics, September 10, 2019. 
</details>

- **Red-C** (RNA Ends on DNA Capture) technology - proximity ligation-based technology to understand RNA-DNA interactome (3' and 5' ends of the RNA molecule associated with a given DNA site). Technology description(Methods, Results, Figure 1). Assesses all coding and noncoding RNA classes (piRNAs, tRNAs, rRNAs, snRNAs, scRNAs, srpRNAs, vlinc, antisense RNAs). Applied to K562 cells. The RNA-DNA matrices show a wide distribution of RNA contacts along extended genomic regions. The highest number of contacts was observed for mRNA, linc and vlinc RNAs. Enhancer RNAs (eRNAs) produced from strong enhancers interact with other strong enhancers on the same chromosome.  MIR3648 and MIR3687 interact with repressed chromatin genome-wide. Investigation of mRNA interaction preference across gene body. Discovery of novel chromatin-interacting RNAs (X-RNAs). [Processed Red-C and RNA-seq data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE136141), [GitHub, Nextflow processing pipeline](https://github.com/agalitsyna/RedClib). <details>
    <summary>Paper</summary>
    - Gavrilov, Alexey A, Anastasiya A Zharikova, Aleksandra A Galitsyna, Artem V Luzhin, Natalia M Rubanova, Arkadiy K Golov, Nadezhda V Petrova, et al. "Studying RNA–DNA Interactome by Red-C Identiﬁes Noncoding RNAs Associated with Various Chromatin Types and Reveals Transcription Dynamics"  https://doi.org/10.1093/nar/gkaa457 July 6, 2020
</details>

- **ChIA-Drop** technology - multiplex chromatin interaction analysis via droplet-based and barcode-linked sequencing. 10X genomics technology, instead of cells, each gel-bead-in-emulsion contains crosslinked (but not ligated) chromatin and unique barcode. Singleton reads removed, distance constraints further refine multi-way interactions. FISH agrees with ChIA-Drop. Only approx. 20% of promoters are regulated by multiple enhancers, in Drosophila S2 cells. Data. Supplementary - notes about data processing, overview of [ChIA-Dropbox](https://github.com/TheJacksonLaboratory/ChIA-DropBox) software for visualization, Python implementation. [Drosophila S2 cell line ChIA-Drop data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE109355), [Hi-C](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE99104). <details>
    <summary>Paper</summary>
    - Zheng, Meizhen, Simon Zhongyuan Tian, Daniel Capurso, Minji Kim, Rahul Maurya, Byoungkoo Lee, Emaly Piecuch, et al. "Multiplex Chromatin Interactions with Single-Molecule Precision"  https://doi.org/10.1038/s41586-019-0949-1 Nature (February 2019)
</details>

- [ChIA-Dropbox](https://github.com/TheJacksonLaboratory/ChIA-DropBox) - analysis and visualization of ChIA-Drop data (10X Genomics-based GEMs containing cross-linked chromatin). Alignment, demultiplexing, reconstruction of intra-chromosomal chromatin droplets from barcodes, drops inter-chromosomal, generates visualizations compatible with Juicebox, BASIC browser, its own ChIA-View (R/Shiny app). QC plots, multi-way interactions visualization, cluster/fragment/promoter views. Global and RNAPII-enriched [GEO GSE109355](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE109355) - ChIA-Drop data for Drosophila. <details>
    <summary>Paper</summary>
    - Zheng, Meizhen. "ChIA-DropBox: A Novel Analysis and Visualization Pipeline for Multiplex Chromatin Interactions"  https://doi.org/10.1101/613034 Preprint, April 18, 2019
</details>

- Dip-C technology for single-cell Hi-C, multiplex end-tagging amplification (META). Detects approx. 5 times more contacts. Possible to make haplotype-separated Hi-C maps, detect CNVs, resolve X-chromosome inactivation. Approx. 10kb-resolution Hi-C matrices, 3D genome reconstruction at 20kb resolution. PCA on chromatin compartments separates cell types. Comparison with Nagano data, bulk Gm12878 Hi-C. [dip-c - Tools to analyze Dip-C (or other 3C/Hi-C) data](https://github.com/tanlongzhi/dip-c), [hickit](https://github.com/lh3/hickit). Processed data: [Gm12878, 17 cells, PBMC, 18 cells](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE117876). <details>
    <summary>Paper</summary>
    - Tan, Longzhi, Dong Xing, Chi-Han Chang, Heng Li, and X. Sunney Xie. "Three-Dimensional Genome Structures of Single Diploid Human Cells"  https://doi.org/10.1126/science.aat5641 Science. August 31, 2018
</details>

- Methyl-HiC technology, in situ Hi-C and WGBS. Comparable Hi-C matrices, TADs. 20% fewer CpGs overall, more CpGs in open chromatin. Proximal CpGs correlate irrespectively of loop anchors, weaker for inter-chromosomal interactions. Application to single-cell, mouse ESCs under different conditions. Relevant clustering, cluster-specific genes. Methods for wet-lab and computational processing. [Bulk (replicates) and single-cell Methyl-HiC data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE119171). Scripts in https://bitbucket.org/dnaase/bisulfitehic/src/master/, Bhmem pipeline to map bisulfite-converted reads, Juicer pipeline for processing, VC normalization, HiCRep at 1Mb matrix similarity. <details>
    <summary>Paper</summary>
    - Li, Guoqiang, Yaping Liu, Yanxiao Zhang, Naoki Kubo, Miao Yu, Rongxin Fang, Manolis Kellis, and Bing Ren. "Joint Profiling of DNA Methylation and Chromatin Architecture in Single Cells"  https://doi.org/10.1038/s41592-019-0502-z Nature Methods, August 5, 2019. 
</details>

- Review of chromatin conformation capture technologies, from image-based methods (FISH), through proximity ligation (3/4/5C, Hi-C, TCC, ChIA-PET, scHi-C), to ligation-free methods (GAM, SPRITE, ChIA-Drop). Details of each technology (Table 1, Figures), comparison of them (Table 2). <details>
    <summary>Paper</summary>
    - Kempfer, Rieke, and Ana Pombo. "Methods for Mapping 3D Chromosome Architecture"  https://doi.org/10.1038/s41576-019-0195-2 Nature Reviews Genetics, December 17, 2019. 
</details>

- Optimization steps for Hi-C wet-lab protocol. Pitfalls and their effect on the downstream quality. Recommendations for each step. 
    - Golloshi, Rosela, Jacob Sanders, and Rachel Patton McCord. "Iteratively Improving Hi-C Experiments One Step at a Time"  https://doi.org/10.1101/287201 Preprint. Genomics, March 22, 2018. 

- DLO Hi-C technology (digestion-ligation-only Hi-C). Uses two rounds of digestion and ligation, without biotin and pull-down. Allows for early evaluation of Hi-C quality. Cost-effective, high signal-to-noise-ratio. Tested on THP-1 (human monocytes) and K562 cells. [Data processed with ChIA-PET Tool, normalized with ICE](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE89663). <details>
    <summary>Paper</summary>
    - Lin, Da, Ping Hong, Siheng Zhang, Weize Xu, Muhammad Jamal, Keji Yan, Yingying Lei, et al. "Digestion-Ligation-Only Hi-C Is an Efficient and Cost-Effective Method for Chromosome Conformation Capture"  https://doi.org/10.1038/s41588-018-0111-2 Nature Genetics 50, no. 5 (May 2018)
</details>

- HIPMap - high-throughput imaging and analysis pipeline to map the location of gene loci within the 3D space. FISH in a 384-well plate format, automated imaging. <details>
    <summary>Paper</summary>
    - Shachar, Sigal, Gianluca Pegoraro, and Tom Misteli. "HIPMap: A High-Throughput Imaging Method for Mapping Spatial Gene Positions"  https://doi.org/10.1101/sqb.2015.80.027417 Cold Spring Harbor Symposia on Quantitative Biology 80 (2015)
</details>

- HiC method description, 1Mb, Gm06990. Small chromosomes, but 18, interact. Compartment A associated with open chromatin. 1Mb, 100kb resolution. <details>
    <summary>Paper</summary>
    - Lieberman-Aiden, Erez, Nynke L. van Berkum, Louise Williams, Maxim Imakaev, Tobias Ragoczy, Agnes Telling, Ido Amit, et al. "Comprehensive Mapping of Long-Range Interactions Reveals Folding Principles of the Human Genome"  https://doi.org/10.1126/science.1181369 Science (New York, N.Y.) 326, no. 5950 (October 9, 2009)
</details>

- 3C technology, the matrix of interaction frequencies, application to reveal spatial information, applied to yeast (S cerevisiae) genome. Interphase and metaphase chromosomes show different patterns of interactions. Distance-dependent decay of interaction frequencies. Basic observations on chromosome size, inter-chromosomal interactions. <details>
    <summary>Paper</summary>
    - Dekker, Job, Karsten Rippe, Martijn Dekker, and Nancy Kleckner. "Capturing Chromosome Conformation"  https://doi.org/10.1126/science.1067799 Science (New York, N.Y.) 295, no. 5558 (February 15, 2002)
</details>

- The Arima kit uses two restriction enzymes: ^GATC (DpnII), G^ANTC (N can be either of the 4 genomic bases) (HinfI), which after ligation of DNA ends generates 4 possible ligation junctions in the chimeric reads: GATC-GATC, GANT-GATC, GANT-ANTC, GATC-ANTC. Source: 'Hi-C library preparation' Methods section from [Du et al., “DNA Methylation Is Required to Maintain Both DNA Replication Timing Precision and 3D Genome Organization Integrity.”"  https://doi.org/10.1016/j.celrep.2021.109722)

#### Micro-C

- Stability of enhancer-promoter (E-P) interactions after 3-hours depletion of CTCF, cohesin, WAPL, and YY1 (auxin-inducible degron). Micro-C, nascent transcript profiling (mNET-seq), live-cell single-molecule imaging (single-particle tracking technique spaSPT. Mouse embryonic stem cells. E-P interaction strength correlates with gene expression, cohesin loop strength does not. E-P and P-P interactions can cross TAD boundaries. TADs are much more effective at insulating cohesin loops than E-P and P-P loops. CTCF depletion had minimal impact on genomewide interactions; RAD21 depletion reduced contact frequency in the range of 10 – 200 kb but increased interactions at 300 kb – 5 Mb; and WAPL depletion increased contacts at 70 – 700 kb but reduced contacts at 1 – 5 Mb. YY1 depletion has minimal effect on gene expression and E-R and P-P interactions. [GEO GSE130257](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE130275) - Previously published Micro-C replicates of mESCs WT and RNA PolII inhibition, .mcool and .hic files. [Zenodo 10.5281/zenodo.5035837](https://zenodo.org/record/5035837) - spaSPT data for endogenously tagging HaloTag-YY1 in mESCs. [GEO GSE178982](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE178982) - ChIP-seq, RNA-seq, mNET-seq, Micro-C replicates of CTCF, RAD21, WAPL, YY1 depletion, pooled .mcool files. <details>
    <summary>Paper</summary>
    Hsieh, Tsung-Han S., Claudia Cattoglio, Elena Slobodyanyuk, Anders S. Hansen, Xavier Darzacq, and Robert Tjian. “Enhancer-Promoter Interactions and Transcription Are Maintained upon Acute Loss of CTCF, Cohesin, WAPL, and YY1.” Preprint. Molecular Biology, July 14, 2021. https://doi.org/10.1101/2021.07.14.452365.
</details>

- Micro-Capture-C (MCC) technology. Advanced and optimized 3C technology, using micrococcal nuclease (MNase), intact cells permeabilized with digitonin, ultra-deep sequencing, plus sequencing the ligation junction. 330 viewpoints (promoters, enhancers, CTCF binding sites) in primary mouse erythroid and empryonic stem cells. Many biological observations, cohesin is required for CTCF contacts.Enhancer-promoter contacts are mediated by at least partly different mechanisms than cohesin-mediated interactions. [Computational pipeline](https://process.innovation.ox.ac.uk/software/p/16529a/micro-capture-c-academic/1). [GEO GSE153256](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE153256) - mouse spleen erythroid cells MCC data. [GEO GSE144336](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE144336) - mouse primary erythroid cells, embryonic stem cells, HUDEP-2 cells. MCC, CTCF/Rad21/NIPBL ChIP-seq. <details>
    <summary>Paper</summary>
    - Hua, Peng, Mohsin Badat, Lars L. P. Hanssen, Lance D. Hentges, Nicholas Crump, Damien J. Downes, Danuta M. Jeziorska, et al. "Defining Genome Architecture at Base-Pair Resolution"  https://doi.org/10.1038/s41586-021-03639-4 Nature, (July 1, 2021)
</details>

- Ultra-deep Micro-C maps of human embryonic stem cells and fibroblasts. Compared with in situ Hi-C (DpnII 4bp cutter), Micro-C allows for the detection of \~20,000 additional loops, improved signal-to-noise ratio. Similar distance-dependent decay, recovery of A/B compartments, better recovery of close-range interactions. High-resolution interaction boundaries are not created equal - most are CTCF+ and YY1+, some are CTCF- and YY1+, CTCF- and YY1-, and completely negative boundaries. Multiple, weak pause sites of SMC complexes. Distiller-nf processing, ICE normalization, other Mirnylab tools. [Data](https://data.4dnucleome.org/). <details>
    <summary>Paper</summary>
    - Krietenstein, Nils, Sameer Abraham, Sergey V. Venev, Nezar Abdennur, Johan Gibcus, Tsung-Han S. Hsieh, Krishna Mohan Parsi, et al. "Ultrastructural Details of Mammalian Chromosome Architecture"  https://doi.org/10.1016/j.molcel.2020.03.003 Molecular Cell 78, no. 3 (May 2020)
</details>

- Micro-C (MNase digestion Hi-C) data analysis. Nucleosome-level (\~100-200bp) resolution Hi-C, captures all structures in regular Hi-C data. Stripes/flames structures correspond to enhancer-promoter interactions, colocalize with PolII, CTCF.  TADs are further split into "micro TADs", insulation score. Active boundaries colocalize with CpG islands, promoters, tRNA genes. Inactive boundaries are in repeats. Micro TADs subdivided into five subgroups. Two-start zig-zag model tetra-nucleosome stacks. Mouse stem cell, 38 biological replicates. [Twitter](https://twitter.com/Stanley_TH/status/1242843692081111040?s=20). <details>
    <summary>Paper</summary>
    - Hsieh, Tsung-Han S., Claudia Cattoglio, Elena Slobodyanyuk, Anders S. Hansen, Oliver J. Rando, Robert Tjian, and Xavier Darzacq. "Resolving the 3D Landscape of Transcription-Linked Mammalian Chromatin Folding"  https://doi.org/10.1016/j.molcel.2020.03.002 Molecular Cell, March 2020
</details>

- Micro-C (MNase digestion Hi-C) technology and basic analysis. Human embryonic stem cells H1-ESC and differentiated human foreskin fibroblasts (HFFc6). Captures standard Hi-C features, with many additional interaction peaks ("dots"). Enrichment of classical marks of TAD boundaries (Fig 3C) - RAD21, TAF1, PHF8, CTCF, TBP, POL2RA, YY1, and more. <details>
    <summary>Paper</summary>
    - Krietenstein, Nils, Sameer Abraham, Sergey Venev, Nezar Abdennur, Johan Gibcus, Tsung-Han Hsieh, Krishna Mohan Parsi, et al. "Ultrastructural Details of Mammalian Chromosome Architecture"  https://doi.org/10.1101/639922 Preprint. Genomics, May 17, 2019. 
</details>

- Micro-C technology - mononucleosome resolution mapping in yeast. Micrococcal nuclease to fragment chromatin. Yeast does not have TADs, but Micro-C revealed self-associating domains (chromatin interaction domains, CIDs) driven by the number of genes. Enrichment of histone modifications. [Data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE68016). <details>
    <summary>Paper</summary>
    - Hsieh, Tsung-Han S., Assaf Weiner, Bryan Lajoie, Job Dekker, Nir Friedman, and Oliver J. Rando. "Mapping Nucleosome Resolution Chromosome Folding in Yeast by Micro-C"  https://doi.org/10.1016/j.cell.2015.05.048 Cell 162, no. 1 (July 2015)
</details>

- [Micro-C](https://github.com/dovetail-genomics/Micro-C) scripts and [documentation](https://micro-c.readthedocs.io/) for Dovetail™ Micro-C Kit. Uses the Micrococcal nuclease (MNase) enzyme instead of restriction enzymes for chromatin digestion, yielding 146 bp fragments distributed frequently across the genome. Detailed computational processing of Micro-C data, generation of valid pairs using bwa mem, pairtools, juicer_tools, cooler and other genomics tools, QC, contact matrix generation. [Introduction to Dovetail™ Micro-C Technology Video](https://vimeo.com/431456105), 5min, [Breaking the Hi-C Resolution Barrier with Micro-C Video](https://vimeo.com/470724936), 45 min. [Micro-C datasets](https://micro-c.readthedocs.io/en/latest/data_sets.html), [MicroC](https://github.com/EricSDavis/MicroC) Snakemake pipeline by Eric Davis.


#### Multi-way interactions

- **ImmunoGAM** - an extension of genome architecture mappint (GAM, thin nuclear cryosections. Works with small numbers of cells (approx. 400-1500 cells). Immunoselection of cryosections (incubation with antibodies). Applied to profile oligodendrocytes (OLGs), pyramidal glutamatergic neurons (PGNs), dopaminergic neurons (DNs) of mouse brain. Integration with pseudobulk RNA-seq and ATAC-seq. Insulation score to detect domains, extensive cell type-specific TAD, AB compartment rearrangement. "Melting" - contact loss at highly expressed long neuronal genes (MELTRON pipeline to calculate a melting score https://github.com/DominikSzabo1/Meltron). Methods: GAM data window calling and QC. [Extensive supplementary material](https://www.nature.com/articles/s41586-021-04081-2#Sec55). [GEO GSE148792](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE148792) - GAM sequencing data from DN, PGN and OLG, non-normalized co-segregation matrices, normalized pair-wised chromatin contacts maps and raw GAM segregation tables. [Microscopy images](https://github.com/pombo-lab/WinickNg_Kukalev_Harabula_Nature_2021/tree/main/microscopy_images/). A public UCSC session with all data produced, as well as all published data utilized in this study is available at [the UCSC Genome Browser session](http://genome-euro.ucsc.edu/s/Kjmorris/Winick_Ng_2021_GAMbrainpublicsession). [Tweet](https://twitter.com/LabPombo/status/1461008979837005826?s=20). <details>
    <summary>Paper</summary>
    - Winick-Ng, Warren, Alexander Kukalev, Izabela Harabula, Luna Zea-Redondo, Dominik Szabó, Mandy Meijer, Leonid Serebreni, et al. "Cell-Type Specialization Is Encoded by Specific Chromatin Topologies"  https://doi.org/10.1038/s41586-021-04081-2 Nature, November 17, 2021. 
</details>

- [MATCHA](https://github.com/ma-compbio/MATCHA) - a computational framework for the analysis of multi-way chromatin interactions (hyperedges). Graph embedding fed into Hyper-SAGNN (self-attention based graph neural network for hypergraphs). Applied to SPRITE and ChIA-Drop data, Gm12878 at 1Mb and 100kb resolution. <details>
    <summary>Paper</summary>
    - Zhang, Ruochi, and Jian Ma. "MATCHA: Probing Multi-Way Chromatin Interaction with Hypergraph Representation Learning"  https://doi.org/10.1016/j.cels.2020.04.004 Cell Systems, (May 2020)
</details>

- **Multi-contact 3C** (MC-3C, based on conventional 3C, C-walk, and multi-contact 4C approaches) technology reveals distinct chromosome territories with very little mixing, never entanglement, same with chromosomal compartment domains (A-A, B-B interactions predominant, A-B - minimal to none). Analysis of C-walks - connected paths of pairwise interactions. Compared with C-walks generated from Hi-C data. Permutation analysis of the significance of insulated, mixed, and intermediate domains. PacBio sequencing, processing with SMRT Analysis package and a [custom pipeline](https://github.com/dekkerlab/MC-3C_scripts). <details>
    <summary>Paper</summary>
    - Tavares-Cadete, Filipe, Davood Norouzi, Bastiaan Dekker, Yu Liu, and Job Dekker. "Multi-Contact 3C Data Reveal That the Human Genome Is Largely Unentangled"  https://doi.org/10.1101/2020.03.03.975425 Preprint. Genomics, March 4, 2020. 
</details>

- [MIA-Sig](https://github.com/TheJacksonLaboratory/mia-sig) (multiplex interactions analysis by signal processing algorithms) - de-noise the multi-interaction data, assess the statistical significance of chromatin complexes, identify topological domains and multi-way inter-TAD contacts. Tailored for ChIA-Drop, also works with SPRITE and GAM data. Uses the assumption that the genomic distance of a true multiway interaction should be more evenly spaced to remove noise. <details>
    <summary>Paper</summary>
    - Kim, Minji, Meizhen Zheng, Simon Zhongyuan Tian, Byoungkoo Lee, Jeffrey H. Chuang, and Yijun Ruan. "MIA-Sig: Multiplex Chromatin Interaction Analysis by Signalprocessing and Statistical Algorithms"  https://doi.org/10.1186/s13059-019-1868-z Genome Biology, (December 2019)
</details>

- **MC-4C** multi-way contacts technology and computational protocols. ~2 weeks, ~$600/sample, best for <120kb regions. [Computational protocol](https://github.com/deLaatLab/mc4c_py), test data included. <details>
    <summary>Paper</summary>
    - Vermeulen, Carlo, Amin Allahyar, Britta A. M. Bouwman, Peter H. L. Krijger, Marjon J. A. M. Verstegen, Geert Geeven, Christian Valdes-Quezada, et al. "Multi-Contact 4C: Long-Molecule Sequencing of Complex Proximity Ligation Products to Uncover Local Cooperative and Competitive Chromatin Topologies"  https://doi.org/10.1038/s41596-019-0242-7 Nature Protocols 15, no. 2 (February 2020)
</details>

- **MC-4C** - Multi-way interactions technology, uses Nanopore MinION (or, PacBio) sequencing. Cross-linking, cutting with four-cutter and six-cutter enzymes, circularization, cutting with Cas9 gRNA designed to the viewpoint region, selective amplification of concatemers with primers specific to the viewpoint. Rigorous filtering strategy, interactions are allowing to distinguish reads coming from individual alleles. Compared with genome-wide multi-contact technologies C-walks, SPRITE, GAM, Tri-C. Applied to mouse beta-globin (fetal liver where hemoglobin genes are expressed, and brain, where they are silent) and protocadherin-alpha (same tissues, vice versa ) loci. Super enhancers can form hubs, target multiple genes. WAPL deletion in HAP1 (leukemia) cells stimulates the collision of CTCF-anchored domain loops to form rosette-like structures. [MC-4C processing pipeline](https://github.com/UMCUGenetics/pymc4c/), [Visualization of the analyzed data](http://www.multicontactchromatin.nl/), [raw data](https://www.ebi.ac.uk/ena/data/view/PRJEB23327), [processed data matrices](https://data.mendeley.com/datasets/wbk8hk87r2/1). <details>
    <summary>Paper</summary>
    - Allahyar, Amin, Carlo Vermeulen, Britta A. M. Bouwman, Peter H. L. Krijger, Marjon J. A. M. Verstegen, Geert Geeven, Melissa van Kranenburg, et al. "Enhancer Hubs and Loop Collisions Identified from Single-Allele Topologies"  https://doi.org/10.1038/s41588-018-0161-5 Nature Genetics 50, no. 8 (August 2018)
</details>

- **Multiplex-GAM** - Genome Architecture Mapping technology. Multiple nuclear profiles (2-3 NPs, slices of nuclei) are sequenced together. Updates of the SLICE method for GAM data analysis. Details on the dependencies between the number of GAM samples, probability to detect interactions, the number of NPs per sample, technical parameters. TAD boundaries match those from Hi-C. Method-specific contacts exist, but GAM contacts are enriched in CTCF-enhancer contacts and other active transcription annotations, in contrast to heterochromatin-prone Hi-C contacts. No data yet. <details>
    <summary>Paper</summary>
    - Beagrie, Robert A, Christoph J Thieme, Carlo Annunziatella, Catherine Baugher, Yingnan Zhang, Markus Schueler, Dorothee CA Kramer, et al. "Multiplex-GAM: Genome-Wide Identification of Chromatin Contacts Yields Insights Not Captured by Hi-C"  https://doi.org/10.1101/2020.07.31.230284 Preprint. Molecular Biology, July 31, 2020. 
</details>

- **GAM** (genome architecture mapping) - restriction- and ligation free chromatin conformation capture technology. Isolates and sequences DNA content of many ultra-thin (~0.22um) cryo-fixes nuclear slices, whole-genome amplification.~30kb matrix is built on frequencies of co-occurrences of regions in multiple slices. Applied to mouse ESCs. Normalization using linkage disequilibrium (better than ICE). GAM and Hi-C matrices are highly correlated, A/B compartments, TADs significantly overlap. Enhancers and active genes significantly interact. Multi-way interactions, triplets, super-enhancers are enriched in three-way interactions, confirmed by FISH. SLICE (Statistical Inference of co-segregation) mathematical model to assign significance of interactions ([Supplementary Note 1](https://static-content.springer.com/esm/art%3A10.1038%2Fnature21411/MediaObjects/41586_2017_BFnature21411_MOESM22_ESM.pdf)). Negative binomial modeling of significant interactions, log-normal noise. [Supplementary Table 2](https://static-content.springer.com/esm/art%3A10.1038%2Fnature21411/MediaObjects/41586_2017_BFnature21411_MOESM24_ESM.xlsx) - genomic coordinates of triplet (three-way interacting) TADs. Raw data, processed matrices, [Python scripts](https://gam.tools/papers/nature-2017/), [GEO GSE64881](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE64881) - mouse ES cell GAM matrices at 1Mb and 30kb resolution. <details>
    <summary>Paper</summary>
    - Beagrie, Robert A., Antonio Scialdone, Markus Schueler, Dorothee C. A. Kraemer, Mita Chotalia, Sheila Q. Xie, Mariano Barbieri, et al. "Complex Multi-Enhancer Contacts Captured by Genome Architecture Mapping"  https://doi.org/10.1038/nature21411 Nature 543, no. 7646 (23 2017)
</details>

- **SPRITE** (Split-Pool Recognition of Interactions by Tag Extension) - Multi-way interactions technology, barcode system based on repeated pooling ans splitting of crosslinked DNAhairballs to uncover clustered DNA fragments (SPRITE clusters). Does not involve proximity ligation. Transcriptionally active interaction hubs around duclear speckles, inactive - around nucleolus. These nuclear bodies constrain the 3D packaging. Applied to mouse embryonic stem cells (mESCs) and GM12878, data correlates well with Hi-C. [Data: 25kb-1Mb inter- and intra-chromosomal interactions](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE114242), [Processing Pipeline](https://github.com/GuttmanLab/sprite-pipeline/wiki). <details>
    <summary>Paper</summary>
    - Quinodoz, Sofia A., Noah Ollikainen, Barbara Tabak, Ali Palla, Jan Marten Schmidt, Elizabeth Detmar, Mason M. Lai, et al. "Higher-Order Inter-Chromosomal Hubs Shape 3D Genome Organization in the Nucleus"  https://doi.org/10.1016/j.cell.2018.05.024 Cell 174, no. 3 (July 2018)
</details>

- **C-walks**, multi-way technology, genome-wide. TADs organize chromosomal territories. Active and inactive TAD properties. Methods: Good mathematical description of insulation score calculations. Filter TADs smaller than 250kb. Inter-chromosomal contacts are rare, \~7-10%. Concatemers (more than two contacts) are unlikely. <details>
    <summary>Paper</summary>
    - Olivares-Chauvet, Pedro, Zohar Mukamel, Aviezer Lifshitz, Omer Schwartzman, Noa Oded Elkayam, Yaniv Lubling, Gintaras Deikus, Robert P. Sebra, and Amos Tanay. "Capturing Pairwise and Multi-Way Chromosomal Conformations Using Chromosomal Walks"  https://doi.org/10.1038/nature20158 Nature 540, no. 7632 (November 30, 2016)
</details>

- **TM3C** - Tethered multiple 3C technology to probe multi-point contacts. NHEK, KBM7 cells, detected the Philadelphia chromosome, investigated triple contacts in the IGF2-H19 locus at 40kb, detected typical genomic structures (chromosomal compartments, distance-decay, TADs), reconstructed 3D genome at 1Mb resolution. A two-phase mapping strategy that separately maps chimeric subsequences within a single read (Methods). Multiple 4-cutter restriction enzymes. <details>
    <summary>Paper</summary>
    - Ay, Ferhat, Thanh H Vu, Michael J Zeitz, Nelle Varoquaux, Jan E Carette, Jean-Philippe Vert, Andrew R Hoffman, and William S Noble. "Identifying Multi-Locus Chromatin Contacts in Human Cells Using Tethered Multiple 3C"  https://doi.org/10.1186/s12864-015-1236-7 BMC Genomics 16, no. 1 (2015)
</details>

- **INGRID** - chromatin conformation capture technology using in-gel replication of interacting DNA segments. Detects multi-way interactions. Protocol, demonstration of beta-globin gene locus. <details>
    <summary>Paper</summary>
    - Gavrilov, Alexey A., Helena V. Chetverina, Elina S. Chermnykh, Sergey V. Razin, and Alexander B. Chetverin. "Quantitative Analysis of Genomic Element Interactions by Molecular Colony Technique"  https://doi.org/10.1093/nar/gkt1322 Nucleic Acids Research 42, no. 5 (March 1, 2014)
</details>

#### Imaging

- [OligoFISSEQ"  https://doi.org/10.1038/s41592-020-0890-0) - fluorescence in situ sequencing (FISSEQ) of barcoded oligopaint probes to enable the rapid visualization of many targeted genomic regions. Three strategies for interrogation of targets: sequencing by ligation (SBL, O-LIT), sequencing by synthesis (SBS, O-SIT), sequencing by hybridization (SBH, O-HIT). Applied to human diploit fibroblast cells, 36 regions across 6 chromosomes in just 4-8 rounds of sequencing. Fine tracing of 46 regions on X chromosome. Combined with OligoSTORM, allows for single-molecule super-resolution imaging. Whole genome-ready technology. [Figure-specific source data](https://www.nature.com/articles/s41592-020-0890-0#Sec51), [Analysis scripts](https://github.com/3DGenomes/OligoFISSEQ/). <details>
    <summary>Paper</summary>
    - Nguyen, Huy Q., Shyamtanu Chattoraj, David Castillo, Son C. Nguyen, Guy Nir, Antonios Lioutas, Elliot A. Hershberg, et al. "3D Mapping and Accelerated Super-Resolution Imaging of the Human Genome Using in Situ Sequencing"  https://doi.org/10.1038/s41592-020-0890-0 Nature Methods, (August 2020)
</details>

- [MERFISH](https://github.com/BogdanBintu/ChromatinImaging) - Super-resolution imaging technology, reconstruction 3D structure in single cells at 30kb resolution, 1.2Mb region of Chr21 in IMR90 cells. Distance maps obtained by microscopy show small distance for loci within, and larger between, TADs. TAD-like structures exist in single cells. 2.5Mb region of Chr21 in HCT116 cells, cohesin depletion does not abolish TADs, only alter their preferential positioning. Multi-point (triplet) interactions are prevalent. TAD boundaries are highly heterogeneous in single cells. , diffraction-limited and STORM (stochastic optical reconstruction microscopy) imaging. [GitHub](https://github.com/BogdanBintu/ChromatinImaging). <details>
    <summary>Paper</summary>
    - Bintu, Bogdan, Leslie J. Mateo, Jun-Han Su, Nicholas A. Sinnott-Armstrong, Mirae Parker, Seon Kinrot, Kei Yamaya, Alistair N. Boettiger, and Xiaowei Zhuang. "Super-Resolution Chromatin Tracing Reveals Domains and Cooperative Interactions in Single Cells"  https://doi.org/10.1126/science.aau1783 Science, (October 26, 2018)
</details>

### Normalization

- Lyu, Hongqiang, Erhu Liu, and Zhifang Wu. "Comparison of Normalization Methods for Hi-C Data](https://europepmc.org/article/med/31588782 BioTechniques 68, no. 2 (2020) - a comprehensive analysis of six Hi-C normalization methods for their ability to remove systematic biases. The introduction provides a good classification and overview of different normalization methods, including the latest methods for cross-sample normalization, such as "multiHiCcompare." Human and mouse Hi-C data were used, only cis interaction matrices are considered. A systematic protocol for benchmarking is presented. Several benchmarks were performed, including statistical quality, the influence of resolution, consistency of distance-dependent changes in interaction frequency, reproducibility of the 3D architecture. [multiHiCcompare](https://bioconductor.org/packages/multiHiCcompare/) is reported as outperforming other methods on a range of performance metrics. 

- Imakaev, Maxim, Geoffrey Fudenberg, Rachel Patton McCord, Natalia Naumova, Anton Goloborodko, Bryan R. Lajoie, Job Dekker, and Leonid A. Mirny. "Iterative Correction of Hi-C Data Reveals Hallmarks of Chromosome Organization"  https://doi.org/10.1038/nmeth.2148 Nature Methods 9, no. 10 (October 2012) - ICE - Iterative Correction and Eigenvalue decomposition, normalization of HiC data. Assumption - all loci should have equal visibility. Deconvolution into eigenvectors/values.

- Yaffe, Eitan, and Amos Tanay. "Probabilistic Modeling of Hi-C Contact Maps Eliminates Systematic Biases to Characterize Global Chromosomal Architecture"  https://doi.org/10.1038/ng.947 Nature Genetics 43, no. 11 (November 2011) - Sources of biases: 1) non-specific ligation (large distance between pairs); 2) length of each ligated fragments; 3) CG content and nucleotide composition; 4) Mappability. Normalization. Enrichment of long-range interactions in active promoters. General aggregation of active chromosomal domains. Chromosomal territories, high-activity and two low-activity genomic clusters

### TAD detection

- [Brief description of 22 TAD calling methods](https://static-content.springer.com/esm/art%3A10.1186%2Fs13059-018-1596-9/MediaObjects/13059_2018_1596_MOESM1_ESM.pdf). Source: [Zufferey et al., “Comparison of Computational Methods for the Identification of Topologically Associating Domains.”](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-018-1596-9#Bib1)

- Dali, Rola, and Mathieu Blanchette. "A Critical Assessment of Topologically Associating Domain Prediction Tools"  https://doi.org/10.1093/nar/gkx145 Nucleic Acids Research 45, no. 6 (April 7, 2017) - TAD definition, tools. Meta-TADs, hierarchy, overlapping TADs. HiCPlotter for visualization. Manual annotation as a gold standard. Sequencing depth and resolution affect things. Code, manual annotations

- Forcato, Mattia, Chiara Nicoletti, Koustav Pal, Carmen Maria Livi, Francesco Ferrari, and Silvio Bicciato. "Comparison of Computational Methods for Hi-C Data Analysis"  https://doi.org/10.1038/nmeth.4325 Nature Methods, June 12, 2017 - Hi-C processing and TAD calling tools benchmarking, Table 1, simulated (Lun and Smyth method) and real data. Notes about pluses and minuses of each tool. TAD reproducibility is higher than chromatin interactions, increases with a larger number of reads. Consistent enrichment of TAD boundaries in CTCF, irrespectively of TAD caller. Hi-C replication is poor, just a bit more than random. Supplementary table 2 - technical details about each program, Supplementary Note 1 - Hi-C preprocessing tools, Supplementary Note 2 - TAD callers. [Supplementary note 3](https://images.nature.com/full/nature-assets/nmeth/journal/v14/n7/extref/nmeth.4325-S1.pdf) - how to simulate Hi-C data. [Supplementary note 6](https://images.nature.com/full/nature-assets/nmeth/journal/v14/n7/extref/nmeth.4325-S1.pdf) - how to install tools. [Tools for TAD comparison, and simulated matrices](https://bitbucket.org/mforcato/hictoolscompare.git), https://bitbucket.org/mforcato/hictoolscompare.git

- Olivares-Chauvet, Pedro, Zohar Mukamel, Aviezer Lifshitz, Omer Schwartzman, Noa Oded Elkayam, Yaniv Lubling, Gintaras Deikus, Robert P. Sebra, and Amos Tanay. "Capturing Pairwise and Multi-Way Chromosomal Conformations Using Chromosomal Walks"  https://doi.org/10.1038/nature20158 Nature 540, no. 7632 (November 30, 2016) - TADs organize chromosomal territories. Active and inactive TAD properties. Methods: Good mathematical description of insulation score calculations. Filter TADs smaller than 250kb. Inter-chromosomal contacts are rare, \~7-10%. Concatemers (more than two contacts) are unlikely.

- Zufferey, Marie, Daniele Tavernari, Elisa Oricchio, and Giovanni Ciriello. "Comparison of Computational Methods for the Identification of Topologically Associating Domains"  https://doi.org/10.1186/s13059-018-1596-9 Genome Biology 19, no. 1 (10 2018) - Comparison of 22 TAD callers across different conditions. Callers are classified as linear score-based, statistical model-based, clustering, graph theory. Table 1 and Additional file 1 summarizes each caller. The effect of data resolution, normalization, hierarchy. Test on Rao 2014 data, chromosome 6. ICE or LGF (local genomic feature,) normalization. The measure of Concordance (MoC) to compare TADs. CTCF/cohesin as a measure of biological significance. TopDom, HiCseg, CaTCH, CHDF are the top performers. [R scripts, including for calculation MoC](https://github.com/CSOgroup/TAD-benchmarking-scripts), https://github.com/CSOgroup/TAD-benchmarking-scripts

- Rocha, Pedro P., Ramya Raviram, Richard Bonneau, and Jane A. Skok. "Breaking TADs: Insights into Hierarchical Genome Organization"  https://doi.org/10.2217/epi.15.25 Epigenomics 7, no. 4 (2015) - Textbook overview of TADs in 3 pages with key references. 3D organization discovery using FISH, 3C, Hi-C. Discovery of A/B compartments (euchromatin, heterochromatin), TADs as regulatory units conserved even across syntenic regions in different organisms. TADs coordinate gene expression. TAD boundaries are not created equal. Examples of changes of TAD boundaries (Hox gene cluster, ES differentiation). Hierarchy of TADs.

- Crane, Emily, Qian Bian, Rachel Patton McCord, Bryan R. Lajoie, Bayly S. Wheeler, Edward J. Ralston, Satoru Uzawa, Job Dekker, and Barbara J. Meyer. "Condensin-Driven Remodelling of X Chromosome Topology during Dosage Compensation"  https://doi.org/10.1038/nature14450 Nature 523, no. 7559 (July 9, 2015). - Insulation Score to define TADs - sliding square along the diagonal, aggregating signal within it. This aggregated score is normalized and binned into TADs, boundaries. See [Methods and implementation](https://github.com/dekkerlab/crane-nature-2015). [matrix2insulation.pl](https://github.com/dekkerlab/cworld-dekker/tree/master/scripts/perl/matrix2insulation.pl), Parameters: -is 480000 -ids 320000 -im iqrMean -nt 0 -ss 160000 -yb 1.5 -nt 0 -bmoe 0. 

- "Hierarchical Regulatory Domain Inference from Hi-C Data" - presentation by Bartek Wilczyński about TAD detection, existing algorithms, new SHERPA and OPPA methods. [Video](https://simons.berkeley.edu/talks/bartek-wilczynski-03-10-16), [PDF](https://simons.berkeley.edu/sites/default/files/docs/4588/2016-03-10-simons-institute-wilczynski.pdf), [Web site](http://regulomics.mimuw.edu.pl/wp/), [GitHub](https://github.com/regulomics/) - SHERPA and OPPA code there.

### Spectral clustering

- Y. X Rachel Wang, Purnamrita Sarkar, Oana Ursu, Anshul Kundaje and Peter J. Bickel, "[Network modelling of topological domains using Hi-C data](https://arxiv.org/abs/1707.09587)"  - TAD analysis using graph-theoretical (network-based) methods. Treats TADs as a "community" within the network. Shows that naive spectral clustering is generally ineffective, leaving gaps in the data. 

- Liu, Sijia, Pin-Yu Chen, Alfred Hero, and Indika Rajapakse. "Dynamic Network Analysis of the 4D Nucleome"  https://doi.org/10.1101/268318 BioRxiv, January 1, 2018. - Temporal Hi-C data analysis using graph theory. Integrated with RNA-seq data. Network-based approaches such as von Neumann graph entropy, network centrality, and multilayer network theory are applied to reveal universal patterns of the dynamic genome. Toeplitz normalization. Graph Laplacian matrix. Detailed statistics.

- Norton, Heidi K, Harvey Huang, Daniel J Emerson, Jesi Kim, Shi Gu, Danielle S Bassett, and Jennifer E Phillips-Cremins. "Detecting Hierarchical 3-D Genome Domain Reconfiguration with Network Modularity"  https://doi.org/10.1101/089011 November 22, 2016. - Graph theory for TAD identification. Louvain-like local greedy algorithm to maximize network modularity. Vary resolution parameter, hierarchical TAD identification. Hierarchical spatial variance minimization method. ROC analysis to quantify performance. Adjusted RAND score to quantify the TAD overlap.

- Chen, Jie, Alfred O. Hero, and Indika Rajapakse. "Spectral Identification of Topological Domains"  https://doi.org/10.1093/bioinformatics/btw221 Bioinformatics (Oxford, England) 32, no. 14 (15 2016) - Spectral algorithm to define TADs. Laplacian graph segmentation using Fiedler vector iteratively. Toeplitz normalization to remove distance effect. Spectral TADs do not overlap with Dixon's, but better overlap with CTCF. Python implementation https://github.com/shappiron/TAD-Laplacian-Identification

## Courses

- [3DGenomes/3DAROC](https://github.com/3DGenomes/3DAROC) - list of notebooks for 4 days course on Hi-C data handling and 3D modeling of chromatin. Jupiter notebooks, using `pytadbit`. Instructors: Marc Marti-Renom, Francois Serra , David Castillo.

- [3d-genome-processing-tutorial](https://github.com/hms-dbmi/3d-genome-processing-tutorial) - A 3D genome data processing tutorial for ISMB/ECCB 2017. https://github.com/hms-dbmi/3d-genome-processing-tutorial

- [Workshop on measuring, analyzing, and visualizing the 3D genome with Hi-C data](https://github.com/hms-dbmi/hic-data-analysis-bootcamp). Presentations (PDFs, PPTX) and Jupyter notebooks. Cooler, HiCGlass, HiPlier. https://github.com/hms-dbmi/hic-data-analysis-bootcamp

- [The 3D Organization of Our Genome](https://youtu.be/Pl44JjA--2k) 3 min video recapitulates our current understanding of genome organization in the three-dimensional space of the cell nucleus. More videos in the description. By the [Cavalli lab videos](https://www.youtube.com/channel/UCFjv-tOfb_AaGLE-tKvLvTA), [Tweet](https://twitter.com/giacomo_cavalli/status/1453771881740476422?s=20)

## Labs

- [Best-Labs-of-3D-Genome](https://github.com/XiaoTaoWang/Best-Labs-of-3D-Genome) - Most active 3D genomics labs, collaborative networks. By Xiaotao Wang

<center><img src="https://github.com/XiaoTaoWang/Best-Labs-of-3D-Genome/blob/master/networks/2017-2021/2017-2021.coauthors.png?raw=true" alt="Best-Labs-of-3D-Genome" width="514" height="300"></center>


