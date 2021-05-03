# 4C-Seq method using 4Cker

![Screen Shot 2021-05-04 at 1 02 42 AM](https://user-images.githubusercontent.com/69442178/116879176-6f64e880-ac74-11eb-8ebf-b8b4bf192ef8.png)


**To increase the number of reads two sequencing runs were performed (NZGL01087 and NZGL01900)
**Demultiplexing and adapator trimming was also performed by the NZGL bioinformatians in 2015

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

The reduced genome file GCA_000001405.15_GRCh38_no_alt_analysis_set_dpnii_flanking_sequences_70_unique.fa was then used as an index for bowtie2

![Screen Shot 2021-05-04 at 12 43 34 AM](https://user-images.githubusercontent.com/69442178/116877222-c4532f80-ac71-11eb-8a82-4be253ca04ac.png)

#Mapping reads to reduced genome

![Screen Shot 2021-05-04 at 12 49 03 AM](https://user-images.githubusercontent.com/69442178/116877801-886c9a00-ac72-11eb-9088-cf9ae97ba74c.png)

#Creating a counts file from the output sam file
The number of reads per fragment generated bedGraph files created using the 4Cker script sam_bedGraph.sh

#Remove self-ligated and undigested fragments.
To remove the self-ligated and undigested fragments
-find the coordinates based on the primer sequence in the Genome file (Watson strand regardless of primer strand and not including the RE sequence).
Using R254 VP as an example:
Use reverse complement (RC) of rev primer for DpnII: 

![Screen Shot 2021-05-04 at 12 56 20 AM](https://user-images.githubusercontent.com/69442178/116878498-8e16af80-ac73-11eb-81e5-37e561968a01.png)

Find fragments overlapping the R254 reverse primer 

![Screen Shot 2021-05-04 at 12 59 43 AM](https://user-images.githubusercontent.com/69442178/116878871-0d0be800-ac74-11eb-9cbd-3ecd8849d559.png)

This did not return any overlapping fragments

#Remove reads in unligated control file
![Screen Shot 2021-05-04 at 1 04 30 AM](https://user-images.githubusercontent.com/69442178/116879360-b0f59380-ac74-11eb-9bc8-7c9be1c66652.png)

#Remove reads 10kb +/- of the bait (not entirely sure this step worked!)
![Screen Shot 2021-05-04 at 1 06 42 AM](https://user-images.githubusercontent.com/69442178/116879637-fe720080-ac74-11eb-85bc-3d5c752e9765.png)

#Analyse 4C interactions 
4Cker object was created as described using https://github.com/rr1859/R.4Cker






