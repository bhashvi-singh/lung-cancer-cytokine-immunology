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

---

## Analysis Workflow

### Cytokines associated with lung cancer progression

Progression-associated cytokines were identified by filtering studies not explicitly linked to metastasis and counting recurring cytokines.

```r
progression_data <- cytokine_data %>%
  filter(Metastasis_link == "Progression")

progression_summary <- progression_data %>%
  count(Cytokine, sort = TRUE)
Full analysis: scripts/analysis_progression.R

Figure 1. Cytokines reported in lung cancer progression (exploratory).



Metastasis-associated cytokines and target prioritisation
Metastasis-linked studies were used to identify cytokines recurrently implicated in lung cancer dissemination.

r
Copy code
metastasis_data <- cytokine_data %>%
  filter(Metastasis_link == "Metastasis")

metastasis_summary <- metastasis_data %>%
  count(Cytokine, sort = TRUE)
Full analysis: scripts/analysis_metastasis_targets.R

Figure 2. Metastasis-associated cytokines prioritised as candidate immunotherapeutic targets.



Directionality of cytokine effects in metastasis
Directionality of cytokine effects was assessed to evaluate immune balance in metastatic lung cancer.

r
Copy code
metastasis_direction <- metastasis_data %>%
  count(Direction) %>%
  mutate(proportion = n / sum(n))
Full analysis: scripts/analysis_directionality.R

Figure 3. Directionality of cytokine effects in lung cancer metastasis.



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
