---
title: Fetch GenBank from Seq List
layout: post
tag: python-script
---

- Input/download a list of gene ID
- Fetch GenBank records accordingly
- Write each entry into one .gb file
- Rename as ID + description

<!--more-->

## Preparing the Seq List

1. Go to [NCBI Nucleotide](https://www.ncbi.nlm.nih.gov/nuccore) and seach a keyword.
2. Check the item(s) and click **Send to**. Choose **Complete Record** (default). Choose **Clipboard** in <u>Choose Destination</u>. Click **Add to Clipboard**.
3. Keep searching and adding more items to the clipboard.
4. Open the [clipboard page](https://www.ncbi.nlm.nih.gov/nuccore/clipboard).
5. Click **Send to**. Choose **Complete Record** (default). Choose **File** in <u>Choose Destination</u>. Select **Accession List** in <u>Format</u>. Click **Create File** to download.
6. The **sequence.seq** file is downloaded. Here shows one example:

```text
NC_001451.1
NC_003436.1
NC_038861.1
NC_045512.2
NC_004718.3
NC_002645.1
NC_006213.1
NC_006577.2
NC_005831.2
NC_048217.1
NC_002306.3
```

## Script

```python
import os
import re
from Bio import Entrez
from Bio import SeqIO

# set path to current directory
path = os.path.dirname(os.path.abspath(__file__))

# remove version number of gene ID and concatanate
with open(f"{os.path.join(path,'sequence.seq')}","r") as ip:
	id_concat = ''
	for line in ip:
		id_concat += f"{line.strip().split('.')[0]},"


# fetch genbank data
Entrez.email   = "xxx"
Entrez.api_key = "xxx"
print ('Fetching GenBank data...')
with Entrez.efetch(db="nucleotide", id=id_concat, rettype="gb", retmode="text") as handle:
    records = SeqIO.parse(handle, "gb") 
    for record in records:
        name = str(record.name)
        # name is the gene ID without version
        desc = re.sub(r'[/|\|<|>|?|:|"|*|!]', r'-', str(record.description))
        # first convert record.description to str
        # then substitute special characters with hythen
        # otherwise error special characters appear in file names
        print (f'Fetching {name}\t{desc:.60}')
        # show only first 60 characters of description
        SeqIO.write(record, f"{name} {desc:.200}.gb", "gb")
        # limit description length to 200 characters

# remove python script file and sequence.seq
os.remove((os.path.join(path,'Fetch GenBank from Seq List.py')))
os.remove((os.path.join(path,'sequence.seq')))
```

## Output

```text
D:\NC_001451 Avian infectious bronchitis virus, complete genome.gb
D:\NC_002306 Feline infectious peritonitis virus, complete genome.gb
D:\NC_002645 Human coronavirus 229E, complete genome.gb
D:\NC_003436 Porcine epidemic diarrhea virus, complete genome.gb
D:\NC_004718 SARS coronavirus Tor2, complete genome.gb
D:\NC_005831 Human Coronavirus NL63, complete genome.gb
D:\NC_006213 Human coronavirus OC43 strain ATCC VR-759, complete genome.gb
D:\NC_006577 Human coronavirus HKU1, complete genome.gb
D:\NC_019843 Middle East respiratory syndrome-related coronavirus isolate HCoV-EMC-2012, complete genome.gb
D:\NC_038861 Transmissible gastroenteritis virus complete genome, genomic RNA.gb
D:\NC_045512 Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome.gb
D:\NC_048217 Murine hepatitis virus strain A59, complete genome.gb
```

## Final remark

- Saving the items as individual GenBank files will make it easier to open them individually using Snapgene. However, primers and customized features cannot be saved in GenBank format. For that, you need to save the file as `.dna` 