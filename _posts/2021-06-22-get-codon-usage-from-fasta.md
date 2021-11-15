---

layout: post
tag: python-script
title: "Get codon usage from FASTA"
---

- Build-in codon usage utility from Biopython gives an unsorted list of all codons
- This script prints out a codon usage list sorted by amino acids

<!--more-->

## (input) IBV.fasta

```
>IBV-ORF1ab
ATGGCTTCAAGCCTAAAACAGGGAGTATCTCCCAAACCACGGGATGTCATTCTT...TAG
>IBV-S
ATGTTGGTAACACCTCTTTTACTAGTGACTCTTTTGTGTGCACTATGTAGTGCT...TGA
>IBV-E
ATGAATTTATTGAATAAGTCGCTAGAGGAGAATGGAAGTTTTCTAACAGCGCTT...TGA
>IBV-M
ATGCCCAACGAGACAAATTGTACTCTTGACTTTGAACAGTCAGTTCAGCTTTTT...TAA
>IBV-N
ATGGCAAGCGGTAAAGCAGCTGGAAAAACAGACGCCCCAGCGCCAGTCATTAAA...TGA
```

## Built-in codon usage method in Biopython


```python
from Bio.Seq import Seq
from Bio.SeqUtils import CodonUsage

CAI = CodonUsage.CodonAdaptationIndex()
CAI.generate_index("IBV.fasta")
CAI.print_index()
```

    AAA	1.000
    AAC	0.317
    AAG	0.982
    AAT	1.000
    ACA	0.843
    ACC	0.166
    ACG	0.149
    ACT	1.000
    AGA	1.000
    AGC	0.207
    AGG	0.436
    AGT	0.838
    ATA	0.742
    ATC	0.167
    ATG	1.000
    ATT	1.000
    CAA	1.000
    CAC	0.447
    CAG	0.644
    CAT	1.000
    CCA	0.985
    CCC	0.219
    CCG	0.204
    CCT	1.000
    CGA	0.168
    CGC	0.386
    CGG	0.099
    CGT	0.832
    CTA	0.356
    CTC	0.201
    CTG	0.251
    CTT	1.000
    GAA	1.000
    GAC	0.420
    GAG	0.665
    GAT	1.000
    GCA	0.824
    GCC	0.202
    GCG	0.160
    GCT	1.000
    GGA	0.339
    GGC	0.248
    GGG	0.078
    GGT	1.000
    GTA	0.437
    GTC	0.218
    GTG	0.350
    GTT	1.000
    TAA	0.333
    TAC	0.370
    TAG	0.333
    TAT	1.000
    TCA	0.606
    TCC	0.096
    TCG	0.141
    TCT	1.000
    TGA	1.000
    TGC	0.229
    TGG	1.000
    TGT	1.000
    TTA	0.726
    TTC	0.269
    TTG	0.758
    TTT	1.000
    

## My script


```python
from collections import Counter
from Bio.Seq import Seq
from Bio import SeqIO

### take amino acid single letter as argument
### return a list of codons
### for example, take "*"
### return ["TGA", "TAG", "TAA"]
def from_aa_get_codon_list(aa):
    codon_list = []
    genetic_table_dic = {\
    'ATA':'I', 'ATC':'I', 'ATT':'I', 'ATG':'M', 
    'ACA':'T', 'ACC':'T', 'ACG':'T', 'ACT':'T', 
    'AAC':'N', 'AAT':'N', 'AAA':'K', 'AAG':'K', 
    'AGC':'S', 'AGT':'S', 'AGA':'R', 'AGG':'R', 
    'CTA':'L', 'CTC':'L', 'CTG':'L', 'CTT':'L', 
    'CCA':'P', 'CCC':'P', 'CCG':'P', 'CCT':'P', 
    'CAC':'H', 'CAT':'H', 'CAA':'Q', 'CAG':'Q', 
    'CGA':'R', 'CGC':'R', 'CGG':'R', 'CGT':'R', 
    'GTA':'V', 'GTC':'V', 'GTG':'V', 'GTT':'V', 
    'GCA':'A', 'GCC':'A', 'GCG':'A', 'GCT':'A', 
    'GAC':'D', 'GAT':'D', 'GAA':'E', 'GAG':'E', 
    'GGA':'G', 'GGC':'G', 'GGG':'G', 'GGT':'G', 
    'TCA':'S', 'TCC':'S', 'TCG':'S', 'TCT':'S', 
    'TTC':'F', 'TTT':'F', 'TTA':'L', 'TTG':'L', 
    'TAC':'Y', 'TAT':'Y', 'TAA':'*', 'TAG':'*', 
    'TGC':'C', 'TGT':'C', 'TGA':'*', 'TGG':'W',}
    for k,v in genetic_table_dic.items():
        if v == aa:
            codon_list.append(k)
    return codon_list
###



### take *.fasta file as input
### return codon count and amino acid count
def codon_aa_count(fasta_file):
    codon_list = []
    aa_list = []
    for record in SeqIO.parse(fasta_file, "fasta"):
        for i in range(0, len(record.seq), 3):
            codon = record.seq[i:i + 3]
            codon_list.append(str(codon))
            aa = codon.translate()
            aa_list.append(str(aa))
    codon_count = Counter(codon_list)
    aa_count = Counter(aa_list)
    return [codon_count, aa_count]
###



### take codon_aa_count as argument
### print codon usage for all amino acids
def print_all_codon_usage(codon_aa_count):
    codon_count = codon_aa_count[0]
    aa_count = codon_aa_count[1]
    for aa in aa_count:
        print (f"{aa}:", end="   ")
        for codon in from_aa_get_codon_list(aa):
            codon_usage_f = codon_count[codon]/aa_count[aa]
            print (f"{codon} {codon_usage_f:.3f} ", end="  ")
        print ()
###



### take an amino acid single letter code, codon_count, aa_count
### return the codon usage for that amino acid
def print_codon_usage_for_aa(aa, codon_aa_count):
    codon_count = codon_aa_count[0]
    aa_count = codon_aa_count[1]
    print (f"{aa}:", end="   ")
    for codon in from_aa_get_codon_list(aa):
        codon_usage_f = codon_count[codon]/aa_count[aa]
        print (f"{codon} {codon_usage_f:.3f} ", end="  ")
    print ()
###



## core script
codon_aa_count = codon_aa_count("IBV.fasta")

print_codon_usage_for_aa("V", codon_aa_count)
print_codon_usage_for_aa("R", codon_aa_count)
print ("="*75)
print_all_codon_usage(codon_aa_count)
```

    V:   GTA 0.218   GTC 0.109   GTG 0.175   GTT 0.499   
    R:   AGA 0.342   AGG 0.149   CGA 0.058   CGC 0.132   CGG 0.034   CGT 0.285   
    ===========================================================================
    M:   ATG 1.000   
    A:   GCA 0.377   GCC 0.092   GCG 0.073   GCT 0.457   
    S:   AGC 0.072   AGT 0.290   TCA 0.210   TCC 0.033   TCG 0.049   TCT 0.346   
    L:   CTA 0.108   CTC 0.061   CTG 0.076   CTT 0.304   TTA 0.221   TTG 0.230   
    K:   AAA 0.505   AAG 0.495   
    Q:   CAA 0.608   CAG 0.392   
    G:   GGA 0.203   GGC 0.149   GGG 0.047   GGT 0.601   
    V:   GTA 0.218   GTC 0.109   GTG 0.175   GTT 0.499   
    P:   CCA 0.409   CCC 0.091   CCG 0.085   CCT 0.415   
    R:   AGA 0.342   AGG 0.149   CGA 0.058   CGC 0.132   CGG 0.034   CGT 0.285   
    D:   GAC 0.296   GAT 0.704   
    I:   ATA 0.389   ATC 0.088   ATT 0.524   
    E:   GAA 0.601   GAG 0.399   
    C:   TGC 0.186   TGT 0.814   
    F:   TTC 0.212   TTT 0.788   
    Y:   TAC 0.270   TAT 0.730   
    T:   ACA 0.391   ACC 0.077   ACG 0.069   ACT 0.464   
    H:   CAC 0.309   CAT 0.691   
    N:   AAC 0.241   AAT 0.759   
    W:   TGG 1.000   
    *:   TAA 0.200   TAG 0.200   TGA 0.600   
    
