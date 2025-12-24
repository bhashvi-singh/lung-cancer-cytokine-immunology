# Lung Cancer Cytokine Immunology

A literature-based exploratory analysis of cytokines involved in lung cancer progression, metastasis, and immune modulation.

---

## Overview

This repository presents an exploratory, literature-derived analysis examining how cytokines contribute to lung cancer progression and metastatic disease. Using recent peer-reviewed reviews and mechanistic studies, cytokine-related findings were manually curated into a structured dataset and analysed in R to identify recurring biological patterns and generate testable hypotheses relevant to cancer immunology.

This project is intended as a hypothesis-generating, conceptual analysis rather than a clinical or patient-level study.

---

## Research Questions

This analysis addresses three core questions:

1. **Progression**  
   Are specific cytokines consistently associated with lung cancer progression and disease advancement, suggesting potential relevance as early-stage biomarkers?

2. **Metastatic prioritisation**  
   Which cytokines are most frequently implicated in lung cancer metastasis, and which signalling pathways emerge as candidate targets for mechanistic and immunotherapeutic investigation?

3. **Immune directionality**  
   Do cytokines associated with lung cancer metastasis predominantly exhibit tumour-promoting or immunosuppressive effects rather than tumour-inhibitory roles?

---

## Data Source

- Curated from recent (approximately last 2 years) peer-reviewed review and mechanistic studies
- Focused on cytokines, chemokines, and immunoregulatory signalling in lung cancer
- Data manually extracted and structured using Google Sheets, then imported into R
- No patient-level, clinical trial, or omics datasets are included

---

## Methods

- Manual literature screening and annotation
- Classification of cytokines by:
  - Disease context (non-metastatic progression vs metastasis)
  - Direction of effect (tumour-promoting, inhibitory, context-dependent)
- Exploratory data analysis and visualisation using R (`dplyr`, `ggplot2`)
- Disease context classification:
  - `Metastasis_link = "Yes"` → explicitly metastasis-associated
  - `Metastasis_link = "No"` → non-metastatic / progression-related
  - `Metastasis_link = "Context"` → mixed or conditional evidence

---

## Cytokines Associated with Lung Cancer Progression

Progression-associated cytokines were identified from non-metastatic study contexts.

```r
progression_data <- cytokine_data %>%
  filter(Metastasis_link == "No")

progression_summary <- progression_data %>%
  count(Cytokine, sort = TRUE)
Full analysis: scripts/analysis_progression.R




Metastasis-Associated Cytokines and Target Prioritisation
Metastasis-linked studies were used to identify cytokines recurrently implicated in lung cancer dissemination.

r
Copy code
metastasis_data <- cytokine_data %>%
  filter(Metastasis_link == "Yes")

metastasis_summary <- metastasis_data %>%
  count(Cytokine, sort = TRUE)
Full analysis: scripts/analysis_metastasis_targets.R




Directionality of Cytokine Effects in Metastasis
Directionality of cytokine effects was assessed to evaluate immune balance in metastatic lung cancer.

r
Copy code
metastasis_direction <- metastasis_data %>%
  count(Direction) %>%
  mutate(proportion = n / sum(n))
Full analysis: scripts/analysis_directionality.R


Key Findings
Cytokine signalling is consistently implicated in lung cancer progression, although evidence for dominant early-stage biomarker candidates remains limited.

Metastasis-associated cytokines show stronger recurrence and pathway convergence, supporting their prioritisation for mechanistic and immunotherapeutic research.

Metastatic contexts are characterised by a skew towards tumour-promoting and immunosuppressive cytokine activity.

Limitations
Small, literature-derived dataset

Dependence on study-level interpretations

No clinical validation or patient-level inference

Cytokine redundancy and strong context dependence are not fully captured

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
Expansion to include additional primary studies and meta-analyses

Integration with bulk or single-cell transcriptomic datasets

Comparative analysis with immune checkpoint and T-cell signalling pathways

Extension of the framework to other cancer types

References
Mechanism of interleukin-6 cytokine family in bone metastasis of lung cancer and prospects for its application.

Therapeutic targeting of TGF-β in lung cancer.

The novel functions of chemokines in lung cancer progression.

The distinct roles of IL-37 and IL-38 in non-small cell lung carcinoma and their clinical implications.

Author
Bhashvi Singh
Background in immunology and molecular biology with research interests in cancer immunology and immune signalling.


