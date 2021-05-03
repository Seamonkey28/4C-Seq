# 4C-Seq method using 4Cker

#Primer Trimming
Paired-end reads containing the primary restriction enzyme were treated as single-end data and were trimmed up to and including the RE sequence using cutadapt. Only reads with a minimum length of 30bp and minimum quality score of 30 were kept for further downstream analysis. Reads were also trimmed from the 3' end to 70bp to maximise mapping efficiency. 

Using R254 VP as an example

![Screen Shot 2021-05-04 at 12 22 43 AM](https://user-images.githubusercontent.com/69442178/116875343-daabbc00-ac6e-11eb-8f9a-e4d680b5defd.png)



