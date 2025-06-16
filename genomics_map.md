graph TD
    %% --- Define styles for different node types ---
    classDef root fill:#ddeeff,stroke:#333,stroke-width:2px,font-weight:bold,font-size:16px
    classDef branch fill:#ffe8d1,stroke:#333,font-weight:bold
    classDef subbranch fill:#ffdddd,stroke:#333
    classDef category fill:#ddf3dd,stroke:#333
    classDef item fill:#f5f5f5,stroke:#333,rx:15px,ry:15px,font-size:12px
    classDef method fill:#e9d8ff,stroke:#333
    classDef math fill:#ffffd4,stroke:#333

    %% --- The Graph Structure ---
    A["Genetic Variant"]:::root

    %% --- Branch 1: Physical Nature ---
    A --> B("Variant Type <br/> (Physical Nature)"):::branch
    
    B --> B1("SNV / Indel"):::subbranch
    B1 --> B1_Cat("Functional Consequence"):::category
    B1_Cat --> B1_1("Missense"):::item
    B1_Cat --> B1_2("Nonsense (LoF)"):::item
    B1_Cat --> B1_3("Frameshift (LoF)"):::item
    B1_Cat --> B1_4("Splice Site"):::item
    B1_Cat --> B1_5("Synonymous"):::item

    B --> B2("Structural Variation (SV)"):::subbranch
    B2 --> B2_Cat("SV Subtypes"):::category
    B2_Cat --> B2_1("Deletion / Duplication"):::item
    B2_Cat --> B2_2("Inversion"):::item
    B2_Cat --> B2_3("Translocation"):::item

    %% --- Branch 2: Clinical Interpretation ---
    A --> C("Variant Interpretation <br/> (Clinical Significance)"):::branch
    
    C --> C1("ACMG/AMP <br/> 5-Tier Classification"):::subbranch
    C1 --> C1_1("Pathogenic"):::item
    C1 --> C1_2("Likely Pathogenic"):::item
    C1 --> C1_3("VUS"):::item
    C1 --> C1_4("Likely Benign"):::item
    C1 --> C1_5("Benign"):::item

    C --> C2("Evidence Types"):::subbranch
    C2 --> C2_1("Population Data"):::category
    C2_1 --> C2_1_Item("Allele Frequency (MAF) <br/> from gnomAD"):::item
    
    C2 --> C2_2("Computational Data"):::category
    C2_2 --> C2_2_Item1("<i>In Silico</i> Predictors <br/> (SIFT, CADD, etc.)"):::item
    C2_2 --> C2_2_Item2("Constraint Scores <br/> (pLI, LOEUF)"):::item

    C2 --> C2_3("Functional Data"):::category
    C2_3 --> C2_3_Item("Experimental Assays <br/> (e.g., RNA/protein analysis)"):::item

    C2 --> C2_4("Segregation Data"):::category
    C2_4 --> C2_4_Item("Family Studies, <br/> <i>De Novo</i> Status"):::item

    C --> C3("Analytical Methods"):::subbranch
    C3 --> C3_1("GWAS"):::method
    C3_1 --> C3_1_1("Polygenic Score (PGS)"):::method
    C3_1 --> C3_1_2("Linkage Disequilibrium (LD)"):::item

    C3 --> C3_2("AI for Variant <br/> Prioritization"):::method
    C3_2 --> C3_2_1("Mathematical Frameworks"):::math
    C3_2_1 --> C3_2_1_1("Deep Learning / NNs"):::math
    C3_2_1 --> C3_2_1_2("Graph Theory (e.g., GNNs)"):::math