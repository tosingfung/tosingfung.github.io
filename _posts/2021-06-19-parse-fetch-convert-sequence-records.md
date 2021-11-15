---

layout: post
tag: biopython-learn
title: "Parse, fetch, convert seq records"
---

- from Bio import Entrez
- with Entrez.efetch() as handle
- record = SeqIO.read(handle,"gb")
- records = SeqIO.parse(handle,"gb")
- SeqIO.to_dict(records)
- dicRecord = SeqIO.index("*.gb","gb")
- SeqIO.write(records,"*.gb","gb")
- SeqIO.convert("*.gb","gb","*.fasta","fasta")

<!--more-->

## fetch one GB record


```python
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"

with Entrez.efetch(db="nucleotide", \
                   id="NC_045512.2", \
                   rettype="gb", \
                   retmode="text") as handle:
    record = SeqIO.read(handle,"gb") # read for 1 record
    print (record.annotations["source"])
    
# rettype: return type, gb(gp for protein) or fasta
# use with..as.. so that handle is closed automatically
```

    Severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2)
    

## fetch several GB records


```python
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"

with Entrez.efetch(db="nucleotide", \
                   id="NC_045512,DQ001339", \
                   rettype="gb", \
                   retmode="text") as handle:
    for record in SeqIO.parse(handle,"gb"): # parse for >1 records
        print (record.annotations["source"])
```

    Severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2)
    Infectious bronchitis virus
    

## Seq files as dic in memory


```python
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"

with Entrez.efetch(db="nucleotide", \
                   id="NC_045512,DQ001339", \
                   rettype="gb", \
                   retmode="text") as handle:
    records = SeqIO.parse(handle,"gb") # parse for >1 records
    dicRecord = SeqIO.to_dict(records)
    # build a normal Python dictionary
    # key: record.id
    # value: SeqRecord
    # Memory demanding!
    print (dicRecord.keys())
    print (dicRecord["NC_045512.2"].annotations["source"])
    print (dicRecord["DQ001339.1"].annotations["source"])
```

    dict_keys(['NC_045512.2', 'DQ001339.1'])
    Severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2)
    Infectious bronchitis virus
    


```python
from Bio import SeqIO

dicRecord = SeqIO.index("mhv.gb","gb")
# .index() do not take handle, only filenames
# .index() also returns a disctionary
# it does not keep everything in RAM
# it just records where each record in within the file
# when ask for a record, it parses it on demand
for key in dicRecord:
    print (f"{key:15}{dicRecord[key].annotations['source']}")
```

    NC_048217.1    Murine hepatitis virus
    FJ647223.1     Murine coronavirus MHV-1
    FJ647224.1     Murine coronavirus MHV-3
    AF201929.1     Murine hepatitis virus strain 2
    GU593319.1     Murine hepatitis virus
    AC_000192.1    Murine hepatitis virus strain JHM
    

## Make enumerate dicRecord


```python
from Bio import SeqIO

dicRecord = {}
dicIndex = SeqIO.index("mhv.gb","gb")
for i, key in enumerate(dicIndex):
    dicRecord[i+1] = [key,dicIndex[key]]
for n in dicRecord:
    print(f"\
{n!s:5}\
{dicRecord[n][0]:15}\
{dicRecord[n][1].annotations['source']}")
# n = item number
# dicRecord[n][0]: id
# dicRecord[n][1]: SeqRecord
dicIndex.close()
# index must be closed
```

    1    NC_048217.1    Murine hepatitis virus
    2    FJ647223.1     Murine coronavirus MHV-1
    3    FJ647224.1     Murine coronavirus MHV-3
    4    AF201929.1     Murine hepatitis virus strain 2
    5    GU593319.1     Murine hepatitis virus
    6    AC_000192.1    Murine hepatitis virus strain JHM
    

## Convert .gb to .fasta file


```python
from Bio import SeqIO
SeqIO.convert("mhv.gb","gb","mhv.fasta","fasta")
# convert mhv.gb to mhv.fasta
# return the number of records converted
```




    6



## fetch and save multiple GB records


```python
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"

with Entrez.efetch(db="nucleotide", \
                   id="NC_045512,DQ001339,NC_048217", \
                   rettype="gb", \
                   retmode="text") as handle:
    records = SeqIO.parse(handle,"gb") # parse for >1 records
    SeqIO.write(records,"download.gb","gb")
```

## combine the above


```python
dicCov = { 
    "IBV"   :  "NC_001451",   # Beaudette
    "SARS"  :  "NC_004718",   # Tor2
    "SARS2" :  "NC_045512",   # WH-1
    "MERS"  :  "NC_019843",
    "229E"  :  "NC_002645",
    "OC43"  :  "NC_006213",
    "NL63"  :  "NC_005831",
    "HKU1"  :  "NC_006577",
    "PEDV"  :  "NC_003436",
    "TGEV"  :  "NC_038861",
    "FIPV"  :  "NC_002306",
    "A59"   :  "NC_048217",   # MHV-A59
    "JHM"   :  "AC_000192",}  # MHV-JHM 

strCov = ",".join([dicCov[key] for key in dicCov])


# download GB records of all IDs above to a file
from Bio import Entrez
from Bio import SeqIO
Entrez.email   = "tosingfung@qq.com"
Entrez.api_key = "fa5971edd0a80ba2a99eaa7d6191f674d808"
with Entrez.efetch(db = "nucleotide", \
                   id = strCov, \
                   rettype = "gb", \
                   retmode = "text") as handle:
    records = SeqIO.parse(handle,"gb")
    SeqIO.write(records,"download.gb","gb")


# index the .gb file and list records inside
from Bio import SeqIO    
dicRecord = {}
dicIndex = SeqIO.index("download.gb","gb")
for i, key in enumerate(dicIndex):
    dicRecord[i+1] = [key,dicIndex[key]]
for n in dicRecord:
    print(f"\
{n!s:5}\
{dicRecord[n][0]:15}\
{dicRecord[n][1].annotations['source']}")
dicIndex.close()

```

    1    DQ001339.1     Infectious bronchitis virus
    2    NC_001451.1    Infectious bronchitis virus
    3    NC_004718.3    SARS coronavirus Tor2
    4    NC_045512.2    Severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2)
    5    NC_019843.3    Middle East respiratory syndrome-related coronavirus (MERS-CoV)
    6    NC_002645.1    Human coronavirus 229E
    7    NC_006213.1    Human coronavirus OC43 (HCoV-OC43)
    8    NC_005831.2    Human coronavirus NL63 (HCoV-NL63)
    9    NC_006577.2    Human coronavirus HKU1 (HCoV-HKU1)
    10   NC_003436.1    Porcine epidemic diarrhea virus (PEDV)
    11   NC_038861.1    Transmissible gastroenteritis virus
    12   NC_002306.3    Feline infectious peritonitis virus
    13   NC_048217.1    Murine hepatitis virus
    14   AC_000192.1    Murine hepatitis virus strain JHM
    
