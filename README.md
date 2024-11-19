# RepeatMasker library : CHM13
```
RepeatMasker was developed by Arian Smit and Robert Hubley
Please refer to: Smit, AFA, Hubley, R. & Green, P "RepeatMasker" at
http://www.repeatmasker.org
```
The completion of the human genome (T2T-CHM13 project) allowed for a complete repeat analysis of the centromeres and telomeres therein. In order investigate new repetitive elements, a new repeat pipeline was developed (<b>Fig 1</b>)<sup>1</sup>. 

This RepeatMasker-based pipeline was used to generate new models not only the T2T-CHM13 project, but also for the human Y chromosome<sup>2</sup>, the X and Y chromosomes of apes<sup>3</sup>, and ape autosomes<sup>4</sup>. The investigation of these genomes not only allowed for the discovery of novel satellite sequences, but also to update the taxonomic label of select repeats. The combined repeat library discovered by all of these analyses for investigation of <b>human repeats</b> can be found in this repository. 

![Untitled presentation](https://github.com/user-attachments/assets/e1bf5099-9786-4905-9ccb-598722b9eb25)

<b> Figure 1 : A discovery workflow afforded comprehensive annotations of a complete human genome as part of Hoyt et al. 2022. </b> Workflow implemented to obtain updated repeat models and teh derivation of RepeatMasker Annoatations 2 (RMv2), consisting of combined and polished RM annotations submitted to Dfam <b> (A) </b> and applied to T2T-CHM13 and GRCh38 as RepeatMaskerv2 tracks. Workflow consisted of multiple iterations of RepeatMasker and RepeatModeler. <b> (A) </b> The components intersected during manual curation <b> (B) </b> include CAT/gene annotations, segmental duplications, repeates masked using DFam (v3.3) repeat models, tandem repeat arrays identified as gaps in annotations >10 kbp and overlap with ULTRA tandem repeat models. <b> (C) </b> Repeat model polishing was derived from a compilation of RepeatMasker output (previous repeat models; HM1) RepeatMasker 2 output (updated models; RM annotation 2), and gap entires. Additional and previously unclassified family entries identified from RMv2 were further filtered following multiple seqence alignment (MSA) among members of the predicted category.

<b>Building a custom repeat library for human repeat analyses</b><br>
Some human models produced as part of the T2T-CHM13 analysis<sup>1</sup> are part of the Dfam<sup>5</sup> database, released in v3.6. In order to produce a non-redundant repeat library for use in RepeatMasker and include the models produced for the human Y<sup>2</sup> and ape autosomal and X/Y<sup>3,4</sup> analyses, the following pipeline is suggested:

1. Make a directory for the new libraries
&nbsp;&nbsp;&nbsp;&nbsp;<br>$ mkdir ~/TEproject/RMplusSpeciesLib/
2. Copy the RepeatMasker libraries to a new location
&nbsp;&nbsp;&nbsp;&nbsp;<br>$ cp -r /usr/local/RepeatMasker-4.1.4/Libraries/ ~/TEproject/RMplusSpeciesLib/<br>
&nbsp;&nbsp;&nbsp;&nbsp;<b>NOTE:</b> RepeatMasker v4.1.4 and v4.1.5 come precompiled libraries which include the human repeats submitted to Dfam as part of the T2T-CHM13 project<sup>1</sup>
4. Append the .embl file to the existing library
&nbsp;&nbsp;&nbsp;&nbsp;<br>$ famdb.py -i ~/TEproject/RMplusSpeciesLib/Libraries/RepeatMaskerlib.h5 append
humanAutoXYape.embl --name 'your_favorite_name'<br>
&nbsp;&nbsp;&nbsp;&nbsp;<b>NOTE:</b> the stage and taxonomic label information is included for each entry<br>
&nbsp;&nbsp;&nbsp;&nbsp;famdb.py included as part of the RepeatMasker package.<br>
&nbsp;&nbsp;&nbsp;&nbsp;For additional famdb.py usage, please refer to the Dfam-consortium [FamDB github page](https://github.com/Dfam-consortium/FamDB)
5. Run RepeatMasker with the appended library
&nbsp;&nbsp;&nbsp;&nbsp;<br>$ RepeatMasker -libdir ~/TEproject/RMplusSpeciesLib/Libraries/ -s -species
your_favorite_species yourGenome.fa

Please refer to the [RepeatMasker manual](https://www.repeatmasker.org/webrepeatmaskerhelp.html#reading) for additional program settings.

<b>References</b>

1. Hoyt, S. J. et al (2022). From telomere to telomere: The transcriptional and epigenetic state of human repeat elements. Science (New York, N.Y.), 376(6588), eabk3112. https://doi.org/10.1126/science.abk3112
2. Rhie, A. et al (2023). The complete sequence of a human Y chromosome. Nature, 621(7978), 344–354. https://doi.org/10.1038/s41586-023-06457-y
3. Makova, K. D. et al (2023). The Complete Sequence and Comparative Analysis of Ape Sex Chromosomes. bioRxiv : the preprint server for biology, 2023.11.30.569198. https://doi.org/10.1101/2023.11.30.569198
4. Yoo, D et al (2024). Complete sequencing of ape genomes. bioRxiv 2024.07.31.605654; doi: https://doi.org/10.1101/2024.07.31.605654
5. Storer, J et all (2021). The Dfam community resource of transposable element families, sequence models, and genome annotations. Mobile DNA 12:2 doi: https://doi.org/10.1186/s13100-020-00230-y
   
