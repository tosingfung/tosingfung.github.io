---
layout: post
tag: python-learn
title: "SeqRecord and SeqFeature"
---

- record = SeqIO.read()
- **SeqRecord Object**
- record.id
- record.name
- record.description
- record.annotations (dic)
- record.annotations['source']
- record.features (list)
- **SeqFeature Object**
- feature.type
- feature.location
- feature.location.extract(record.seq)
- **.type = "CDS"**
- feature.qualifiers (dic)
- feature.qualifiers['protein_id'] (list)
- feature.qualifiers['product'] (list)
- feature.qualifiers['translation'] (list)

<!--more-->

## SeqRecord obj from FASTA


```python
from Bio import SeqIO
record = SeqIO.read("ibv.fasta","fasta")
# SeqIO.read() for only one record
# SeqIO.parse() for all the records
record
```




    SeqRecord(seq=Seq('ACTTAAGATAGATATTAATATATATCTATTATACTAGCCTTGCGCTAGATTTTT...GCA'), id='DQ001339.1', name='DQ001339.1', description='DQ001339.1 Avian infectious bronchitis virus isolate IBV-p65, complete genome', dbxrefs=[])




```python
from Bio import SeqIO
record = SeqIO.read("ibv.fasta","fasta")
record.description
```




    'DQ001339.1 Avian infectious bronchitis virus isolate IBV-p65, complete genome'



## SeqRecord obj from GenBank


```python
from Bio import SeqIO
record = SeqIO.read("sars2.gb","genbank")
print (record.id)
print (record.name)
print (record.description)
print (len(record.seq))
```

    NC_045512.2
    NC_045512
    Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome
    29903



```python
from Bio import SeqIO
record = SeqIO.read("sars2.gb","genbank")
print (len(record.annotations))
print (record.annotations["source"])
# return the annotations dictionary
```

    13
    Severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2)



```python
from Bio import SeqIO
record = SeqIO.read("sars2.gb","genbank")
print (len(record.features))
print (record.features)
# return a list of SeqFeature object
```


```python
from Bio import SeqIO
record = SeqIO.read("sars2.gb","genbank")
for feature in record.features:
    print (f"""\
    {feature.type},{feature.location}\
    """)
```

        source,[0:29903](+)    
        5'UTR,[0:265](+)    
        gene,[265:21555](+)    
        CDS,join{[265:13468](+), [13467:21555](+)}    
        mat_peptide,[265:805](+)    
        mat_peptide,[805:2719](+)    
        mat_peptide,[2719:8554](+)    
        mat_peptide,[8554:10054](+)    
        mat_peptide,[10054:10972](+)    
        mat_peptide,[10972:11842](+)    
        mat_peptide,[11842:12091](+)    
        mat_peptide,[12091:12685](+)    
        mat_peptide,[12685:13024](+)    
        mat_peptide,[13024:13441](+)    
        mat_peptide,join{[13441:13468](+), [13467:16236](+)}    
        mat_peptide,[16236:18039](+)    
        mat_peptide,[18039:19620](+)    
        mat_peptide,[19620:20658](+)    
        mat_peptide,[20658:21552](+)    
        CDS,[265:13483](+)    
        mat_peptide,[265:805](+)    
        mat_peptide,[805:2719](+)    
        mat_peptide,[2719:8554](+)    
        mat_peptide,[8554:10054](+)    
        mat_peptide,[10054:10972](+)    
        mat_peptide,[10972:11842](+)    
        mat_peptide,[11842:12091](+)    
        mat_peptide,[12091:12685](+)    
        mat_peptide,[12685:13024](+)    
        mat_peptide,[13024:13441](+)    
        mat_peptide,[13441:13480](+)    
        stem_loop,[13475:13503](+)    
        stem_loop,[13487:13542](+)    
        gene,[21562:25384](+)    
        CDS,[21562:25384](+)    
        gene,[25392:26220](+)    
        CDS,[25392:26220](+)    
        gene,[26244:26472](+)    
        CDS,[26244:26472](+)    
        gene,[26522:27191](+)    
        CDS,[26522:27191](+)    
        gene,[27201:27387](+)    
        CDS,[27201:27387](+)    
        gene,[27393:27759](+)    
        CDS,[27393:27759](+)    
        gene,[27755:27887](+)    
        CDS,[27755:27887](+)    
        gene,[27893:28259](+)    
        CDS,[27893:28259](+)    
        gene,[28273:29533](+)    
        CDS,[28273:29533](+)    
        gene,[29557:29674](+)    
        CDS,[29557:29674](+)    
        stem_loop,[29608:29644](+)    
        stem_loop,[29628:29657](+)    
        3'UTR,[29674:29903](+)    
        stem_loop,[29727:29768](+)    

