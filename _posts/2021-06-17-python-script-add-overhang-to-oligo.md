---

layout: post
tag: python-script
title: "Add overhang to oligo"

---

- Input multiple targeting sequence
- Return lentiCRISPRv2 cloning oligos

<!--more-->

## script


```python
def sgRNA(target):
    dna = target.lower()
    rev = target[::-1]
    rev_comp = rev\
    .replace("a","T")\
    .replace("t","A")\
    .replace("g","C")\
    .replace("c","G").lower()
    return [f"CACCG{target}",f"AAAC{rev_comp}C"]
    # return a list [sense, antisense]

fh_input = open("target.txt", "r")

with open("sgRNA.csv", "w") as fh_output:
    fh_output.write("target,sense,antisense\n")
    # remember to add \n after the first line
    
    for line in fh_input:
        target = line.strip()
        # remember to strip the \n
        
        sense = sgRNA(target)[0]
        antisense = sgRNA(target)[1]
        
        fh_output.write(f"{target},{sense},{antisense}\n")
        
fh_input.close()
# remember to close the handle
```

## target.txt
```
ctatggcggtcaatatggtg
tgttccacagtatgtccatg
tctcataacccggttgccga
ggctggacaatcatcagaat
tcgtgaatatcactagcggt
```

## sgRNA.csv
```
target,sense,antisense
ctatggcggtcaatatggtg,CACCGctatggcggtcaatatggtg,AAACcaccatattgaccgccatagC
tgttccacagtatgtccatg,CACCGtgttccacagtatgtccatg,AAACcatggacatactgtggaacaC
tctcataacccggttgccga,CACCGtctcataacccggttgccga,AAACtcggcaaccgggttatgagaC
ggctggacaatcatcagaat,CACCGggctggacaatcatcagaat,AAACattctgatgattgtccagccC
tcgtgaatatcactagcggt,CACCGtcgtgaatatcactagcggt,AAACaccgctagtgatattcacgaC
```
