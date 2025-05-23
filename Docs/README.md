**<h1>lycopene34: Ortholog scan of _ispA_ in pLYC72I</h1>**

What the project is about
The biology and context of the ispA gene
Why you chose your orthologs (biochemical rationale, functional hypotheses, etc.)
Any literature you consulted

The goal of this project is to do an ortholog scan of the _ispA_ gene from the lycopene-producing plasmid pLYC72I and create the necessary files to insert the orthologs found into pLYC72I. The ispA gene encodes the enzyme farnesyl diphosphate synthase(FPPS), which is essential in the MEP isoprenoid biosynthetic pathway. This pathway leads to the production of biomolecules that are very important for survival, like cholesterol for lipid membrane structure, ubiqionones for cellular respiration, or caratenoids like our lycopene.
  
FPPS is responsible for the condensation of dimethylallyl diphosphate(DMAPP) isopentenyl diphosphate(IPP) to make geranyl diphosphate(GPP), as well as the addition of another IPP to GPP to make farnesyl diphosphate(FPP). 
<img width="618" alt="Image" src="https://github.com/user-attachments/assets/5ea80372-d386-4e2b-a2fc-984ca8354c66" /> The lycopene production pathway (Furubayashi, Maiko, et al.).


**<h2>FPPS structural biochemistry</h2>**

A search into literature revealed the active site and I-VII conserved regions in FPPS structure that correlate with the efficiency of the enzyme(Szkopińska, Anna, and Danuta Płochocka.). Here are some notable regions that effect FPPS catalysis:
- First aspartic rich motif(FARM): DDXX(XX)D, located in region II, faces SARM in active pocket, binds DMAPP, GPP, or FPP, mutation results in severe loss in catalytic activity.
- Second aspartic rich motif(SARM): DDXXD, located in region VI, faces FARM in active pocket, binds IPP, mutation results in severe loss in catalytic activity.
- FQ located 4bp upstream of SARM: properly positions DMAPP or GPP for condensation with IPP, mutations result in 1,000-100,000 fold decrease in catalytic activity.
- Lysine in region I and V: aids binding of IPP, mutations result in decrease of catalytic activity. 
- Fourth and fifth postion before FARM: effects the chain length determination of the product due to its position at the "bottom" of the active pocket.

*D  = Asp and X = any amino acid


**<h2>FPPS and Biochemical Discoveries using Synthetic Biology</h2>**

In one study, synthetic DNA primers were used for **site directed mutagenesis** at fifth amino acid before FARM to make every amino acid mutation at that position(Ohnuma, Shin-ichi, et al.). WT FPPS with tyrosine in that gives FPP which is 15 carbons long as the longest product, but mutations at this site can change product specificity and extend that length. The control of this length could be desireble for industrial or biotechnical uses. 
- Longest product: a small ratio of 30 carbon long hexaprenyl diphosphate(HPP) when Tyr was mutated to Ala, Gly, or Ser. Higher concentrations of HPP with Ala or Gly, but the major product was 25 carbon geranylfarnesyl diphosphate(GFPP), effectively changing the enzyme into a GFPP synthase. *Note that HPP is two additions of IPP too many if the goal is to make lycopene or other caratenoids, as 20 carbon geranylgeranyl diphosphate(GGPP) is the intermediate that can diverge to lycopene. 
- Mutation to His also created GFPP as a major product, but Cys, Ile, Leu, Asn, Thr, Val, Asp, Glu, Phe, Lys, Met, Gln, and Arg all formed GGPP.
- Trp did not seem to change product specificity.


In another study, error prone PCR was used to create ispA gene library for **directed evolution**, and those with a red phenotype(meaning carotenoids were produced) were sequenced to identify unique mutations and analyzed by HPLC and LCMS(Lee, Pyung Cheon, et al.). 
- In vivo, the selected mutants all produced caratenoids, lycopene and tetradehydrolycopene, similarly to crtE gene, the natural enzyme that creates GGPP. This evidence strengthens the argument that ispA mutants are major producers of GGPP, a major intermediate to caratenoid biosynthesis.
- In vitro, two chosen mutants produced GGPP or a mixture of FPP and GGPP, but in combination with the in vivo results, both should be adequately producing caratenoids.
- In vivo, WT _ispA_ expectedly did not produce a significant amount of caratenoids because it is naturally unable to create a 20 carbon chain, this fact strengthened by evidence from in vitro where only FPP was detected.
- It should be noted that there was a pattern of mutations observed accross the selected mutants located near the FARM region. 
 

**<h2>Returning to our Project: Selection of the Orthologs</h2>**

Eight initial orthologs were chosen that had from 70% to 80% sequence similarity to the original ispA gene for greater sequence variation:
- _Pectobacterium carotovorum_
- _Yersinia kristensenii_
- _Pantoea agglomerans_
- _Klebsiella pneumoniae_
- _Brenneria roseae_
- _Atlantibacter subterranea_
- _Cronobacter dublinensis_
- _Buttiauxella brennerae_

A phylogenetic tree was made using species names and NCBI, and four of the least related, with each coming from different families, but all from the order _Enterobacterales_, were chosen.
- _Pectobacterium carotovorum_: Contained internal BsaI site, so removeSite in C6 tools was used to create codon-modified version.
- _Yersinia kristensenii_: No internal BsaI site, so PCR was done directly from genomic DNA
- _Pantoea agglomerans_: No internal BsaI site, so PCR was done directly from genomic DNA
- _Klebsiella pneumoniae_: Contained internal BsaI site, so removeSite in C6 tools was used to create codon-modified version.

All orthologs were inserted into plasmid pLYC72I using Golden Gate assembly, and then were transformed into Mach1 strain of _E. coli_.

**<h2>Constructs</h2>**
- pLYCpc: _P. carotovorum_ ispA, inserted via gBlock
- pLYCyk: _Y. kristensenii_ ispA, inserted via PCR
- pLYCpa: _P. agglomerans_ ispA, inserted via gBlock
- pLYCkp: _K. pneumoniae_ ispA, inserted via PCR

After further investigation of the sequences, it was found that they all had the same FARM(DDLPAMDDDD), SARM(DILD), Tyrosine residue (5bp upstream of FARM) and FQ(4bp upstream of the SARM) sequences conserved, strongly suggesting that the resulting protein for each sequence are functional FPP synthases.

Also, it could be worth mentioning the natural temperature differences in the four organisms' natural environment. For example, _K. pneumoniae_ is pathogenic in the human body which is 37 degrees C, showing favor to higher temperatures, and _Y. kristensenii_ is found almost strictly in cold enrichments(Kontiainen, Sirkka, et al.). Ohnuma, Shin-ichi, et al. showed that, _Bacillus stearothermophilus_ FPPS synthase with mutations at fifth before FARM were all thermostable, but organisms could have FPP synthases could have other subtle mutation that are optimized to their preferred temperatures, which could have implications in biotechnological and pharmaceutical settings. 


**<h2>References</h2>**

Furubayashi, Maiko, et al. “A High-Throughput Colorimetric Screening Assay for     Terpene Synthase Activity Based on Substrate Consumption.” PLoS ONE, vol. 9, no. 3, 28 Mar. 2014, doi:10.1371/journal.pone.0093317. 

Kontiainen, Sirkka, et al. “Increased Yields of Pathogenic Yersinia Enterocolitica Strains by Cold Enrichment.” Scandinavian Journal of Infectious Diseases, vol. 26, no. 6, Jan. 1994, pp. 685–691, doi:10.3109/00365549409008636.

Lee, Pyung Cheon, et al. “Directed Evolution of Escherichia Coli Farnesyl Diphosphate Synthase (ISPA) Reveals Novel Structural Determinants of Chain Length Specificity.” Metabolic Engineering, vol. 7, no. 1, Jan. 2005, pp. 18–26, doi:10.1016/j.ymben.2004.05.003. 

Ohnuma, Shin-ichi, et al. “A Role of the Amino Acid Residue Located on the Fifth Position before the First Aspartate-Rich Motif of Farnesyl Diphosphate Synthase on Determination of the Final Product.” Journal of Biological Chemistry, vol. 271, no. 48, Nov. 1996, pp. 30748–30754, doi:10.1074/jbc.271.48.30748. 

Szkopińska, Anna, and Danuta Płochocka. “Farnesyl Diphosphate Synthase; Regulation of Product Specificity.” Acta Biochimica Polonica, vol. 52, no. 1, 31 Mar. 2005, pp. 45–55, doi:10.18388/abp.2005_3485.





