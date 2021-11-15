---

layout: post
tag: python-script
title: "Mutable RE sites inside a peptide"
---

- Input a short peptide sequence
- Check if a restriction enzyme site can be incorporated to the coding sequence without changing the amino acids
- return a list of such "mutable" RE sites and their locations

<!--more-->


```python
from Bio.Seq import Seq
import re

### Dictionary
### k = re_name
### v = re_site
dic_re = {\
"AflII"  : "CTTAAG",
"ApaI"   : "GGGCCC",
"BamHI"  : "GGATCC",
"BglII"  : "AGATCT",
"BlnI"   : "CCTAGG",
"ClaI"   : "ATCGAT",
"DraI"   : "TTTAAA",
"EcoRI"  : "GAATTC",
"EcoRV"  : "GATATC",
"HindIII": "AAGCTT",
"HpaI"   : "GTTAAC",
"KpnI"   : "GGTACC",
"MluI"   : "ACGCGT",
"NcoI"   : "CCATGG",
"NheI"   : "GCTAGC",
"PstI"   : "CTGCAG",
"PvuII"  : "CAGCTG",
"SacI"   : "GAGCTC",
"SmaI"   : "CCCGGG",
"SnaBI"  : "TACGTA",
"SpeI"   : "ACTAGT",
"SphI"   : "GCATGC",
"StuI"   : "AGGCCT",
"SalI"   : "GTCGCA",
"XbaI"   : "TCTAGA",
"XhoI"   : "CTCGAG",}
###



### tuple of DNA bases
base = ("A","T","G","C")



### get translations from a list of DNA
def translate_dna_list (l):
    return {str(Seq(x).translate()) for x in l if "*" not in str(Seq(x).translate())}



### Take an re_name as argument
### get all three frame translation possibilities
### return a list
### list[0]: re_site
### list[1]: frame 1 translations (set)
### list[2]: frame 2 translations (set)
### list[3]: frame 3 translations (set)
def translate_6cut (re_site):
    dna1 = [re_site]
    dna2 = [f"{n1}{re_site}{n2}{n3}" for n1 in base for n2 in base for n3 in base]
    dna3 = [f"{n1}{n2}{re_site}{n3}" for n1 in base for n2 in base for n3 in base]
    translate1 = translate_dna_list(dna1)
    translate2 = translate_dna_list(dna2)
    translate3 = translate_dna_list(dna3)
    return [re_site, translate1, translate2, translate3]
###



### print all MutableRE for one enzyme 
def printMutableRE (re_name, re_site, protein):
    for p1 in translate_6cut(re_site)[1]:
        for match in re.finditer(p1, protein):
            location = match.start() + 1
            print (f"{re_name:10}{location!s:6}{p1:6}(frame1)   {re_site[0:3]} {re_site[3:6]}")
    for p2 in translate_6cut(re_site)[2]:
        for match in re.finditer(p2, protein):
            location = match.start() + 1
            print (f"{re_name:10}{location!s:6}{p2:6}(frame2)   x{re_site[0:2]} {re_site[2:5]} {re_site[5:6]}xx")
    for p3 in translate_6cut(re_site)[3]:
        for match in re.finditer(p3, protein):
            location = match.start() + 1
            print (f"{re_name:10}{location!s:6}{p3:6}(frame2)   xx{re_site[0:1]} {re_site[1:4]} {re_site[4:6]}x")
###



### get a string from compulsory input
### take prompt message as only argument
def getInputStr(msg):
    s = ""
    while s == "":
        s = input(f"{msg}")
        continue
    return s
###



### ask for choice between two options
### if user choose option 1, return int 1
### if user choose option 2, return int 2
def getInputSelect (msg,s1,d1,s2,d2):
    selection = 0
    while selection == 0:
        print (msg)
        Input = input(f"Enter '{s1}' for {d1}, '{s2}' for {d2}:  ")
        if Input == s1:
            selection = 1
        elif Input == s2:
            selection = 2
        else: continue
    return selection
###



### core script
protein = ""
while protein == "":
    protein = getInputStr("Enter amino acid sequence of a short peptide:  ")
    if re.match("^[ACDEFGHIKLMNPQRSTVWY]*$",protein.upper()):
        # check if input contains characters other than amino acid codes
        for re_name in dic_re_site:
            printMutableRE (re_name, dic_re[re_name], protein)
    else:
        print ("Something wrong with input peptide sequence...")
        protein = ""
        continue
```

    Enter amino acid sequence of a short peptide:  try sth stupid
    Something wrong with input peptide sequence...
    Enter amino acid sequence of a short peptide:  GSEFGSSGHILL
    BamHI     1     GS    (frame1)   GGA TCC
    BamHI     5     GS    (frame1)   GGA TCC
    EcoRI     3     EF    (frame1)   GAA TTC
    SacI      5     GSS   (frame2)   xxG AGC TCx
    XhoI      5     GSS   (frame2)   xxC TCG AGx
    
