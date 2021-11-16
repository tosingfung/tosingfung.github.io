---

layout: post
tag: python-script
title: "Parse GB and write to FASTA"
---

- Input download.gb
- Choose nucleotide or protein seq
- Give abbr. for virus strain/isolate
- Parse GB record
- Enumerate CDS with translation
- Choose CDS and give abbr.
- Give name to output .fasta file
- Write to the output .fasta file

<!--more-->


```python
from Bio import SeqIO

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
        Input = input(f"Enter {s1} for {d1}, {s2} for {d2}:  ")
        if Input == s1:
            selection = 1
        elif Input == s2:
            selection = 2
        else: continue
    return selection
###



### input a string: number separated by comma
### split and append number to a list
### use number as key to get description of CDS product:
### SeqFeature.qualifiers["product"][0]
### display and ask user to confirm
### if confirm, return the list
### if deny, loop to get input again
def get_input_list_check_CDS (dic):
    l = []
    while l == []:
        s = input("Select item(s) to download (1,2...):  ")
        for x in s.split(","):
            try: l.append(int(x))
            except: continue
        l1 = list(set(l))
        print ("You have selected these:  ")
        for k in l1:
            print (dic[k][1])
        yn = getInputSelect("Proceed to write to fasta?","y","yes","n","no")
        if yn == 1:
            continue
        if yn == 2:
            l.clear()
            continue
    return l1
###



### build a dictionary from SeqRecord
### get user input for abbreviation of GB record
### filter features with .type==CDS and has translation in .qualifiers
### extract the CDS sequence and protein sequences
def build_CDS_dic(record):
    CDS_counter = 0
    dic = {}
    CDS_source_abbr = getInputStr(msg = f"Give abbreviation for the follwing isolate:\n{record.description}:  ")
    for feature in record.features:
        if feature.type == "CDS" and "translation" in feature.qualifiers:
            CDS_counter += 1
            CDS_protein_id = feature.qualifiers['protein_id'][0] # dic0
            CDS_product = feature.qualifiers['product'][0] # dic1
            CDS_sequence = feature.location.extract(record.seq) #dic2
            CDS_translation = feature.qualifiers['translation'][0] #dic3      
            dic[CDS_counter] = [CDS_protein_id, \
                                  CDS_product, \
                                  CDS_sequence, \
                                  CDS_translation, \
                                  CDS_source_abbr]
    return dic
###



### enumerate CDS from a CDS_dict
### show the key, accession and CDS product
def enumerate_CDS(dic):
    for k in dic:
        print(f"{k!s:5}{dic[k][0]:18}{dic[k][1]}")
###



### three arguments
### lis: list of CDS keys input and confirm by user
### dic: CDS dictionary generated from parsing a SeqRecord
### np: nucleotide(1) or protein(2) seq type user choose
def write_fasta(lis,dic,np):
    for k in lis:
        try:
            seq = dic[k][np]
            name = getInputStr(f"Give abbreviation for {dic[k][1]}:  ")
            fh.write(f">{dic[k][4]}-{name}\n{seq}\n")
        except: continue
###



### core script
fname = getInputStr("Give a file name for the fasta file:  ")
with open(f"{fname}.fasta","w") as fh:
    # open fasta output with user provided file name
    dicRecord = {}
    dicIndex = SeqIO.index("download.gb","gb")
    # create SeqIO.index handle for GB file 
    
    np = getInputSelect("Get nucleotide or protein sequence?","n","nucleotide","p","protein")+1
    # user choose seq type: nucleotide(np=2) or protein(np=3)
    
    for i, key in enumerate(dicIndex):
        dicRecord[i+1] = [key,dicIndex[key]]
        # create dicRecord from dicIndex
        
    for n in dicRecord:
        print (f"{n!s:5}{dicRecord[n][0]:18}{dicRecord[n][1].description}")
    print (f"Total {len(dicRecord)} records to process\n","="*50)
        # enumerate record in the dicRecord
    
    for n in dicRecord:
        record = dicRecord[n][1]
        CDS_dic = build_CDS_dic(record)
        enumerate_CDS(CDS_dic)
        yn1 = getInputSelect("Proceed to select items?","y","yes","n","no")
        # user choose whether extract CDS from current record
        # if yes, user input a list
        # if no, skip this record and move on to next record in dicRecord
        if yn1 == 1:
            write_fasta(get_input_list_check_CDS(CDS_dic),CDS_dic,np)
        if yn1 == 2: continue

dicIndex.close()
# close the SeqIO.index handle
```

    Give a file name for the fasta file:  E protein
    Get nucleotide or protein sequence?
    Enter n for nucleotide, p for protein:  p
    1    NC_048213.1       Infectious bronchitis virus isolate Ind-TN92-03, complete genome
    2    NC_001451.1       Avian infectious bronchitis virus, complete genome
    3    NC_002470.1       Turkey astrovirus, complete genome
    4    NC_002469.1       Ovine astrovirus, complete genome
    Total 4 records to process
     ==================================================
    Give abbreviation for the follwing isolate:
    Infectious bronchitis virus isolate Ind-TN92-03, complete genome:  TN92
    1    YP_009824996.1    ORF1ab polyprotein
    2    YP_009824997.1    ORF 1a polyprotein
    3    YP_009824998.1    spike glycoprotein
    4    YP_009824999.1    3a protein
    5    YP_009825000.1    3b protein
    6    YP_009825001.1    3c protein
    7    YP_009825002.1    membrane glycoprotein
    8    YP_009825003.1    5a protein
    9    YP_009825004.1    5b protein
    10   YP_009825005.1    nucleocapsid protein
    Proceed to select items?
    Enter y for yes, n for no:  y
    Select item(s) to download (1,2...):  1, *** Type Error ***
    You have selected these:  
    ORF1ab polyprotein
    Proceed to write to fasta?
    Enter y for yes, n for no:  n
    Select item(s) to download (1,2...):  6
    You have selected these:  
    3c protein
    Proceed to write to fasta?
    Enter y for yes, n for no:  y
    Give abbreviation for 3c protein:  E
    Give abbreviation for the follwing isolate:
    Avian infectious bronchitis virus, complete genome:  IBV
    1    NP_066134.1       ORF1ab polyprotein
    2    NP_040829.1       ORF1a polyprotein
    3    NP_040831.1       spike protein
    4    NP_040832.1       3a protein
    5    NP_040833.1       3b protein
    6    NP_040834.1       small virion-associated protein
    7    NP_040835.1       membrane protein
    8    NP_040836.1       5a protein
    9    NP_040837.1       5b protein
    10   NP_040838.1       nucleocapsid protein
    Proceed to select items?
    Enter y for yes, n for no:  y
    Select item(s) to download (1,2...):  6
    You have selected these:  
    small virion-associated protein
    Proceed to write to fasta?
    Enter y for yes, n for no:  y
    Give abbreviation for small virion-associated protein:  E
    Give abbreviation for the follwing isolate:
    Turkey astrovirus, complete genome:  Turkey
    1    NP_853540.1       orf1ab polyprotein (pp1ab)
    2    NP_059947.1       orf1a polyprotein (pp1a)
    3    NP_059949.1       capsid protein precursor
    Proceed to select items?
    Enter y for yes, n for no:  n
    Give abbreviation for the follwing isolate:
    Ovine astrovirus, complete genome:  Ovine
    1    NP_059945.2       orf1ab polyprotein (orf1ab)
    2    NP_059944.1       nonstructural protein, putative serine protase
    3    NP_059946.1       capsid protein precursor
    Proceed to select items?
    Enter y for yes, n for no:  n
    

## (output) E protein.fasta


```python
>TN92-E
MMNLLNKSLEENGSFLTALYIIVGFLALYLLGRALQAFVQAADACCLFWYTWVVIPGAKGTAFVYKYTYGRKLNNPELEAVIVNEFPKNGWNNKNPANFQDVQRDKLHS
>IBV-E
MNLLNKSLEENGSFLTALYIIVGFLALYLLGRALQAFVQAADACCLFWYTWVVIPGAKGTAFVYKYTYGRKLNNPELEAVIVNEFPKNGWNNKNPANFQDAQRDKLYS
```
