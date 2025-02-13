# Truffula
Jupyter notebooks for the analysis of data associated with the maize Truffula mutant 

These jupyter notebooks contain all of the bash, R, and Python code used to anlayse data associated with the paper "Dominant mutants reveal a conserved method of class-B ARF regulation in land plants revealing a ~500myo piece of the auxin signalling puzzle" 
Authors: Michael J. Prigge1, Nicholas Morffy2, Amber de Neve3,4, Whitnie Szutu1, Jazmín Abraham Juárez5, Kjel Johnson3,4, Nicole Do1, Meirav Lavy1, Sarah Hake3,4, Lucia Strader*2, Mark Estelle*1, Annis E. Richardson*3,4,6§
(1) UCSD
(2) Duke University
(3) USDA Plant Gene Expression Center, 800 Buchanan Street, Albany, CA 94710. 
(4) Department of Plant and Microbial Biology, University of California Berkeley, CA. 
(5) Jazmin’s address
(6) Institute of Molecular Plant Sciences, School of Biological Sciences, University of Edinburgh, Edinburgh, UK. 
*Co-corresponding Authors
§ current location

Truffula is a dominant, EMS-induced maize mutant. The phenotype was assessed in both the original Mo17, and W22 backcross (10 generations) inbred backgrounds. 

_Materials and Methods_
_Maize plants_
The Truffula seed was provided by Gerry Neuffer, and originally called Ts-2620, found in an EMS mutagenized Mo17 population. The phenotype of Trf was analyzed in backcrosses into W22 and Mo17 advanced to generation 10. Field grown plants were grown at UC Berkeley Gill Tract, UC Davis and UMass Amherst during summer field seasons. All plants used for molecular analysis were backcrossed into W22 10 times. Seedlings grown for RNA and DNA extractions were grown under greenhouse conditions in 30×45×2.5cm trays with peat free soils plus osmocote. Seedlings grown for auxin treatment tests and western blots were grown in temperature-controlled greenhouses with supplemental light in 30×45×2.5cm trays with peat-reduced osmocote compost with added fertilizer under 16hr 25°C/8hr 21°C day/ night cycle. 

_DNA Extraction_ 
Leaf discs were collected from 80 Trf and N siblings in the W22 backcross population (at least10 introgressions). High-quality gDNA was extracted using urea as described previously(59). In brief, genomic DNA was extracted using a urea-based extraction method which is as follows. Tissue was ground in urea extraction buffer (4M urea, 4M NaCl, 1M Tris pH8, 0.5M EDTA, 34mM n-lauroyl sarcosine). Then an equal volume of phenol:chloroform:isoamyl alcohol (25:24:1), was added and vortexed to mix. After centrifugation, the supernatant was decanted and mixed with an equal volume of chloroform. After centrifugation, the supernatant was decanted and mixed with 1/10th volume of 4.4 M NH4OAc pH 5.2 and 0.7 volume of isopropanol. Strands of DNA were then collected and washed with 70% ethanol in a separate tube. The dried pellet was resuspended in 100µl of TE. DNA integrity was checked using gel electrophoresis and quantified using qubit before sending for library preparation and 150bp PE sequencing by Novogene. Sequencing was for 10 × coverage of the maize genome. DNA for SSR mapping and genotyping was extracted from 1.5cm of leaf tissue using the protocol described previously(60). 

_Whole-Genome Sequencing Bulk-segregant Analysis_
Sequence data was downloaded via ftp from Novogene servers and passed through the following analysis pipeline: FASTPQ(61)> Bowtie2(62) alignment to the B73_Reference_Nam5.0 genome > samtools mpileup variant calling(63) > SNPeff (42) and variant filtering in R, restricting to EMS type SNPs. Jupyter notebooks containing the code for WGS-BSA analysis is available at: https://github.com/ThePlantShapeLab

_Auxin Treatment of Maize_
A segregating population of 5-week-old Trf siblings was genotyped using primers AD_4 and AD_5. Plants were cut at the root-shoot node and submerged in either 100µm Indole-3-Acetic Acid (Sigma I5148) in 1% ethanol, or 1% ethanol only, ensuring that at least 10cm of the shoot base was completely submerged. Shoot apices were harvested (~1cm encompassing the base of the meristem and young leaf tissue, outer leaf removed), dried briefly, and flash frozen in liquid nitrogen at 0 minutes and 30 minutes. 2 replicate pools for each treatment and genotype group were collected, containing 3 individuals in each pool. 

_Maize RNA Extraction_
For the Trf versus normal (N) sibling RNAseq experiment, a segregating population of 3-week-old maize seedlings were first genotyped for Trf (see Table S1 for primers). The outer 2 leaves were removed and 0.5cm of the shoot apex was dissected and flash frozen in liquid nitrogen. Three replicate pools were created for Trf and N siblings, 10 individuals per pool. For the auxin treatment of Trf versus N siblings tissue was for above. RNA for all experiments was extracted from each pool using TRIzol® (Invitrogen) as described in the manual. RNA was DNAse treated to remove gDNA contamination using Invitrogen DNaseI (#18068015) digestion. RNA quality was checked using gel electrophoresis (1x Agarose in 1x TBE) and quantified using Qubit before sending for library preparation and 150bp PE sequencing by Novogene, or generating cDNA libraries using the iScript gDNA clear cDNA synthesis kit (Bio-Rad). 

_RNAseq Analysis_
Sequence data was downloaded via ftp from Novogene servers and passed through the following analysis pipeline: FASTPQ(61) > HiSAT2(64) alignment to the Zea mays Reference NAM5.0 genome > FeatureCounts(65) > DeSeq2(66) analysis of differential gene expression using genes with more than 5 counts in 3 or more samples. All analysis was carried out locally (3.6GHz 8-Core Intel Core i9 processor, 32GB RAM) using R packages combined with Jupyter notebooks. Jupyter notebooks containing the code for RNAseq analysis are available at:       https://github.com/ThePlantShapeLab GO term analysis was carried out using the GAMER Maize annotations(67) and the GOSeq R package(68), significantly enriched GO terms had a Benjamini and Hochberg cutoff padj value of <0.05.

_References_

42. 	P. Cingolani, A. Platts, L. L. Wang, M. Coon, T. Nguyen, L. Wang, S. J. Land, X. Lu, D. M. Ruden, A program for annotating and predicting the effects of single nucleotide polymorphisms, SnpEff: SNPs in the genome of Drosophila melanogaster strain w1118; iso-2; iso-3. Fly (Austin) 6, 80–92 (2012).
59. 	J. Chen, S. Dellaporta, “Urea-based plant DNA miniprep” in The Maize Handbook (Springer, 1994), pp. 526–527.
60. 	C. Lunde, Small-scale DNA Extraction Method for Maize and Other Plants. Bio Protoc 8 (2018).
61. 	S. Chen, Y. Zhou, Y. Chen, J. Gu, Fastp: An ultra-fast all-in-one FASTQ preprocessor. Fastp: An ultra-fast all-in-one FASTQ preprocessor, doi: 10.1101/274100 (2018).
62. 	B. Langmead, S. L. Salzberg, Fast gapped-read alignment with Bowtie 2. Nat Methods 9, 357–359 (2012).
63. 	P. Danecek, J. K. Bonfield, J. Liddle, J. Marshall, V. Ohan, M. O. Pollard, A. Whitwham, T. Keane, S. A. McCarthy, R. M. Davies, H. Li, Twelve years of SAMtools and BCFtools. Gigascience 10, giab008 (2021).
64. 	D. Kim, J. M. Paggi, C. Park, C. Bennett, S. L. Salzberg, Graph-based genome alignment and genotyping with HISAT2 and HISAT-genotype. Nat Biotechnol, doi: 10.1038/s41587-019-0201-4 (2019).
65. 	Y. Liao, G. K. Smyth, W. Shi, FeatureCounts: An efficient general purpose program for assigning sequence reads to genomic features. Bioinformatics, doi: 10.1093/bioinformatics/btt656 (2014).
66. 	M. I. Love, W. Huber, S. Anders, Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. Genome Biol, doi: 10.1186/s13059-014-0550-8 (2014).
67. 	K. Wimalanathan, I. Friedberg, C. M. Andorf, C. J. Lawrence-Dill, Maize GO Annotation—Methods, Evaluation, and Review (maize-GAMER). Plant Direct, doi: 10.1002/pld3.52 (2018).
68. 	M. D. Young, M. J. Wakefield, G. K. Smyth, A. Oshlack, Gene ontology analysis for RNA-seq: accounting for selection bias. Genome Biol, doi: 10.1186/gb-2010-11-2-r14 (2010).



_Specific files_

RNAseq Analysis Jupyter notebooks: 
- Trf TRF_VegetativeShoot_Apex_RNAseq_BashCode_Alignments_2022.ipynb
- Trf_DE_analysis_NAM5alignment_April2022_CleanForGitHub.ipynb

WGS Analysis Jupyter notebooks:
- TRF_WGS_NAM5_alignment_BashCode_202
- Trf_WGS_NAM5_alignment_R_code.ipynb
- Trf_WGS_PyVCF_code.ipynb
- Trf_WGS_SnpEff_Bash_code.ipynb

General Data Analysis:
- Trf_Phenotype_and_ARFB_stability_DataAnalysis



