---
layout: post
tag: python-learn
title: "re.finditer / random.choice"
---

- revision of re.finditer
- random.choice to generate seq
- time.time() to time script

<!--more-->

## String to datetime object


```python
ibvm = """\
ATGTCCAACGAGACAAATTGTACTCTTGACTTTGAACAGTCAGTTCAGCTTTTTAAAGAGTATAATTTAT\
TTATAACTGCATTCTTGTTGTTCTTAACCATAATACTTCAGTATGGCTATGCAACAAGAAGTAAGGTTAT\
TTATACACTGAAAATGATAGTGTTATGGTGCTTTTGGCCCCTTAACATTGCAGTAGGTGTAATTTCATGT\
ATATACCCACCAAACACAGGAGGTCTTGTCGCAGCGATAATACTTACAGTGTTTGCGTGTCTGTCTTTTG\
TAGGTTATTGGATCCAGAGTATTAGACTCTTTAAGCGGTGTAGGTCATGGTGGTCATTTAATCCAGAATC\
TAATGCCGTAGGTTCAATACTCCTAACTAATGGTCAACAATGTAATTTTGCTATAGAGAGTGTGCCAATG\
GTGCTTTCTCCAATTATAAAGAATGGTGTTCTTTATTGTGAGGGTCAGTGGCTTGCTAAGTGTGAACCAG\
ACCACTTGCCTAAAGATATATTTGTTTGTACACCGGATAGACGTAATATCTACCGTATGGTGCAGAAATA\
TACTGGTGACCAAAGCGGAAATAAGAAAAGGTTTGCTACGTTTGTCTATGCAAAGCAGTCAGTAGATACT\
GGCGAGCTAGAAAGTGTAGCAACAGGAGGAAGTAGTCTTTACACATAA"""

import re

for m in re.finditer("GG..CC", ibvm):
    print(m.group(), m.start(), m.end())
```

    GGCCCC 175 181
    GGATCC 289 295


## generate random seq


```python
import random, time, re
bases = ("A", "T", "G", "C")
seq_list = []

t1 = time.time() # timer 1

for n in range (0,1000):
    seq_list.append(random.choice(bases))
seq = "".join(seq_list)

t2 = time.time()

for m in re.finditer("GG..CC", seq):
    print(m.start(), end=" ")
    
t3 = time.time()

print ()
print ("program start:", t1)
print ("generate seq: ", t2)
print ("find pattern: ", t3)

```

    24 113 618 683 857 900 
    program start: 1623763846.3518999
    generate seq:  1623763846.352897
    find pattern:  1623763846.3538928

