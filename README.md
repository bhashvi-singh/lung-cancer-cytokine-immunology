# lung-cancer-cytokine-immunology
**Lung Cancer Cytokine Analysis**

A literature-based exploratory analysis of cytokines in lung cancer progression and metastasis.

---

## Overview

This repository contains an exploratory, literature-derived analysis examining the role of cytokines in lung cancer progression, metastasis, and immune modulation. Using recent peer-reviewed studies, cytokine-related findings were structured into a curated dataset and analysed using R to identify recurring biological patterns and generate testable hypotheses relevant to cancer immunology.

---

## Research Questions

The project addresses three core hypotheses:

**1. Early progression**  
Specific cytokines associated with lung cancer progression may serve as candidate biomarkers for early-stage disease detection.

**2. Metastatic prioritisation**  
Cytokines associated with lung cancer metastasis highlight key signalling pathways that can be targeted to study metastatic mechanisms and inform immunotherapeutic strategies.

**3. Immune directionality**  
Cytokines involved in lung cancer metastasis predominantly exhibit tumour-promoting or immunosuppressive effects rather than tumour-inhibitory roles.

---

## Data Source

- Curated from recent (last ~2 years) peer-reviewed review and mechanistic studies  
- Focused on cytokines, chemokines, and immunoregulatory signalling in lung cancer  
- Data manually extracted and structured using Google Sheets, then imported into R  

### Note
This dataset is literature-derived and does not contain patient-level or clinical trial data.

---

## Methods

- Manual literature screening and annotation  
- Classification of cytokines by:
  - Disease context (progression vs metastasis)
  - Biological process
  - Direction of effect (tumour-promoting, inhibitory, context-dependent)
  - Cytokine group (pro-inflammatory, regulatory, chemokine)
- Exploratory data analysis and visualisation in R (`dplyr`, `ggplot2`)
- Cytokines were classified as progression-associated or metastasis-associated based on manual literature annotation, where ‘Yes’ indicated explicit metastatic involvement, ‘No’ indicated non-metastatic or primary tumour contexts, and ‘Context’ reflected mixed or conditional evidence.

---

## Analysis Workflow

### Cytokines associated with lung cancer progression

## Cytokines associated with lung cancer progression

Progression-associated cytokines were identified from non-metastatic study contexts.

```r
progression_data <- cytokine_data %>%
  filter(Metastasis_link == "No")

progression_summary <- progression_data %>%
  count(Cytokine, sort = TRUE)

Full analysis: scripts/analysis_progression.R

Figure 1. Cytokines reported in lung cancer progression (exploratory).

<img width="1074" height="888" alt="Figure 1 lung cancer analysis" src="https://github.com/user-attachments/assets/eb28d45b-77dd-43b2-aa72-51d2284e0713" />



metastasis_data <- cytokine_data %>%
  filter(Metastasis_link == "Yes")

metastasis_summary <- metastasis_data %>%
  count(Cytokine, sort = TRUE)

Full analysis: scripts/analysis_progression.R


Figure 2. Metastasis-associated cytokines prioritised as candidate immunotherapeutic targets.

<img width="1074" height="888" alt="Figure 2 lung cancer analysis" src="https://github.com/user-attachments/assets/f5d3c887-1e76-4e99-8b7d-96d7e1fa2459" />


metastasis_direction <- metastasis_data %>%
  count(Direction) %>%
  mutate(proportion = n / sum(n))

Full analysis: scripts/analysis_directionality.R

Figure 3. Directionality of cytokine effects in lung cancer metastasis.


<img width="1074" height="888" alt="Figure 3 lung cancer analysis" src="https://github.com/user-attachments/assets/ade37079-d1d3-47b9-91e8-6c47943dfa37" />




Analysis Scripts
analysis_progression.R
Identifies cytokines associated with lung cancer progression and evaluates their potential relevance as early-stage disease markers.

analysis_metastasis_targets.R
Analyses metastasis-associated cytokines and prioritises candidates based on recurrence and immunotherapeutic relevance.

analysis_directionality.R
Examines the directionality of cytokine effects in metastatic lung cancer, focusing on tumour-promoting versus inhibitory roles.

Figures
fig_progression_cytokines.png
Distribution of cytokines reported in lung cancer progression-related contexts (exploratory).

fig_metastasis_targets.png
Metastasis-associated cytokines prioritised as candidate targets for mechanistic and immunotherapeutic studies.

fig_metastasis_directionality.png
Directionality of cytokine effects in lung cancer metastasis, highlighting immune suppression and tumour-promoting biases.

Key Findings
Cytokine signalling is consistently implicated in lung cancer progression, but evidence for early-stage biomarker dominance remains limited.

Metastasis-associated cytokines show stronger recurrence and pathway enrichment, supporting their prioritisation for mechanistic and immunotherapeutic research.

Metastatic contexts are characterised by a skew towards tumour-promoting and immunosuppressive cytokine activity.

Limitations
Small, literature-derived dataset

Dependence on study-level interpretations

No clinical validation or patient-level inference

Cytokine redundancy and context dependence are not fully captured

Repository Structure
kotlin
Copy code
├── data/
│   └── lung_cancer_cytokine_literature.csv
├── scripts/
│   ├── analysis_progression.R
│   ├── analysis_metastasis_targets.R
│   └── analysis_directionality.R
├── figures/
│   ├── fig_progression_cytokines.png
│   ├── fig_metastasis_targets.png
│   └── fig_metastasis_directionality.png
└── README.md
Tools
R (tidyverse)

Google Sheets (data curation)

ggplot2 (visualisation)

Future Directions
Expansion to include more primary studies and meta-analyses
Integration with single-cell or bulk transcriptomic datasets
Comparative analysis with immune checkpoint and T-cell signalling pathways
Extension to other cancer types

References
Mechanism of interleukin-6 cytokine family in bone metastasis of lung cancer and prospects for its application.
Therapeutic targeting of TGF-β in lung cancer.
The novel functions of chemokines in lung cancer progression.
The distinct roles of IL-37 and IL-38 in non-small cell lung carcinoma and their clinical implications.

Author
Bhashvi Singh
Background in immunology and molecular biology with research interests in cancer immunology and immune signalling.
