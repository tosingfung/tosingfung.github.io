---
title: 2007 DREAM report
layout: post
tag: undergraduate
---

## Microfluidic and Microbiology

Student: Martin To Sing Fung<br>Supervisor: Professor Leo Lau

## Background

In 2005, it was reported that pilus-like appendages are produced by Shewanella oneidensis in direct response to electron acceptor limitation. The apparent height of these appendages in scanning tunneling microscope (STM) is about 10nm, which is in consistent with scanning electron microscope (SEM) measurement, indicating that they are electrical conductive. (In STM, conducting samples should have apparent height close to actual height. If a sample feature is not conductive, the feature is invisible to STM and the apparent height should be zero. ) These appendages are thus named bacterial nanowires. When S.oneidensis is grown with silica ferrihydrite as the only electron acceptor, nanocrystalline magnetite is found arranged in linear arrays, whose dimensions consistent with nanowires.(Figure.1) It is proposed that nanowires are used to transport electrons to extracellular solid iron oxide.

![dream1](https://raw.githubusercontent.com/tosingfung/images/master/dream1.png)

#### Figure 1

Another group studied on anaerobic bacteria Geobacter sulfurreducens, which produce nanowires to attach to and reduce Fe (III). Using conducting probe atomic force microscopy (CP-AFM), the nanowires were also found highly conductive. Certain pilus-deficient mutants could not reduce Fe (III) but could attach to them with nanowires. (Lovley, 2005) However, some skeptics claimed that the TEM image (Figure.1) is a thin section of sample, and for three dimensionally protruding nanowires, it’s fairly unlikely that the section will cut through three nanowires at the same time. So, these linear structures are more likely to be extracellular polymeric substances secreted by the bacteria. Also, in Lovley’s CP-AFM study, the measured part between the conductive tip and graphite support is the equatorial section of the pilus filament, so whether it is conductive along the nanowire is not tested.

### Experimental design and theory

Using an alternative approach, we have the idea of inducing the nanowire to grow in a confined nanochannel in a microfluidic device. The design is shown in Figure.2, which is embedded between two glass slides. To save cost, two separate systems are put on one device. In each system, the large circles at top and bottom are the inlets and outlets. Thick lines are microchannels where bacteria culture or mineral solution flows through, which are about 25μm wide. The two smaller circles in the middle indicate chambers, which are not to scale. The diameter should be around 60μm. The thin lines between two chambers refer to the nanochannels, each of which is 400nm wide and deep, about 25μm long. It is slightly narrower than the diameter of S.oneidensis cells; also given the chemotaxis motion (thrust and tumble) of bacteria, it is fairly unlikely that a bacterium will flow through the nanochannels to the mineral chamber. Except for the nanochannels, the depths of all device features are 8.5μm.

![dream2](https://raw.githubusercontent.com/tosingfung/images/master/dream2.png)

####  Figure 2

Then S.oneidensis is injected in the bacteria chamber and uranyl acetate in the mineral chamber. When oxygen is depleted, S.oneidensis will shift to second best available electron acceptor. Sensing the trace amount of uranyl acetate yet unable to move to the opposite chamber, S.oneidensis may then produce nanowires through interlinking nanochannels. If black precipitation of reduced uranium is observed in mineral chamber, we can crack the device to image and analyze it. Microfluidics provides many advantages in this study. Fluid has unique properties in micro-scale, such as laminar and electro-osmotic flow, which can be utilized to manipulate micro environment of the bacteria chamber. What is more, a microfluidic device can easily combine with micro electro mechanical systems (MEMs). For example, a refined device with probes at the two ends of nanochannel can characterize the electrical properties along the nanowires. A microfluidic device also has the advantage of saving materials. Not only fewer bacteria are needed, but the use of toxic mineral (uranyl acetate) is reduced.

### Objective

If the hypothesis stands, we expect to observe bacterial nanowires in the nanochannels and possibly in the mineral chamber. Coexistence of nanowires and reduced uranium precipitations will be good evidence that nanowires are used to transport electrons and reduce uranyl acetate. If the two chambers are linked with nanowires, there will also be an increase of conductivity along the nanochannels. In confirming that nanowires are produced under electron acceptor limitation and are used by S.oneidensis to transport electrons to extracellular minerals, we can further study the electrical and chemical properties of the nanowires by further modifying the device and combining it with MEMs. We can also study the molecular basic of nanowires’ conductivity and its functioning mechanisms. Moreover, mutant studies will allow us to unravel the genetic and molecular basis of nanowire function.

## Experimental design and procesures

### 1. Fabrication of microfluidic device

1. A glass slide is cleaned. Using E-beam evaporation, chromium (10nm) is coated as the adhesion layer. Then, another gold layer (150nm) is coated on top. These metal layers serve as media to transfer the mask pattern from the photoresist layer to the glass slide (because glass etchant hydrogen fluoride is not selective and reacts with exposed photoresist, a media layer is required). Also, the chromium layer is essential in the carving of nanochannel with focused ion beam (FIB).

2. Positive photoresist (Shipley® SC1827) is spread (500 rpm, 10 s) and spin-coated (2500 rpm, 45 s) on top of the gold layer. The thickness of photoresist layer is about 3.5 micron.

3. Photolithography. A 5’ by 5’ mask is prepared, with channels and chambers’ pattern transparent and other area opaque. UV light is then shined through the mask onto the glass slide prepared in step2. Chemical reactions will occur in and only in the exposed region of photoresist layer.

4. The exposed region is washed away with photoresist developer (MF-319).

5. Gold etchant is added to transfer pattern to gold layer. After that chromium etchant is added to further transfer pattern to the chromium layer. Both etching last for 30 seconds and are isotropic.

6. Hydrogen fluoride is added to etch microchannels and chambers into the glass slide. This is also isotropic, so the edges are round and actual diameter will be little bigger than that on the mask. After 45 minutes, the pattern is about 8.5 microns deep into glass.

7. Photoresist and gold coating are removed.

8. Using Focused Ion Beam (FIB-SEM), five nanochannels (400nm deep and wide, about 25 micron long) is fabricated between two chambers. Gallium ion is used to sputter the surface and dry-etch into glass. Because focused ion beam requires a conductive layer (so that positive charge will not accumulate and eventually repel positive gallium ion), the chromium layer is not washed in step 7. Also, SEM is used for accurate positioning of nanochannels, which also needs a conductive surface.

9. The chromium layer is removed.

10. Cover glass bonding. Because the device has to be cracked open after the experiment, permanent bonding can’t be used. Also, ordinary microscopy cover glass is too flexible to withstand the pressure of injection. Therefore, we use anther glass slide as cover glass. Eight holes are drilled beforehand at the location of the inlets and outlets. The bonding surfaces are cleaned, moisturized and directly bonded. Cover glass is essential in making the device completely isolated from atmosphere and creates the anaerobic environment that is critical for nanowire production.

11. Flat bottom ports are added on top of all inlets and outlets. These ports are convenient adaptors which keeps device anaerobic yet provide easy access whenever injection of fresh medium/bacteria/minerals is necessary.

Figure.3 shows what a complete device looks like (A, B). 3-C illustrate the relative dimension of chambers, nanochannels and S.oneidensis cells under SEM. 3-D is the unfilled device under an optical microscope. When the microchannels and chambers are filled up, it becomes transparent, so do the nanochannels shown in the middle.

![dream3](https://raw.githubusercontent.com/tosingfung/images/master/dream3.png)

#### Figure 3

### 2. Growing of S. oneidensis culture

Shewanella oneidensis is a gram negative bacterium. It is widely used as the model organism of metal reducing bacteria due to the following reasons:

1. Metabolic robust. S.oneidensis can utilize various kinds of electron donor (lactate, acetate, pyruvate, serine, and other amino acids) and electron acceptors (S, S2O32-, NO3-, NO2-, trimethylamine oxide, dimethyl sulfoxide, fumarate, soluble and insoluble forms of iron (III), manganese (III/IV) etc.).

2. Facultative anaerobic. S.oneidensis can live with or without oxygen. This makes culturing easy and incurs research interest in the genetic switching basis behind this environmental responds. This property is beneficial for our experiment because trace amount of oxygen within the device can be used for bacterial growth and replication; whereas the anaerobic condition afterwards will induce electron acceptor to shift and production of nanowires.

3. The genome of S.oneidensis has been mapped, which makes mutant study possible. By knocking out or overexpressing certain genes, we can unravel the molecular basis of nanowire function. S.oneidensis from rich medium is inoculated into a minimal defined medium of the following chemical compositions:

| Constituents          | Concentration |
| --------------------- | ------------- |
| sodium lactate        | 18 mM/L       |
| PIPES buffer          | 3 mM/L        |
| sodium bicarbonate    | 20 mM/L       |
| ammonium chloride     | 28 mM/L       |
| sodium biphosphate    | 4.35 mM/L     |
| nitrilotriacetic acid | 0.1 mM/L      |

Sodium lactate is the electron donor for S.oneidensis; it also serves as the carbon source in assimilation. PIPEs buffer maintains the medium at around pH 6.8, and it makes medium isotonic to bacterial cytoplasm, so that cells will not burst due to water inflow under osmotic pressure. Sodium bicarbonate also works as buffer. Ammonium chloride and NaH2PO4 are nitrogen and phosphate source respectively. Nitrolotriacetic acid is a chelator of metal ions. It can shuttle metal ions to and fro the two chambers in its alternative redox forms. Vitamins and minerals are essential for bacterial survival because they are necessary components of enzymes or coenzymes. Final pH was adjusted to 7.0 with 2M HCl. A defined minimal medium is used because it contains and only contains all the chemicals necessary for S.oneidensis survival. Also, under anaerobic condition, no chemical in the mineral medium can serve as an alternative electron acceptor, so S.oneidensis is obliged to produce nanowires in search for uranyl acetate in the mineral chamber.

### 3. Induction nanowire growth in nanochannel

The uranyl acetate is kept in anaerobic for two days to get rid of any dissolved oxygen. Then it is injected via a syringe filter into the mineral chamber through the mineral inlet under an optical microscope. When the microchannels and chamber become transparent, plugs are added on the flat bottom ports of mineral inlet and outlet to ensure anaerobic environment. At the time of experiment, the population density of S.oneidensis minimal culture is about 108-109 cells/mL. After injection, around 10 - 50 cells will remain in the bacterial chamber. The bacterial inlet and outlet are plugged as well to ensure anaerobic. The device is then left in a dark and cool bench for a week, during which the bacteria grow and replicate. Fresh medium is regularly supplied. Under optical microscope, the cell number in bacterial chamber increases steadily. After 9 days, black precipitation is observed in the mineral chamber and the device is ready for analysis.

### 4. SEM imaging and further characterization

Glucoaldehyde is injected into the bacteria chamber to fix all the cells and cellular components. Then the device is cracked open and put in 25% ethanol. Increasing concentration of ethanol (50%, 75% and 100%) is used to gradually dehydrate the sample. The device is then transferred from 100% ethanol to critical point dryer and dried with liquid carbon dioxide. When liquid carbon dioxide completely substitutes ethanol, temperature and pressure are adjusted so that carbon dioxide reaches critical point, where liquid phase and gaseous phase are identical. Since there is no surface tension, the delicate structures are well preserved. The sample is then coated with platinum for SEM imaging. As mentioned above, coexist of bacterial nanowire and reduce uranium is a strong evidence to support the hypothesis. But the dimension of nanowires are too small to identify using SEM. Alternatively, we can use TOF-SIMs to analyze elemental composition of the nanochannel. Since cytochromes play an important role in electron transport, they are believed to be major conductive component of bacterial nanowires. Cytochromes are heme-bound proteins, thus coexist of iron and uranium in the nanochannel will be a good indication. Unfortunately, we don’t have enough time to do this on a cracked device.

![dream4](https://raw.githubusercontent.com/tosingfung/images/master/dream4.png)

#### Figure 4

Figure.4 shows the SEM images token of a cracked device. Sphere-like structures are observed all around the device. The best guess is they are uranyl phosphate precipitates. When device is cracked open, uranyl acetate in the mineral chamber and phosphate in the bacterial chamber mix and form these insoluble spheres. Regardless of this, the SEM results contain features we expected to see and strongly support an electron conducting role of nanowires. In A and B, we can see all five nanochannels are partially or entirely filled up with filaments. The first one from the right are entirely filled and at the side of bacterial chamber, a micro colony of S.oneidensis is found. C is a closer look at the nanochannels. The egg-like structure in the middle is predicted to be reduced uranium (IV) precipitation. Figure.4D is a closer look at the mineral chamber. Reduced uranium (IV) precipitations spread all around. Numerous filaments attach to precipitated particles in a web-like manner, which is similar to the TEM image.

## Discussion

### Drawback of the current design

1. Because the device has to be cracked open for analysis, permanent bonding can not be used. Direct bonding of two glass slide requires a very clean surface and takes a long time of trial and error. Also, sometimes leakage will occur and the device has to be cracked and bond again.

2. Ordinary microscopic cover glass is much thinner than the device’s cover glass. They are not used because they are too flexible to withstand direct bonding and pressure of injection. Since thick cover glass is used, microscope with short working distance can not be used.

3. Direct bonding creates a vacuum between two glass slides. When the device is cracked, contents in the chamber will spread everywhere on the glass slide. Also, delicate structure such as nanowires may be damaged.

4. Under aerobic condition, S.oneidensis is highly adhesive to the device surface because biofilm is formed. However, when oxygen is depleted, the bacteria tend to detach and flow away.

5. After each experiment, some organic remains are secreted by the bacteria, which stick to the device and can’t be removed even by strong acid like aqua regia and nitrous acid, neither by strong detergent like SDS.

### Improvements

We make some improvements regarding the above mentioned problems:<br>
1. Pyrex borosilicate glass is used as cover glass instead. This glass has the property of being strong and thin at the same time. It can substitute ordinary glass slide as cover glass while at the same time only half as thick (5mm).

2. Using PDMS as cover layer. Pyrex can not solve the problem of drastic cracking process. PDMS, which is a biocompatible, near transparent polymer, is flexible but bond to glass tightly. Because it is elastic, the cracking simply means peeling away PDMS layer. This gentle process will not spread chamber contents or damage microstructures.

3. Concerning the SEM artifacts, next time before the device is cracked; fresh water should be used to flush both chambers. Uranium precipitate and bacterial biofilm won’t be easily flushed away, whereas the soluble uranium acetate and sodium phosphate concentration will greatly decrease. Thus even they mix afterwards; large uranyl phosphate precipitate will not form.

## Conclusion

Though this experiment doesn’t provide direct evidence that S.oneidensis produce conductive nanowires to reduce uranyl acetate, the preliminary SEM results show that nanowires are produced under oxygen limited condition, and they are highly associated with uranyl precipitation. This indicates bacterial nanowires’ critical function in mineralization. And it proves that microfluidic device can be used microbiology research; and should be used due to its numerous advantages. Although problems reside in the practical manipulation, this experiment is a pioneer in trying to combine microfluidic techniques and microbiology study, and it provides insights and new prospective in biomineralization research.

## Reference

1. Yuri A. Gorby et al. Electrically conductive bacterial nanowires produced by Shewanella oneidensis strain MR-1 and other microorganisms. PNAS. July 25, 2006. Vol. 103. No. 30.

2. Derek R. Lovley et al. Extracellular electron transfer via microbial nanowires. Nature. June 23, 2005. Vol 435.