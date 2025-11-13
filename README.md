# IRIS Data Poisoning Experiment with MLflow

This repository demonstrates the impact of **data poisoning** (random Gaussian noise) on the **IRIS dataset** using a **Decision Tree Classifier**. The experiment injects noise at **0%**, **5%**, **10%**, and **50%** levels to simulate malicious or corrupted data. All experiments are tracked and logged with **MLflow**.

The Python script `train_poison_experiment.py` trains the model on the poisoned datasets, evaluates accuracy, saves classification reports, and generates a plot showing the effect of poisoning on model performance. All artifacts are stored in the `outputs/` directory.

The experiment is fully automated with GitHub Actions via `.github/workflows/run_experiment.yml`. The workflow installs dependencies, runs the script, uploads experiment outputs as artifacts, and optionally commits them back to the repository.

## Outputs

The `outputs/` directory contains:

- `report_0.txt`, `report_5.txt`, `report_10.txt`, `report_50.txt`: Classification reports for each poisoning level.  
- `poison_accuracy_plot.png`: Accuracy vs. Poisoning Level graph.  

In GitHub Actions, these files are uploaded as workflow artifacts for easy download.

## Experiment Summary

- A **Decision Tree Classifier** is trained using the IRIS dataset.  
- Gaussian noise is injected into the features to simulate **data poisoning** at multiple levels.  
- **0% poisoning**: baseline accuracy.  
- **5% poisoning**: minor drop in accuracy.  
- **10% poisoning**: noticeable misclassifications across classes.  
- **50% poisoning**: model loses generalization, predictions become nearly random.  

All metrics, parameters, and trained models are logged using **MLflow**, allowing for reproducibility and experiment tracking.

## Mitigation Strategies

- **Data Validation Pipelines**: Detect outliers and anomalies before training.  
- **Robust Models**: Use ensemble methods or robust loss functions to reduce sensitivity to noisy data.  
- **Data Provenance**: Track dataset versions and sources.  
- **Adversarial Training**: Retrain models on mixtures of clean and perturbed data to improve resilience.  

## Data Quality vs Quantity

When **data quality decreases** due to poisoning, more samples are required to achieve similar model performance. However, quality is more important than quantity — severe poisoning cannot be compensated for by simply adding more data.

## Author

**Dushyant Singh Bhadauriya**
