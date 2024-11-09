# Matrix eQTL Tutorial
### Matrix eQTL allows for analysis of associations between variants (SNPs) within the genome with gene expression levels, known as expression quanitiative trait loci (eQTLs)
- Uses matrix operations to process multiple SNP-gene pairs in parallel, known as sliced data processing
- Is able to perform ultra-fast eQTL analysis without loss of precision
- Can incorporate covariates, false discovery rate (FDR) correction, and separate cis vs trans eQTLs
- Supports multiple models of genotype-covariate interactions, including linear additive and ANOVA
- Is included in the CRAN Repository, allowing for quick and easy installation

#### Performance comparison to other methods when 10 covariates included in analysis:
Plink: 583.3 days \
R/qtl: 4.7 days \
Matrix eQTL: <20 minutes

#### Getting Started
00getting_started.Rmd includes the basic code needed to install and run Matrix eQTL, including comments describing the function of code, and uses the sample dataset files included with the Matrix eQTL package as a tutorial for identifing eQTLs.

*Minimum necessary files to execute analysis must be in delineated .txt files and include SNP data associated with sample IDs showing allele frequencies (snp_file), gene IDs associated with sample IDs showing gene expression levels (expression_file), and sample IDs with covariates if necessary (covariate_file)*

#### Cis and Trans eQTLs
01cis_trans_eqtl.Rmd includes additional code needed to distinguish local/cis eQTLs from distant/trans eQTLs

Cis-eQTLs are typically defined as loci that are within 1000000 (1e-6) base pairs in either direction of the associated SNP. Trans-QTLs are loci located further away from the SNP, encompacing everything that does not fall within the cis-eQTL range.

- This value can be changed by setting the variable 'cisDist' equal to any numeric value

Cis- and trans-eQTL distinction requires two additional files for analysis, one of gene IDs associated with their respective locations within the genome, and one of SNP locations within the genome

P-value thresholds can differ between cis- and trans-eQTLs by setting 'pvOutputThreshold_cis' and 'pvOutputThreshold_trans' to their respective values

- It is recommended for larger datasets to use more stringent p-values to increase statistical power

#### Histograms and QQplots
02plotting.Rmd includes code that enables histogram and QQplots to be generated using the Matrix eQTL package as well as features of the plots to look at in order to support or detect possible inflation in the results.

**Notes:** \
The Matrix_eQTL_engine function is a fast and simple way to perform eQTL analysis if SNP and gene locations are not included with the input files \
The Matrix_eQTL_main function is more flexible and allows for more complex analyses that include SNP and gene locations, like those needed to identify cis- and trans-eQTLs

Citation for all included data and R package MatrixEQTL: Shabalin, A.A. Matrix eQTL: Ultra fast eQTL analysis via large matrix operations. Bioinformatics 28, no. 10 (2012): 1353-1358.
