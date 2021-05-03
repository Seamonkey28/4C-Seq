# 4C-Seq method using 4Cker

#Primer Trimming
Paired-end reads containing the primary restriction enzyme were treated as single-end data and were trimmed up to and including the RE sequence using cutadapt. Only reads with a minimum length of 30bp and minimum quality score of 30 were kept for further downstream analysis. Reads were also trimmed from the 3' end to 70bp to maximise mapping efficiency. 


