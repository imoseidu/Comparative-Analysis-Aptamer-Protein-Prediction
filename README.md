# Evaluating AI-Based Tools for Aptamer–Protein Interaction Prediction

**Full project write-up:** [View PDF](project_writeup.pdf)

## Overview
This project evaluates the reliability, consistency, and limitations of modern AI-driven and physics-based computational tools for predicting aptamer–protein interactions. Rather than developing new machine learning models, the focus is on **comparative analysis**, **model confidence interpretation**, and **biological plausibility** under realistic constraints.

Aptamers are short DNA or RNA molecules capable of binding proteins with high specificity and affinity, making them attractive alternatives to antibodies in diagnostics and therapeutics. However, experimental identification of effective aptamer binders—especially dual-aptamer “sandwich” pairs—remains costly and time-consuming. Recent advances in AI-based structural biology tools promise to accelerate early-stage screening, but their reliability for flexible nucleic acid–protein systems is still not well understood.

This project asks: *How consistent and informative are current computational predictions, and when should they be interpreted cautiously?*
<img width="206" height="166" alt="image" src="https://github.com/user-attachments/assets/9215687d-d630-40e1-b0b9-2ecba17beb34" />

---

## Objectives
- Compare AI-based and physics-based tools on the same aptamer–protein systems
- Assess agreement, disagreement, and failure modes across methods
- Analyze model confidence metrics versus structural plausibility
- Evaluate whether predictions could support early-stage aptamer screening
- Highlight practical and methodological limitations of current tools

---

## Skills Demonstrated
- Comparative evaluation of AI-based and physics-based models
- Interpretation of model confidence metrics and uncertainty
- Structural bioinformatics analysis
- Integration of heterogeneous model outputs
- Critical assessment of AI applicability in real biological settings
- Technical communication of complex results
  
---

## Data
**Target Proteins**
- SARS-CoV-2 spike protein
- Thrombin (used as a benchmark due to well-characterized aptamer binding)

**Ligands**
- DNA aptamers reported in prior literature

**Interaction Types**
- Single aptamer–protein complexes
- Dual-aptamer “sandwich” complexes

**Modeling Environment**
- Physiological salt conditions (Na⁺ ions)

Thrombin–aptamer interactions were used as a reference to contextualize model behavior, while SARS-CoV-2 interactions served as the primary application case.

---

## Methods & Tools

### AlphaFold 3
- Deep learning model for predicting biomolecular complex structures
- Used to generate 3D structures of protein–aptamer and dual-aptamer complexes
- Analyzed confidence metrics:
  - pLDDT (per-residue confidence)
  - pTM (global structure confidence)
  - ipTM (interface confidence)
- Evaluated sensitivity to input ordering and multi-component modeling assumptions

<img width="259" height="139" alt="image" src="https://github.com/user-attachments/assets/b675bd6c-dab9-4c4b-b94b-3162499a9b7c" />
Figure 3. Results from AlphaFold 3



### AptaTrans
- Deep learning pipeline for predicting aptamer–protein interaction (API) scores
- Used to rank candidate aptamers by predicted interaction strength
- Benchmarked against known aptamer–protein interactions

### HADDOCK
- Physics-based docking server
- Provided binding scores, cluster statistics, RMSD, and energetic components
- Used as an independent comparison to AI-based predictions

<img width="229" height="116" alt="image" src="https://github.com/user-attachments/assets/8b1044ad-f71e-42ef-9f84-d5be338cc3a9" />
Figure 3. Results from Haddock

### PyMOL
- Structural visualization and geometric analysis
- Inspection of predicted binding interfaces
- Measurement of residue proximity and inter-aptamer distances

RoseTTAFold2NA was also explored but could not be fully deployed due to extensive hardware and installation requirements, highlighting practical limitations of some state-of-the-art tools.

---

## Analytical Approach
The analysis emphasizes **comparative evaluation rather than optimization** of any single model:

- Benchmarked predictions using the known RE31–thrombin aptamer–protein pair
- Compared predicted binding quality across AlphaFold 3, AptaTrans, and HADDOCK
- Assessed alignment (or lack thereof) between confidence metrics and docking scores
- Investigated sensitivity to modeling assumptions, including input ordering
- Used structural inspection to contextualize numerical scores

Predictions were interpreted relatively, not as absolute ground truth.

---

## Key Results & Insights
- Substantial variability across tools for the same aptamer–protein pairs
- Strong predictions from one method were not always supported by others
- AlphaFold 3 often produced high global confidence (pTM) despite low interface confidence (ipTM)
- Predictions were sensitive to input ordering and modeling assumptions
- AptaTrans underperformed on a known benchmark interaction, suggesting training or generalization limitations
- Structural inspection revealed frequent involvement of aromatic residues (e.g., tyrosine) at predicted interfaces
- Dual-aptamer sandwich predictions for SARS-CoV-2 showed larger inter-aptamer distances than the thrombin benchmark, plausibly explaining weaker predicted binding

---

## Interpretation & Limitations
While AI-based and docking tools can accelerate hypothesis generation, their predictions for flexible nucleic acid–protein systems are sensitive to:
- Model assumptions
- Training data limitations
- Molecular flexibility
- Confidence metric interpretation

High global confidence does not necessarily imply reliable interface prediction. These tools should therefore be used **comparatively and cautiously**, rather than as definitive predictors.

<img width="411" height="156" alt="image" src="https://github.com/user-attachments/assets/f53a3d94-012d-4e0e-92e0-112f3201058b" />
Figure 4. The closest distance between aptamers RE31 and HD22 (Thrombin).


---

## Key Takeaway
This project demonstrates how modern AI tools can be critically evaluated in a realistic scientific context by integrating confidence metrics, structural inspection, and biological reasoning. Rather than treating AI outputs as ground truth, the analysis emphasizes uncertainty awareness, methodological limitations, and interpretability—core skills in applied data science and bioinformatics.

---

## Potential Extensions
- Validation against additional experimentally characterized aptamer–protein systems
- Incorporation of molecular dynamics simulations to assess flexibility
- Automated pipelines for systematic benchmarking across targets
- Integration of experimental binding data when available

---

## Authors
**Authors:** Imose Iduozee, Matias Ylitolva, Joonatan Lindfors, Sofia Hänninen, Jaakko Pulkkinen, Linda Jalonen
