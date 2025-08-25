Random Forest Classifier for Microbiome Abundance Data
Project Overview

This repository demonstrates how to train and evaluate a Random Forest classifier on microbiome relative abundance data.
The workflow covers:

Data preprocessing and feature alignment

Training with repeated k-fold cross-validation

Evaluation using ROC curves, AUC, and class probabilities

Visualization of prediction probabilities, including heatmaps grouped by diet

The aim is to explore how microbial composition can classify samples (e.g., Healthy vs. Disease) and provide a reproducible template for applying machine learning to microbiome data.

📂 Repository Structure
├── data/                
│   ├── Lifelike_relative_abundance_150samples.csv
│   └── Lifelike_relative_abundance__preview_2.csv
├── models/             
│   ├── rf_model.rds
│   └── rf_features.rds
├── scripts/             
│   ├── RandomForrestAbundance.Rmd   
├── results/           
│   ├── ROC_curve.png
│   ├── mtry_tuning.png
│   ├── prediction_heatmap.png
│   └── predictions_on_lifelike_preview.csv
├── README.md       


⚙️ Methods

Data Preparation

1. Microbiome abundance table (samples × taxa)

- Optional metadata (e.g., Diet) kept for grouping/plotting

- Data coerced to numeric, normalized, and aligned to training feature set

2. Model Training

- Random Forest classifier (caret::train with method="rf")

- 5-fold cross-validation, repeated twice

- Evaluation metrics: ROC (AUC), sensitivity, specificity

3. Model Tuning

- Tested different mtry values (number of variables tried at each split)

- ROC (AUC) stable across mtry, peak at ~11

4. Evaluation

- ROC curves confirm excellent model performance (AUC > 0.95)

- Confusion matrices and probability distributions

- Heatmaps of class probabilities grouped by Diet


📊 Key Results

Cross-validation ROC: ~0.95–0.96 (excellent discrimination power)

Best mtry: ~11 (but performance stable across range)

Visualizations:

- ROC curve (high sensitivity & specificity)

- Heatmap of predicted probabilities for Healthy vs Disease

- Faceting by Diet reveals grouping patterns


🚀 Usage

Clone the repository:

git clone https://github.com/yourusername/RandomForrestAbundance.git
cd RandomForrestAbundance


Run the analysis in R:

# Install dependencies
install.packages(c("caret", "randomForest", "pROC", "ggplot2", "tidyverse"))

# Open RMarkdown workflow
rmarkdown::render("scripts/RandomForrestAbundance.Rmd")


Outputs (plots, ROC curves, predictions) will be saved in the results/ folder.

🔧 Dependencies

R ≥ 4.2

Packages: caret, randomForest, ggplot2, tidyverse, pROC



✨ Author

Frederik Beck
PhD in Microbiology & Bioinformatics
Specializing in gut microbiome modeling and in-vitro gut systems.
