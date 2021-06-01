# AMLproject
We are working on the AML [pedDep]() project with [DFCi]() &amp; the [BroadInsitute](); [BCH](), looking at [CRCs]() and their relation to genomic dependencies in the context of [MLL/AML]().


link to the first paper on the role of the CRC in childhood cancer:
link to the second paper on :
link to the third paper on :

## Data

blacklist from https://github.com/Boyle-Lab/Blacklist/blob/master/lists/hg38-blacklist.v2.bed.gz
##### DBs

http://cistrome.org/db/#/

EOL1;
DPF2
H3K4me1
H3K27ac
BRD9
CTCF
SMARCC1
H3K4me3
SMARCA4
BRD7
BRD9

MOLM-13;
SMARCA4
BRD7
CTCF
SMARCA4
DPF2
BRD9

SKNO-1
H3K27me3
H3K4me1
H3K4me3
ASXL2
H3K27ac

THP-1 
H3K4me3
MLLT3
RUNX1
H3K79me2
H3K27ac


MV411 Pol2, BRD4, H3K79me2 Chips before/after inhibition of BRD4 DOT1L with SGC0946 IBET and SGC0946+IBET
https://www.ncbi.nlm.nih.gov/sra?term=SRP111133

### RNAseq data

slamseq iBet.. max data:
slamseq RNAseq max data:
slamseq iBet: muharpaper:

#### RNPv1

##### Date
IRF2BP2 IDT 12/18/19
IRF8  IDT 12/18/19
MEF2D IDT 12/18/19
MYC IDT 12/18/19
RUNX1 IDT 12/18/19
RUNX2 IDT 12/18/19
SPI1  IDT 12/18/19
ZMYND8  IDT 12/18/19
CDK6  IDT 12/18/19
BRD4  IDT 12/18/19
Non-Target  IDT 12/18/19
LMO2  Synthego  4/9/19
LYL1  Synthego  4/9/19
MAX Synthego  4/9/19
ZEB2  Synthego  4/9/19
MEF2C Synthego  4/9/19
Non-Target  Synthego  4/9/19
MEIS1 Synthego  6/7/19
FLI1  Synthego  6/17/19
ELF2  Synthego  6/17/19
GFI1  Synthego  6/17/19
IKZF1 Synthego  6/17/19
CEBPa Synthego  6/17/19
MYB Synthego  7/16/19

##### batch effect

MAX CEBPa ZEB2 

##### Bio 

MYC BRD4 MEF2D CDK6 IRF2BP2
RUNX1 RUNX2 ZMYND8 SPI1
GFI1 FLY1 MYB IKZF1 ELF2 CEBPa MEIS1
ZEB2
LMO2 MAX LYL1 MEF2C

##### diff expression

BRD4 CDK6 IRF2BP2 IRF8 MEF2D MYC RUNX1 RUNX2 SPI1 ZEB2 ZMYND8
CEBPa ZEB2
MYB
MAX MEF2C LYL1
LMO2
IKZF1 FLI1 ELF2 GFI1 MEIS1

## RNPv2:

### others 

Promoters: were selected from https://epd.epfl.ch/get_promoters.php
slamseq paper:
ATACseq: https://www.ncbi.nlm.nih.gov/sra?term=SRX5608489
depmap:
known enhancer: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5467550/
adjacency:
ABC assignements:
superenhancer matrix:
Fish SuperRes: gs://amlproject/super_res/

#### Motifs:

name  | types 
----------------
BRD4  | x
CDK13 | x
CDK6  | x
CEBPA | MEME
ELF2  | MEME
ETV6  | MEME
FLI1  | DeepBind, MEME
FOXP1 | MEME
GATA2 | MEME
GFI1  | MEME
IKZF1 | DeepBind, MEME
IRF2BP2 | x
IRF8  | DeepBind, MEME
LDB1  | 
LMO2  | x
LYL1  | MEME
MAX | DeepBind, MEME
MEF2C | DeepBind, MEME
MEF2D | DeepBind, MEME
MEIS1 | DeepBind, MEME
MYB | DeepBind, MEME
MYBL2 | MEME
MYC | DeepBind, MEME
RUNX1 | MEME
RUNX2 | DeepBind, MEME
SPI1  | DeepBind, MEME
SP1 | MEME
ZEB2  |
ZMYND8  |


### For data access:


### Map for the amlproject bucket (gs://amlproject)
_to get access to this folder you need to ask jeremie kalfon jkobject@gmail.com _

__you can find how to access this easily [here](https://cloud.google.com/storage/docs/gsutil_install) (you need to be okay with command line) Else you can copy and paste this url https://console.cloud.google.com/storage/browser/<bucketname> and replace the bucket name with the current bucket__

- RNA
  - IRF2BP2: fastqs for the project
  - RNP: fastqs for the project
- Chip
  - IRF2BP2\_degraded\_rep1
    - bwa/MergedLibrary library-level, coordinate sorted \*.bam files after the marking of duplicates, and filtering based on various criteria. The file suffix for the final filtered files will be \*.mLb.clN.\*. 
      - samtools\_stats/ SAMtools 
        - \*.flagstat, 
        - \*.idxstats and 
        - \*.stats files generated from the alignment files.
      - picard\_metrics/ Alignment QC files from picard CollectMultipleMetrics and the metrics file from MarkDuplicates: 
        - \*\_metrics and 
        - \*.metrics.txt, respectively.
        - pdf/ Alignment QC plot files in \*.pdf format from picard CollectMultipleMetrics.
      - preseq/ Preseq expected future yield file (\*.curve.txt).
      - bigwigs Normalised \*.bigWig files scaled to 1 million mapped reads.
      - macs/<PEAK\_TYPE>/ MACS2 output files: 
        - \*.xls, 
        - \*.broadPeak or \*.narrowPeak, 
        - \*.gappedPeak and 
        - \*summits.bed. The files generated will depend on whether MACS2 has been run in narrowPeak or broadPeak mode. HOMER peak-to-gene annotation file: 
        - \*.annotatePeaks.txt.
        - qc/ QC plots for MACS2 peaks: macs\_peak.plots.pdf QC plots for peak-to-gene feature annotation: macs\_annotatePeaks.plots.pdf MultiQC custom-content files for FRiP score, peak count and peak-to-gene ratios: 
          - \*.FRiP\_mqc.tsv, 
          - \*.count\_mqc.tsv and 
          - macs\_annotatePeaks.summary\_mqc.tsv respectively.
        - consensus/ Consensus peak-set across all samples in 
          - \*.bed format. Consensus peak-set across all samples in 
          - \*.saf format. Required by featureCounts for read quantification. HOMER 
          - \*.annotatePeaks.txt peak-to-gene annotation file for consensus peaks. Spreadsheet representation of consensus peak-set across samples with gene annotation columns: 
          - \*.boolean.annotatePeaks.txt. The columns from individual peak files are included in this file along with the ability to filter peaks based on their presence or absence in multiple replicates/conditions. Spreadsheet representation of consensus peak-set across samples without gene annotation columns: 
          - \*.boolean.txt. Same as file above but without annotation columns. UpSetR files to illustrate peak intersection: 
          - \*.boolean.intersect.plot.pdf and 
          - \*.boolean.intersect.txt.
          - <ANTIBODY>/deseq2/ 
            - .featureCounts.txt file for read counts across all samples relative to consensus peak-set. Differential binding 
            - \*.results.txt spreadsheet containing results across all consensus peaks and all comparisons. 
            - \*.plots.pdf file for PCA and hierarchical clustering. 
            - \*.log file with information for number of differentially bound intervals at different FDR and fold-change thresholds for each comparison. 
            - \*.dds.rld.RData file containing R dds and rld objects generated by DESeq2. R\_sessionInfo.log file containing information about R, the OS and attached or loaded packages.
          - <ANTIBODY>/<COMPARISON>/ 
            - \*.results.txt spreadsheet containing comparison-specific DESeq2 output for differential binding results across all peaks. Subset of above file for peaks that pass FDR <= 0.01 (\*FDR0.01.results.txt) and FDR <= 0.05 (\*FDR0.05.results.txt). BED files for peaks that pass FDR <= 0.01 (\*FDR0.01.results.bed) and FDR <= 0.05 (\*FDR0.05.results.bed). MA, Volcano, clustering and scatterplots at FDR <= 0.01 and FDR <= 0.05: 
            - \*deseq2.plots.pdf.
          - <ANTIBODY>/sizeFactors/ Files containing DESeq2 sizeFactors per sample: 
            - \*.txt and 
            - \*.RData. 
      - phantompeakqualtools Output files: 
        - \*.spp.out, 
        - \*.spp.pdf. MultiQC custom content files: 
        - \*\_spp\_correlation\_mqc.tsv, 
        - \*\_spp\_nsc\_mqc.tsv, 
        - \*\_spp\_rsc\_mqc.tsv.
      - deepTools
        - plotFingerprint Output files: 
          - \*.plotFingerprint.pdf, 
          - \*.plotFingerprint.qcmetrics.txt, 
          - \*.plotFingerprint.raw.txt
        - plotProfile Output files: 
          - \*.computeMatrix.mat.gz, 
            - \*.computeMatrix.vals.mat.gz, 
            - \*.plotProfile.pdf, 
            - \*.plotProfile.tab.
    - droso\_aligned reads mapped to the reference drosophilia genome
    - recalib\_bigwig spikedIn control bigwigs
    - fastqs initial fastq files received (renamed)
    - fastqc/ FastQC \*.html files for read 1 (and read2 if paired-end) before adapter trimming.
      - zips/ FastQC \*.zip files for read 1 (and read2 if paired-end) before adapter trimming.
    - igv/<PEAK\_TYPE>/ igv\_session.xml file. igv\_files.txt file containing a listing of the files used to create the IGV session, and their allocated colours.
    - multiqc/<PEAK\_TYPE>/ multiqc\_report.html - a standalone HTML file that can be viewed in your web browser.
      - multiqc\_data/ - directory containing parsed statistics from the different tools used in the pipeline.
      - multiqc\_plots/ - directory containing static images from the report in various formats.
    - pipeline\_info
    - reference\_genome A number of genome-specific files are generated by the pipeline in order to aid in the filtering of the data, and because they are required by standard tools such as BEDTools. These can be found in this directory along with the genome fasta file which is required by IGV.
    - trim\_galore/ FastQ files after adapter trimming will be placed in this directory.
      - logs/ \*.log files generated by Trim Galore!.
      - fastqc/ FastQC \*.html files for read 1 (and read2 if paired-end) after adapter trimming.
        - /zips/ FastQC \*.zip files for read 1 (and read2 if paired-end) after adapter trimming.
    - pipeline\_info/ Reports generated by the pipeline - pipeline\_report.html, pipeline\_report.txt and software\_versions.csv. Reports generated by Nextflow - execution\_report.html, execution\_timeline.html, execution\_trace.txt and pipeline\_dag.svg. Reformatted design files used as input to the pipeline - design\_reads.csv and design\_controls.csv.
    - Documentation/ Documentation for interpretation of results in HTML format - results\_description.html.
  - IRF2BP2\_degraded\_rep2
    - \*\*
  - IRF2BP2\_degraded\_hist
    - \*\*

## Code

terra's RNAseq pipeline:
nextflow's ChIPseq:
nextflow's ATACseq:

### Code additionals: 

JKBio: 

	JKBio's epigenetics/ChIP_helper.py:


and ccle_processing:


### AMLproject code:


notebooks/
  [PROJECT].ipynb
  
html_notebooks/
  [PROJECT]\_v[X].html

data/
  [PROJECT]/
    subfolders/
      data
    data

results/     <- saved into google drive (link: )
  [PROJECT]/
    plots/
      [PLOT_NAME]\_[changetype]\_v[X].png|pdf|html <- each pdfHTML plot needs to have a corresponding png|pdf
    data/
      [Name]\_[changetype]\_v[X].[...]



#### subproject

- Cell lines WGS analysis


- ChIP_analysis:
  - v1:
  - v2:

- creating_intervals_CRISPRtargets

- DeepBind_Analysis

- Fish_SuperRes

- IRF2BP2 ChIPs Analysis

- JQ1_RNA_analysis:
  - v1
  - v2

- JQ1_slamRNA_analysis
  - v1

- processing ChipSeq

- Processing_IRF2BP2_degraded_MV411

- RNA_RNP_analysis
  - v1
  - v2
  - v2_scaled

- RNA-AMLproject

- running OPTICS

- slamseq IRF2BP2 degraded
  - v1
  - v2

- slamseq_MYCpaper
  - v2_K562
  - v2_MOLM13


#### important data


#### important results


#### source codes

- ROSE:
- ROSEv2:
- ChromHMM:
- Ken's code:
	- code for the ABC mapping
	- code for the inference of CRC members from RNAseq
- Moe's code
	- code for the plots
	- code for the cell line/tumors relationship
- Code to create the super enhancer matrix
- Andrew's code
	- Andrew's presentation
- Neekesh's code to create the first CRC list


## TODO:

- packages for ccle_processing
- packages for JKBio
- packages for AMLproject
- add Ken's code to AMLproject