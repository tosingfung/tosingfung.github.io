---
layout: post
tag: [python-script]
title: "Merger for Snapgene primers"
---

- A quick python script to archive newly designed primers exported from Snapgene

<!--more-->

## Script
```python
import os

p = os.path.dirname(os.path.abspath(__file__))
# get current directory


with open(os.path.join(p,'Primer.csv'), 'r') as master:
    count = len(master.readlines()) + 1
# read line number in Primer.csv (master)
# set count to line number plus one


fp_list = [os.path.join(p,f) for f in os.listdir(p) if f.startswith('Primers')]
# build filepath list in current directory
# include all file name that startswith 'Primers'


with open(os.path.join(p,'Primer.csv'), 'a') as master:
# append NOT write to existing Primer.csv
    for fp in fp_list:
        with open(fp, 'r') as fh:
            for line in fh:
                name = line.split('\t')[0].strip()
                # primer name, remove space
                seq = line.split('\t')[1]
                seq = seq.strip('\n').replace(' ','').lower()
                # primer sequence, remove \n and space, lower case
                master.write(f'\np{count}-{name},{seq}')
                # write to Primer.csv, add serial number p#
                count += 1
        os.remove(fp)
        # remove the Snapgene-exported files
```
