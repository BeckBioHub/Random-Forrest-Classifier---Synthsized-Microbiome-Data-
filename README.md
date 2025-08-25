# 🌲 Random Forest Classifier for Microbiome Abundance Data🌲

![Probability_heatmap_by_Diet](https://github.com/user-attachments/assets/899c79c4-1d85-40c2-b83f-f924bcce8543)



This repository demonstrates how to train, evaluate, and apply a **Random Forest classifier** on microbiome relative abundance data.  
It includes preprocessing, cross-validation, model tuning, and visualization of prediction probabilities — including **faceted heatmaps grouped by diet**.

---
```
## 📂 Repository Structure

├── data/
│ ├── Lifelike_relative_abundance_150samples.csv
│ └── Lifelike_relative_abundance__preview_2.csv
├── models/
│ ├── rf_model.rds
│ └── rf_features.rds
├── scripts/
│ └── RandomForrestAbundance.Rmd
├── results/
│ ├── ROC_curve.png
│ ├── mtry_tuning.png
│ ├── prediction_heatmap.png
│ ├── Probability_heatmap_by_Diet.jpg
│ └── predictions_on_lifelike_preview.csv
└── README.md

```
---

## ⚙️ Methods

### Data Preparation
- Input: microbiome **abundance table** (samples × taxa)  
- Optional: sample metadata (e.g., *Diet*) for grouping/plotting  
- Workflow:
  - Coerce abundances to numeric
  - Normalize to relative abundances
  - Align new datasets to training features for reproducibility

### Model Training
- **Random Forest** classifier (`caret::train`, `method = "rf"`)
- **5-fold cross-validation**, repeated twice
- Performance metrics: ROC curves, AUC, sensitivity, specificity

### Model Tuning
- Tested different **mtry** values (variables per split)  
- ROC/AUC stable across tested values, best around *mtry ≈ 11*

### Evaluation
- ROC curves confirm excellent discrimination (AUC > 0.95)
- Confusion matrices and predicted class probabilities
- **Heatmaps** of sample probabilities, faceted by *Diet*

---

## 📊 Key Results

- Cross-validation ROC: **~0.95–0.96** (excellent discrimination)
- Best *mtry*: ~11 (stable across range)
- Visualizations:
  - ROC curve (high sensitivity & specificity)
  - Heatmap of predicted probabilities (Healthy vs. Disease)
  - Faceting by *Diet* highlights grouping patterns

---

## 🚀 Usage

Clone the repository:

git clone https://github.com/BeckBioHub/RandomForrestAbundance.git
cd RandomForrestAbundance

Run the analysis in R:
# Install dependencies
install.packages(c("caret", "randomForest", "pROC", "ggplot2", "tidyverse", "rmarkdown"))

# Render the RMarkdown workflow
rmarkdown::render("scripts/RandomForrestAbundance.Rmd")


🔧 Dependencies

R ≥ 4.2

Packages:
- caret
- randomForest
- ggplot2
- tidyverse
- pROC
- rmarkdown

✨ Author

Frederik Beck, PhD
Microbiologist & Bioinformatician
Specializing in gut microbiome modeling and in-vitro gut systems
