# 4C-Seq method using 4Cker

#Primer Trimming
Paired-end reads containing the primary restriction enzyme were treated as single-end data and were trimmed up to and including the RE sequence using cutadapt. Only reads with a minimum length of 30bp and minimum quality score of 30 were kept for further downstream analysis. Reads were also trimmed from the 3' end to 70bp to maximise mapping efficiency. 

Using R254 VP as an example

![Screen Shot 2021-05-04 at 12 22 43 AM](https://user-images.githubusercontent.com/69442178/116875343-daabbc00-ac6e-11eb-8f9a-e4d680b5defd.png)

#Concatenating files
Primer trimmed sequence reads from the two different sequencing runs (1087 and 1900) were concatenated to give a single fastq file.

#Creating a reduced genome
Restriction enzyme digest of the human genome was performed using an adapted version of the 4Cker reduced_genome.sh script 
Input files included, primary restriction enzyme file, hg38 genome and a fragment size of 70 was defined.
-p dpnii.fa
-g Ch38 reference genome file from O'Sullivan lab: GCA_000001405.15_GRCh38_no_alt_analysis_set.fa
-f 70

![Screen Shot 2021-05-04 at 12 37 14 AM](https://user-images.githubusercontent.com/69442178/116876632-e00a0600-ac70-11eb-8314-6e2aa6170310.png)






