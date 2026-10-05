# temporal-dengue-tabpfn
Leakage-controlled temporal evaluation of conventional machine learning and TabPFN for differentiating dengue from confirmed bacterial infection.
# Leakage-Controlled Temporal Evaluation of Tabular Machine Learning for Differential Dengue Diagnosis

## Overview

This repository contains the complete implementation of a temporally
validated machine-learning study for differentiating dengue from confirmed
community-acquired bacterial infection using routine clinical and laboratory
data.

Models were developed using the 2017 cohort and evaluated once on a locked
2018 temporal-test cohort. The workflow compares conventional machine-learning
models with TabPFN and includes cross-fitted stacking, probability calibration,
sensitivity-oriented threshold selection, conformal prediction and
prespecified feature-panel sensitivity analyses.

## Study design

- Source dataset: 1,984 laboratory rows from 606 patients
- Primary cohort: 332 patients
- Dengue: 152 patients
- Confirmed CABI: 180 patients
- Development cohort: 2017, n = 181
- Locked temporal-test cohort: 2018, n = 151
- Random seed: 42
- Cross-validation: stratified fivefold cross-validation

## Repository contents

### Run 1 — Routine panel without TabPFN

Reproducible conventional-machine-learning baseline using logistic regression,
Explainable Boosting Machine, XGBoost and CatBoost.

### Run 2 — Routine panel with TabPFN

Primary modern comparison incorporating TabPFN and the foundation-model stack.

### Run 3 — Expanded panel with TabPFN

Prespecified sensitivity analysis using six additional laboratory variables.

### Run 4 — Routine panel excluding CRP

Prespecified sensitivity analysis evaluating performance when CRP is
unavailable.

## Dataset

The dataset was published by Yasuda et al. and is available from Figshare:

https://doi.org/10.6084/m9.figshare.16810771.v1

The dataset is not redistributed in this repository. Users should download it
from the original source and comply with its licence and citation requirements.

## Running the notebooks

1. Open the required notebook in Google Colab.
2. Select Runtime > Change runtime type.
3. Use a CPU or GPU runtime according to availability.
4. Run the installation cell.
5. Upload or download the source dataset as instructed.
6. For TabPFN runs, accept the Prior Labs licence and add TABPFN_TOKEN through
   the Colab Secrets panel.
7. Run all cells sequentially from the beginning.
8. Generated tables and figures will be saved to the specified output folder.

## Recommended execution order

1. Run1_Routine_Without_TabPFN.ipynb
2. Run2_Routine_With_TabPFN.ipynb
3. Run3_Expanded_Panel_With_TabPFN.ipynb
4. Run4_Routine_Without_CRP.ipynb

Each notebook is intended to run independently in a fresh Colab session.

## Reproducibility safeguards

- Patient-level cohort construction
- Earliest valid observation retained per patient
- Chronological development-test separation
- Fold-fitted preprocessing
- Cross-fitted stacking
- Development-only calibration and threshold selection
- Locked temporal evaluation
- Fixed random seed

## Important note

The 2018 cohort is used only for final temporal evaluation. Preprocessing
parameters, models, calibration functions, thresholds and conformal rules are
estimated using the 2017 development cohort and subsequently applied to 2018
without refitting.

## Citation

If you use this code, please cite the associated article and the original
dataset publication.

## Licence

The source code is released under the MIT License. The dataset remains subject
to the licence specified by its original authors.
