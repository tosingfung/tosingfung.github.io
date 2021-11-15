---

layout: post
tag: python-script
title: "Generate random oligo"

---

- Input integer A and B
- Make A sequences (B-nt)

<!--more-->

## script


```python
import random

t_base = ("a", "t", "g", "c")
# a tuple of the four bases

i_number = int(input("Number of oligo to make: "))
i_length = int(input("Length of oligo in nt: "))

with open("output.txt","w") as fh_output:
    for n in range (i_number):
        l_dna = []
        # start with empty list in each loop

        for m in range(i_length):
            l_dna.append(random.choice(t_base))
            # append random base to the list

        s_dna = "".join(l_dna)
        # join the list into a string

        print (f"Generating random seq {n+1}...", end="\r")
        # \r allows printing on the same line
        
        fh_output.write(f"{s_dna}\n")
        # remember to add \n 
        
        
print ("\ndone!")
# set a new line before printing done
```

    Number of oligo to make: 1000
    Length of oligo in nt: 50
    Making random seq 1000...
    done!
    

## output.txt
```
tagacaccgacgttacca
gttccgttcttggagagt
tcatagtcaatcggagag
gttaccgtagtcgaggga
taaacatttgcgtactgt
aaaagggacctgcgctta
agttcgggtacggaaact
agcggagctgtctcctct
```