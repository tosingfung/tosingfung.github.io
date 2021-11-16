---

layout: post
tag: python-learn
title: "Biopython Basic seq operations"
---



## comp and rev_comp


```python
from Bio.Seq import Seq
dna = Seq("AGGGCCCTTTA")
print (dna[::-1]) # reverse
print (dna.complement())
print (dna.reverse_complement())
```

    ATTTCCCGGGA
    TCCCGGGAAAT
    TAAAGGGCCCT


## parse fasta file


```python
from Bio import SeqIO
for record in SeqIO.parse("ibv.fasta","fasta"):
    print(record.id)
    print(len(record.seq))
    print(repr(record.seq))
```

    DQ001339.1
    27611
    Seq('ACTTAAGATAGATATTAATATATATCTATTATACTAGCCTTGCGCTAGATTTTT...GCA')


## parse genbank file


```python
from Bio import SeqIO
for record in SeqIO.parse("sars2.gb","genbank"):
    print(record.id)
    print(len(record.seq))
    print(repr(record.seq))
```

    NC_045512.2
    29903
    Seq('ATTAAAGGTTTATACCTTCCCAGGTAACAAACCAACCAACTTTCGATCTCTTGT...AAA')


## GC content


```python
from Bio.Seq import Seq
from Bio.SeqUtils import GC
dna = Seq("GaTCGaTGGGCCTaTATAGGATCGaaaaTCGC")
print (f"""\
A: {dna.count("A")}
a: {dna.count("a")}
T: {dna.count("T")}
G: {dna.count("G")}
C: {dna.count("C")}
GC {GC(dna)}%\
""")
# .count() is sensitive to mixed case
# .GC() is not senstitive
```

    A: 3
    a: 7
    T: 7
    G: 9
    C: 6
    GC 46.875%


## slicing a sequence


```python
from Bio.Seq import Seq
dna = Seq("GATCGATGGGCCTATATAGGATCGAAAATCGC")
#          0123456789
print (dna[3:9])
print (dna[0::3])
print (dna[1::3])
print (dna[2::3])
```

    CGATGG
    GCTGTAGTAAG
    AGGCATGCATC
    TAGCTAAGAC


## concatenate sequence


```python
from Bio.Seq import Seq
l_seq = [Seq("ACGT"), Seq("AACC"), Seq("GGTT")]
concat = Seq("")
for s in l_seq:
    concat += s
print (concat)
```

    ACGTAACCGGTT


## join sequence


```python
from Bio.Seq import Seq
l_seq = [Seq("ACGT"), Seq("AACC"), Seq("GGTT")]
print (Seq("").join(l_seq))
print (Seq("nnnnn").join(l_seq))
```

    ACGTAACCGGTT
    ACGTnnnnnAACCnnnnnGGTT


## upper and lower


```python
from Bio.Seq import Seq
dna = Seq("GATCGATGGGCCTATATAGGATCGAAAATCGC")
print (dna.lower())
print ("GATC" in dna)
print ("GATC" in dna.lower()) # case matching
```

    gatcgatgggcctatataggatcgaaaatcgc
    True
    False


## transcribe and translate


```python
from Bio.Seq import Seq
dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")
print (dna.transcribe())
print (dna.translate())
```

    AUGGCCAUUGUAAUGGGCCGCUGAAAGGGUGCCCGAUAG
    MAIVMGR*KGAR*


## translate parameters


```python
from Bio.Seq import Seq
dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")
print (dna.translate())
print (dna.translate(to_stop=True))
print (dna.translate(table="Vertebrate Mitochondrial"))
print (dna.translate(table="Vertebrate Mitochondrial", to_stop=True))
```

    MAIVMGR*KGAR*
    MAIVMGR
    MAIVMGRWKGAR*
    MAIVMGRWKGAR

