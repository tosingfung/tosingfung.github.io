---

layout: post
tag: python-script
title: "Fetch and write GB files"
---

- Input a list of accession No.
- Fetch all GB records in one handle
- Write into one download.gb file
- Parse and enumerate GB records

<!--more-->

## sequence.seq (input)


```python
NC_048213.1
NC_001451.1
NC_002470.1
NC_002469.1
```

## script


```python
# https://www.ncbi.nlm.nih.gov/nuccore
# search, send to...
# complete record
# destination: file
# format: accession list
# return: sequence.seq
### concat GB IDs(remove version)
with open("sequence.seq","r") as file:
    IDs = ""
    for line in file: IDs += f"{line.strip().split('.')[0]},"
###



### download GB files using above GB IDs
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"
with Entrez.efetch(db="nucleotide",id=IDs,rettype="gb",retmode="text") as handle:
    records = SeqIO.parse(handle,"gb")
    SeqIO.write(records,"download.gb","gb")
###



### enumerate GB records
dicRecord = {}
dicIndex = SeqIO.index("download.gb","gb")
for i, key in enumerate(dicIndex):
    dicRecord[i+1] = [key,dicIndex[key]]
for n in dicRecord:
    print(f"\
{n!s:5}\
{dicRecord[n][0]:15}\
{dicRecord[n][1].description:.50}...")
# .50 limit display length
# n = item number
# dicRecord[n][0]: id
# dicRecord[n][1]: SeqRecord
dicIndex.close()
###
```

    1    NC_048213.1    Infectious bronchitis virus isolate Ind-TN92-03, c...
    2    NC_001451.1    Avian infectious bronchitis virus, complete genome...
    3    NC_002470.1    Turkey astrovirus, complete genome...
    4    NC_002469.1    Ovine astrovirus, complete genome...
    
