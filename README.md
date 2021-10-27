# hse21_hw1

    seqtk sample -s613 oil_R1.fastq 5000000 > sub1.fastq
    8  seqtk sample -s613 oil_R2.fastq 5000000 > sub2.fastq
    9  seqtk sample -s613 oilMP_S4_L001_R1_001.fastq > sub1MP.fastq
    10  seqtk sample -s613 oilMP_S4_L001_R1_001.fastq 1500000 > sub1MP.fastq
     11  seqtk sample -s613 oilMP_S4_L001_R2_001.fastq 1500000 > sub1MP.fastq
     12  rm sub1MP.fastq
     13  seqtk sample -s613 oilMP_S4_L001_R1_001.fastq 1500000 > sub1MP.fastq
     14  seqtk sample -s613 oilMP_S4_L001_R2_001.fastq 1500000 > sub2MP.fastq
     16  mkdir quality
     17  fastqc oil_R1.fastq oil_R2.fastq oilMP_S4_L001_R1_001.fastq oilMP_S4_L001_R2_001.fastq
     19  mv oilMP_S4_L001_R1_001_fastqc.html quality/
     20  mv oilMP_S4_L001_R1_001_fastqc.zip quality/
     21  mv oilMP_S4_L001_R2_001_fastqc.zip quality/
     22  mv oilMP_S4_L001_R2_001_fastqc.html quality/
     23  mv oil_R1_fastqc.html quality/
     24  mv oil_R2_fastqc.html quality/
     25  mv oil_R1_fastqc.zip quality/
     26  mv oil_R2_fastqc.zip quality/
     30  fastqc sub1.fastq sub2.fastq sub1MP.fastq sub2MP.fastq
     31  ls
     32  fastqc sub1.fastq sub2.fastq sub1MP.fastq sub2MP.fastq -o quality/
     33  ls
     34  ls quality/
     35  clear
     36  ls
     37  cd hw1/
     38  ls
     39  platanus_trim sub1.fastq sub2.fastq
     40  platanus_trim sub1MP.fastq sub2MP.fastq
     41  platanus_trim sub1.fastq.trimmed sub2.fastq.trimmed
     42  platanus_internal_trim sub1.fastq.trimmed sub2.fastq.trimmed
     43  platanus_internal_trim sub1MP.fastq.trimmed sub2MP.fastq.trimmed
     44  mkdir quality1
     45  fastqc sub1.fastq.trimmed.int_trimmed sub2.fastq.trimmed.int_trimmed sub1MP.fastq.trimmed.int_trimmed sub2MP.fastq.trimmed.int_trimmed -o quality/
     46  fastqc sub1.fastq.trimmed.int_trimmed sub2.fastq.trimmed.int_trimmed sub1MP.fastq.trimmed.int_trimmed sub2MP.fastq.trimmed.int_trimmed -o quality1/
     47  cd quality1/
     48  multiqc .
     49  man platanus assemble
     50  platanus assemble -h
     51  cd ..
     52  mkdir contigs
     53  platanus assemble -f sub1.fastq.trimmed.int_trimmed sub2.fastq.trimmed.int_trimmed > assemble.llog
     54  mv assemble.llog assemble.log 
     55  platanus assemble -f sub1MP.fastq.trimmed.int_trimmed sub2MP.fastq.trimmed.int_trimmed > assemble.log
     56  platanus assemble -f sub1.fastq.trimmed sub2.fastq.trimmed > assemble.log
     57  platanus_internal_trim sub1MP.fastq sub2MP.fastq
     58  rm quality1/*
     59  rm -r quality1/*
     60  fastqc sub1.fastq.trimmed sub2.fastq.trimmed sub1MP.fastq.int_trimmed sub2MP.fastq.int_trimmed -o quality1/
     61  platanus assemble -f sub1.fastq.trimmed sub2.fastq.trimmed sub1MP.fastq.int_trimmed sub2MP.fastq.int_trimmed > assemble.log
     62  ls
     63  ls contigs/
     64  cd quality1/
     65  ls
     66  multiqc .
     67  cd ..
     68  cd hw1/
     69  platanus scaffold -c out_contig.fa -IP1 sub1.fastq.trimmed sub2.fastq.trimmed -OP2 sub1MP.fastq.int_trimmed sub2MP.fastq.int_trimmed
