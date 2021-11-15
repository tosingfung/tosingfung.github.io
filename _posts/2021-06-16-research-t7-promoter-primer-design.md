---
tag: [research-tips]
layout: post
title: "T7 in vitro transcription"
---

![image-20210616150924753](/images/image-20210616150924753.png)

#### The +4 to +8 downstream sequence affect the transcription efficiency of T7 promoter.

<!--more-->

A [study](https://www.nature.com/articles/s42003-020-01167-x) has shown that +4 to +8 nucleotides downstream of T7 significantly affect transcription efficiency. Taken this into consideration, together with the user guide from [Lipofectamine MessengerMAX](https://www.thermofisher.cn/content/dam/LifeTech/global/life-sciences/CellCultureandTransfection/pdfs/Lipofectamine_MessengerMAX_man.pdf), the PCR forward primer should be (the reverse primer should contain a polyA tail): 

```
GC TAATACGACTCACTATA GGG ATAAT gccacc ATG...
   |                 |         |
   T7                Tss       kozak
```

