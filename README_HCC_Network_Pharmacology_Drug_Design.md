# Network Pharmacology and Computational Drug Designing of Hepatocellular Carcinoma

## Project Overview

This project applies a **network pharmacology and structure-based
computational drug-designing workflow** to investigate potential
therapeutic targets and ligand interactions associated with
**hepatocellular carcinoma (HCC)**.

The study combines disease-gene collection, protein-coding gene
filtering, protein--protein interaction (PPI) network analysis, hub-gene
identification, functional and pathway enrichment, target-protein
selection, ligand screening, ADME/toxicity assessment, and molecular
docking.

The final structure-based analysis focuses on **PIK3CA (PI3Kα)** as the
selected target protein and evaluates three turmeric-derived
curcuminoids:

-   Curcumin
-   Demethoxycurcumin
-   Bisdemethoxycurcumin

The workflow and results summarized here are based on the submitted
project report.

------------------------------------------------------------------------

## Project Information

  Category              Details
  --------------------- -------------------------------------------------------
  Project               Network Pharmacology for Computational Drug Designing
  Disease               Hepatocellular carcinoma (HCC)
  Disease database      GeneCards
  PPI database          STRING
  Network analysis      Cytoscape + cytoHubba
  Hub-gene algorithm    Maximal Clique Centrality (MCC)
  Enrichment analysis   DAVID
  Selected target       PIK3CA / PI3Kα
  Target PDB            4JPS
  PDB resolution        2.20 Å
  Ligand source         PubChem
  ADME analysis         SwissADME
  Toxicity prediction   ProTox-3
  Docking               AutoDock
  Visualization         Discovery Studio Visualizer

------------------------------------------------------------------------

# 1. Background

## Network Pharmacology

Network pharmacology is a systems-biology-based approach to drug
discovery.

Traditional drug discovery is often described using a simplified:

``` text
One drug → One target → One disease
```

Network pharmacology instead considers:

``` text
Drug
 │
 ├── Target 1
 ├── Target 2
 ├── Target 3
 └── Multiple biological pathways
             │
             ▼
           Disease
```

This approach considers diseases as complex biological systems involving
interconnected genes, proteins, signaling pathways, and cellular
processes.

The project report highlights that:

-   A disease may involve hundreds of genes.
-   A drug may affect multiple proteins.
-   Proteins participate in interconnected signaling pathways.
-   Network-level analysis can therefore help prioritize biologically
    relevant therapeutic targets.

## Advantages

The reported advantages of network pharmacology include:

-   Studying diseases as biological systems rather than isolated
    targets.
-   Identifying multiple therapeutic targets.
-   Supporting drug repurposing.
-   Integrating genomics, proteomics, and metabolomics.
-   Reducing time and cost during early-stage drug discovery.
-   Complementing molecular docking by prioritizing relevant targets.

------------------------------------------------------------------------

# 2. Objectives

The project objectives were to:

1.  Identify disease-related genes and proteins.
2.  Predict potential therapeutic targets.
3.  Construct and analyze biological interaction networks.
4.  Identify hub genes and key signaling pathways.
5.  Study protein--protein interactions.
6.  Predict drug--target interactions.
7.  Support molecular docking and virtual screening.
8.  Facilitate multi-target drug discovery.
9.  Reduce the time and cost associated with early drug-development
    research.
10. Improve understanding of disease mechanisms for therapeutic design.

------------------------------------------------------------------------

# 3. Disease Selection: Hepatocellular Carcinoma

**Hepatocellular carcinoma (HCC)** is the most common type of primary
liver cancer and is described in the report as a major global health
challenge.

The project therefore used HCC-associated genes as the starting point
for network pharmacology analysis.

------------------------------------------------------------------------

# 4. Complete Computational Workflow

``` text
                    HEPATOCELLULAR CARCINOMA
                              │
                              ▼
                    Disease Gene Collection
                         GeneCards
                              │
                              ▼
                  Protein-Coding Gene Filtering
                              │
                              ▼
                     STRING PPI Network
                              │
                              ▼
                         Cytoscape
                              │
                              ▼
                  cytoHubba / MCC Analysis
                              │
                              ▼
                     Top Hub Genes
                              │
                              ▼
                    DAVID Enrichment
                       │          │
                       ▼          ▼
                     GO          KEGG
                              │
                              ▼
                       Target Selection
                              │
                              ▼
                     PIK3CA / PI3Kα
                              │
                              ▼
                     PDB Structure 4JPS
                              │
                              ▼
                    Ligand Collection
                         PubChem
                              │
                              ▼
                     SwissADME + ProTox
                              │
                              ▼
             Curcumin / Demethoxycurcumin /
                  Bisdemethoxycurcumin
                              │
                              ▼
                       Molecular Docking
                          AutoDock
                              │
                              ▼
                    Interaction Analysis
                   Discovery Studio
                              │
                              ▼
                  Predicted Ligand–Target
                       Interactions
```

------------------------------------------------------------------------

# 5. Disease Gene Collection

Disease-associated genes were collected from **GeneCards** using the
query:

``` text
Hepatocellular carcinoma
```

The report records approximately **15,715 entries** across different
gene categories.

The project subsequently filtered the retrieved list to retain
**protein-coding genes**.

The report describes the GeneCards search as including protein-coding
genes, RNA genes, pseudogenes, and other functional elements.

------------------------------------------------------------------------

# 6. Protein-Coding Gene Filtering

To focus the downstream protein-interaction and structure-based analyses
on genes capable of producing proteins, the project retained
protein-coding genes.

The report states that the following categories were excluded:

-   Long non-coding RNAs (lncRNAs)
-   microRNAs (miRNAs)
-   Pseudogenes
-   Other non-coding transcripts

The filtered gene list was then used for:

``` text
Protein-coding genes
       │
       ├── PPI network construction
       ├── Hub-gene identification
       ├── Functional enrichment
       └── Target-protein selection
```

------------------------------------------------------------------------

# 7. STRING Protein--Protein Interaction Network

The filtered genes were submitted to **STRING** for protein--protein
interaction analysis.

### STRING parameters reported

  Parameter                   Setting
  --------------------------- ----------------
  Organism                    *Homo sapiens*
  Taxonomic ID                9606
  Minimum interaction score   0.4
  Confidence                  Medium
  Disconnected nodes          Hidden

The resulting network represented functional relationships among
HCC-associated proteins.

The STRING network was subsequently imported into Cytoscape for network
analysis.

------------------------------------------------------------------------

# 8. Cytoscape Network Analysis

The STRING-derived PPI network was analyzed in **Cytoscape**.

The **cytoHubba** plugin was used to identify highly connected/central
nodes.

The selected network-ranking method was:

``` text
Maximal Clique Centrality (MCC)
```

------------------------------------------------------------------------

# 9. Hub Gene Identification

The report identified the following top 10 hub genes:

    Rank Hub Gene   Reported relevance
  ------ ---------- ------------------------------------------------
       1 TP53       Tumor suppressor; frequently mutated in HCC
       2 PTEN       Tumor suppressor regulating PI3K/AKT signaling
       3 KRAS       Oncogene involved in cell proliferation
       4 PIK3CA     Activates PI3K/AKT signaling
       5 CDKN2A     Cell-cycle regulator
       6 CTNNB1     Wnt/β-catenin signaling
       7 MYC        Oncogene promoting tumor growth
       8 HRAS       RAS-family oncogene
       9 ATM        DNA-damage-response protein
      10 NRAS       RAS-family oncogene

------------------------------------------------------------------------

# 10. Functional Enrichment Analysis

The identified hub genes were subjected to functional annotation using
**DAVID**.

Gene Ontology (GO) analysis was considered in three major categories:

### Biological Process (BP)

Describes biological processes in which the genes participate.

### Molecular Function (MF)

Describes molecular activities associated with the gene products.

### Cellular Component (CC)

Describes the cellular locations associated with the gene products.

The DAVID functional annotation analysis also included categories such
as:

-   GO terms
-   KEGG pathways
-   InterPro
-   UniProt keywords
-   Protein domains
-   Disease-related annotations

------------------------------------------------------------------------

# 11. KEGG Pathway Analysis

KEGG enrichment was used to investigate biological pathways associated
with the selected hub genes.

The report discusses HCC-associated signaling involving:

-   EGFR/IGF1R--PI3K--Akt--mTOR
-   RAS--MAPK
-   Wnt/β-catenin
-   TGF-β
-   p53

These pathways were used to provide a systems-level context for HCC
progression and to help prioritize a target for downstream molecular
docking.

------------------------------------------------------------------------

# 12. Target Protein Selection

Based on:

1.  PPI network analysis,
2.  MCC hub-gene identification, and
3.  KEGG pathway analysis,

**PIK3CA** was selected as the target protein for molecular docking.

### Target

``` text
PIK3CA
↓
Phosphatidylinositol-4,5-bisphosphate
3-kinase catalytic subunit alpha
↓
PI3Kα
```

The report describes PIK3CA as an important component of the PI3K/Akt
signaling pathway, which regulates processes including:

-   Cell proliferation
-   Cell survival
-   Cell growth
-   Metabolism
-   Apoptosis

The project therefore selected PIK3CA for structure-based ligand
investigation.

------------------------------------------------------------------------

# 13. Protein Structure Retrieval

The three-dimensional structure of human PIK3CA was retrieved from the
**Protein Data Bank**.

### Structure used

  Parameter        Value
  ---------------- ---------------------------------------------
  Protein          PIK3CA / PI3Kα
  PDB ID           4JPS
  Resolution       2.20 Å
  Structure type   Experimentally determined crystal structure

The report selected 4JPS because it provides an experimentally
determined structure suitable for molecular docking and contains a
characterized binding region.

------------------------------------------------------------------------

# 14. Ligand Selection

The project investigated phytochemicals reported from **Curcuma longa**.

Ten compounds were initially considered:

  Compound                 PubChem CID   Molecular Weight
  ---------------------- ------------- ------------------
  Curcumin                      969516        368.4 g/mol
  Demethoxycurcumin            5469424        338.4 g/mol
  Bisdemethoxycurcumin         5315472        308.3 g/mol
  ar-Turmerone                  160512       216.32 g/mol
  Beta-turmerone                196216       218.33 g/mol
  Alpha-turmerone              6434375       273.37 g/mol
  Germacrone                   6436348       218.33 g/mol
  Curdione                    14106072       236.35 g/mol
  Cyclocurcumin                5318992        728.8 g/mol
  Calebin A                     637429        384.4 g/mol

------------------------------------------------------------------------

# 15. Ligand Screening Strategy

The initial phytochemical set was screened using:

``` text
PubChem
   │
   ├── Structural information
   │
   ▼
SwissADME
   │
   ├── Lipinski Rule of Five
   ├── GI absorption
   ├── Bioavailability
   ├── Water solubility
   ├── Drug-likeness
   ├── PAINS alerts
   ├── Brenk alerts
   ├── Synthetic accessibility
   └── BOILED-Egg model
   │
   ▼
ProTox-3
   │
   ├── LD50
   ├── Toxicity class
   ├── Hepatotoxicity
   ├── Carcinogenicity
   ├── Mutagenicity
   ├── Immunotoxicity
   └── Cytotoxicity
   │
   ▼
Selected docking ligands
```

------------------------------------------------------------------------

# 16. Selected Ligands

Based on the report's ADME and toxicity assessment, three compounds were
selected for molecular docking:

1.  **Curcumin**
2.  **Demethoxycurcumin**
3.  **Bisdemethoxycurcumin**

The report describes these compounds as showing favorable overall
characteristics, including reported compliance with Lipinski's Rule of
Five, favorable gastrointestinal absorption, acceptable bioavailability,
suitable solubility/drug-likeness characteristics, and comparatively
favorable predicted toxicity profiles.

------------------------------------------------------------------------

# 17. Excluded Compounds

### Calebin A

Calebin A was not selected for docking because the report states that
there was comparatively less evidence for its activity against HCC and
the PI3K signaling pathway, as well as fewer docking and experimental
studies validating interaction with PI3K.

### Cyclocurcumin

Cyclocurcumin was excluded according to the report because of limited
evidence supporting its anticancer activity against HCC and relatively
limited research targeting the PI3K pathway.

------------------------------------------------------------------------

# 18. Molecular Docking Setup

The target receptor used for the docking experiments was:

``` text
Receptor: PIK3CA / PI3Kα
PDB: 4JPS
```

The site-specific docking coordinates reported in the project were:

  Parameter            Value
  ----------- --------------
  X center            -1.319
  Y center            -9.513
  Z center            16.948
  Grid size     40 × 40 × 40

The binding-site center was derived from the native ligand **1LT**
according to the report.

------------------------------------------------------------------------

# 19. Curcumin Docking

Curcumin was docked against PIK3CA (4JPS).

### Reported interacting residues

The report identifies the following residues in the Curcumin binding
region:

``` text
TRP A:700
HIS A:665
VAL A:853
GLN A:859
PHE A:930
ILE A:972
VAL A:950
ILE A:900
LYS A:802
ASP A:933
ILE A:848
SER A:774
MET A:772
ARG A:852
ASN A:853
SER A:854
MET A:922
```

### Docking result

The reported docking table gives:

    Rank   Energy (kcal/mol)   Cluster RMSD
  ------ ------------------- --------------
       1               -3.72           0.00
       2               -3.64           0.00

The report states that each run formed its own cluster and therefore the
lowest-energy conformation was selected.

### Selected Curcumin pose

``` text
Best reported energy:
-3.72 kcal/mol
```

The report describes the interaction profile as involving:

-   Hydrogen bonding
-   Hydrophobic interactions
-   π--anion interactions
-   π--alkyl interactions
-   van der Waals forces

It specifically reports conventional hydrogen bonds involving **Lys943**
and **Gln1014**, along with an unfavorable acceptor--acceptor
interaction involving **Gln579**.

------------------------------------------------------------------------

# 20. Interpretation of the Curcumin Docking Structure

The project report describes the docked Curcumin structure as:

-   Located inside a cavity/binding region of the protein.
-   Partially buried within the protein structure.
-   Adopting an elongated conformation.
-   Positioned near α-helices and loops.
-   Surrounded by protein secondary-structure elements.

These structural observations were used to describe how Curcumin
occupies the predicted PI3Kα binding region.

The report also notes that the **-3.72 kcal/mol** docking score
represents a relatively weak predicted binding affinity compared with
potent PI3K inhibitors.

------------------------------------------------------------------------

# 21. Demethoxycurcumin Docking

Demethoxycurcumin was docked using the same receptor and reported
docking region.

### Docking parameters

``` text
Receptor: 4JPS
Grid center: (-1.319, -9.513, 16.948)
Grid size: 40 × 40 × 40
```

### Reported docking score

``` text
-6.22 kcal/mol
```

The report states that the best docking pose was **Cluster 1,
Conformation 1**.

### Reported interacting residues

``` text
TRP A:700
GLN A:959
HIS A:955
VAL A:850
VAL A:853
ARG A:852
ASN A:853
SER A:854
MET A:922
PHE A:930
ASP A:933
ILE A:800
ILE A:932
ILE A:848
LYS A:802
ARG A:770
```

The interaction visualization was generated using Discovery Studio
Visualizer.

------------------------------------------------------------------------

# 22. Bisdemethoxycurcumin Docking

Bisdemethoxycurcumin was docked using the same receptor and grid
configuration.

### Docking parameters

``` text
Receptor: 4JPS
Grid center: (-1.319, -9.513, 16.948)
Grid size: 40 × 40 × 40
```

### Reported docking score

``` text
-6.11 kcal/mol
```

The report describes the docking pose as occupying the predefined PI3Kα
active-site region.

### Reported interactions

The interaction profile includes:

-   Conventional hydrogen bonding
-   π--sigma interaction
-   π--alkyl interaction
-   π--sulfur interaction
-   van der Waals interactions

### Reported interacting residues

``` text
ASP A:933
LYS A:802
ILE A:932
ILE A:848
PHE A:930
VAL A:851
ILE A:800
MET A:772
MET A:922
VAL A:850
TYR A:836
TRP A:780
GLU A:849
LEU A:807
SER A:774
SER A:854
```

------------------------------------------------------------------------

# 23. Docking Results Summary

  Ligand                 Target           PDB      Reported docking energy
  ---------------------- ---------------- ------ -------------------------
  Curcumin               PI3Kα / PIK3CA   4JPS              -3.72 kcal/mol
  Demethoxycurcumin      PI3Kα / PIK3CA   4JPS              -6.22 kcal/mol
  Bisdemethoxycurcumin   PI3Kα / PIK3CA   4JPS              -6.11 kcal/mol

The reported docking scores represent computational predictions
generated by the docking workflow and should not be interpreted as
experimentally measured binding affinities.

------------------------------------------------------------------------

# 24. Overall Interaction Analysis

The project investigated multiple types of non-covalent ligand--protein
interactions, including:

``` text
Hydrogen bonds
      +
Hydrophobic interactions
      +
van der Waals interactions
      +
π–alkyl interactions
      +
π–sigma interactions
      +
π–sulfur interactions
      +
π–π / π–anion interactions
```

Discovery Studio Visualizer was used to display the predicted
interactions in two-dimensional diagrams, while three-dimensional
structures were used to inspect ligand positioning within the binding
pocket.

------------------------------------------------------------------------

# 25. Key Computational Findings

The network analysis identified multiple HCC-associated hub genes,
including:

``` text
TP53
PTEN
KRAS
PIK3CA
CDKN2A
CTNNB1
MYC
HRAS
ATM
NRAS
```

PIK3CA was subsequently selected as the structure-based docking target
based on its hub-gene status and association with the PI3K/Akt signaling
pathway and HCC-related pathway analysis.

Three curcuminoids were then selected for docking following ADME and
toxicity screening.

The reported docking energies were:

``` text
Curcumin              → -3.72 kcal/mol
Demethoxycurcumin     → -6.22 kcal/mol
Bisdemethoxycurcumin  → -6.11 kcal/mol
```

------------------------------------------------------------------------

# 26. Project Workflow in One-Line Form

``` text
HCC → GeneCards → Protein-Coding Filtering → STRING → Cytoscape → cytoHubba/MCC → Hub Genes → DAVID GO/KEGG → PIK3CA → PDB 4JPS → PubChem Ligands → SwissADME → ProTox-3 → Curcuminoid Selection → AutoDock → Docking Scores → Discovery Studio Interaction Analysis
```

------------------------------------------------------------------------

# 27. Tools and Resources

## Cytoscape

Used for PPI network visualization and network analysis.

https://cytoscape.org/

## GeneCards

Used for disease-associated gene collection.

https://www.genecards.org/

## STRING

Used for protein--protein interaction network construction.

https://string-db.org/

## DAVID

Used for functional annotation and enrichment analysis.

https://davidbioinformatics.nih.gov/

## SwissADME

Used for ADME and drug-likeness analysis.

https://www.swissadme.ch/

## ProTox-3

Used for computational toxicity prediction.

https://tox.charite.de/protox3/

## Protein Data Bank

Used to obtain the experimentally determined PIK3CA structure.

https://www.rcsb.org/

## PubChem

Used for ligand structural information.

https://pubchem.ncbi.nlm.nih.gov/

## AutoDock

Used for molecular docking.

https://autodock.scripps.edu/

## Discovery Studio Visualizer

Used for protein--ligand interaction visualization.

------------------------------------------------------------------------

# 28. Suggested Repository Structure

A GitHub repository for this project can be organized as follows:

``` text
HCC-Network-Pharmacology-Drug-Design/
│
├── README.md
│
├── data/
│   ├── genecards/
│   ├── ppi/
│   ├── protein/
│   │   └── 4JPS.pdb
│   └── ligands/
│
├── network_analysis/
│   ├── cytoscape/
│   ├── cytohubba/
│   └── ppi_network/
│
├── enrichment/
│   ├── GO/
│   └── KEGG/
│
├── adme/
│   ├── swissadme/
│   └── toxicity/
│
├── docking/
│   ├── curcumin/
│   ├── demethoxycurcumin/
│   └── bisdemethoxycurcumin/
│
├── visualization/
│   ├── network/
│   ├── docking_3D/
│   └── interactions_2D/
│
├── figures/
│
├── results/
│
└── report/
    └── computational_drug_design_report.pdf
```

------------------------------------------------------------------------

# 29. Reproducibility Notes

For a fully reproducible computational project, the repository should
ideally include:

-   Original GeneCards gene list.
-   Protein-coding filtered gene list.
-   STRING input/output files.
-   Cytoscape network file.
-   cytoHubba MCC results.
-   DAVID GO results.
-   DAVID KEGG results.
-   PIK3CA PDB structure or accession information.
-   Original ligand structures.
-   SwissADME outputs.
-   ProTox-3 outputs.
-   AutoDock configuration files.
-   Docking log/DLG files.
-   Docked PDBQT files.
-   Protein--ligand complex structures.
-   Discovery Studio interaction figures.
-   PyMOL session files where applicable.
-   Exact software versions and parameters.

This allows another researcher to reproduce and independently inspect
the computational workflow.

------------------------------------------------------------------------

# 30. Limitations

This project is a **computational drug-design study**. The results
represent predictions rather than experimental confirmation.

Important limitations include:

-   GeneCards disease association scores can include heterogeneous
    evidence sources.
-   PPI networks represent reported/predicted functional associations
    and do not necessarily prove direct physical interaction in every
    biological context.
-   Hub-gene centrality does not by itself establish that a gene is a
    therapeutic target.
-   Docking scores are computational estimates and are not equivalent to
    experimentally measured binding constants.
-   ADME and toxicity predictions are in silico predictions.
-   Docking does not fully capture protein flexibility, solvent effects,
    cellular context, or pharmacodynamics.
-   Experimental validation is required to establish biological activity
    and therapeutic efficacy.

------------------------------------------------------------------------

# 31. Conclusion

This project implemented a multi-stage **network pharmacology and
computational drug-design workflow** for hepatocellular carcinoma.

HCC-associated genes were collected using GeneCards and filtered for
protein-coding genes. The resulting genes were analyzed through STRING
and Cytoscape, with cytoHubba MCC used to identify hub genes. Functional
and pathway enrichment was then performed using DAVID.

**PIK3CA/PI3Kα** was selected as the target for molecular docking, and
the experimentally determined **4JPS** structure was used for
structure-based analysis.

Ten *Curcuma longa*-derived phytochemicals were initially considered,
followed by ADME and toxicity screening. Curcumin, demethoxycurcumin,
and bisdemethoxycurcumin were selected for docking.

The reported docking energies were:

``` text
Curcumin              -3.72 kcal/mol
Demethoxycurcumin     -6.22 kcal/mol
Bisdemethoxycurcumin  -6.11 kcal/mol
```

The docking analysis identified multiple predicted non-covalent
interactions within the PI3Kα binding region.

Overall, the project demonstrates how **network-level disease analysis
can be integrated with ADME/toxicity screening and molecular docking**
to prioritize candidate target--ligand interactions for further
investigation.

The computational findings provide a basis for additional validation,
but experimental studies would be required to establish biological
activity, target inhibition, and therapeutic potential.

------------------------------------------------------------------------

# 32. Author

**Tahreem Waris**\
BS Bioinformatics\
University of Agriculture (UAF)

**Project:** Network Pharmacology for Computational Drug Designing\
**Year:** 2026

**Submitted to:** Dr. Rubab Zahra Naqvi
