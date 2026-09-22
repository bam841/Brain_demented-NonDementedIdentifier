# Brain Demented vs. Non-Demented Identifier

An end-to-end Deep Learning pipeline and clinical diagnostic triage tool for identifying Alzheimer's Disease and Dementia pathology from brain Magnetic Resonance Imaging (MRI) scans.

## Repository Contents
* `alzheimers_two_models.ipynb`: Master Jupyter Notebook containing data preparation, visual EDA, baseline CNN, pretrained MobileNetV2 transfer learning, 3-fold cross-validation, hyperparameter tuning, and clinical evaluation.
* `Alzheimer_Binary/`: Binary-classified brain MRI dataset partitioned into isolated splits:
  * `train/`: Expanded training dataset (8,870 images: 4,480 Non-Demented, 4,390 Demented).
  * `val/`: Untouched validation dataset (950 images: 480 Non-Demented, 470 Demented).
  * `test/`: Untouched test dataset (951 images: 480 Non-Demented, 471 Demented).

## Clinical Diagnostic Formulation
* **Class 0 (`Non_Demented`)**: Healthy control scans with normal ventricles and cortical structures.
* **Class 1 (`Demented`)**: Neurodegenerative impairment combining Very Mild and Mild dementia stages into a clinically actionable triage category.

## Benchmark Results (Untouched Test Set)
* **MobileNetV2 (Champion Transfer Model)**:
  * **Sensitivity (Recall on Dementia)**: 79.79%
  * **Specificity**: 67.94%
  * **Test Accuracy**: 73.92%
  * **ROC-AUC**: 0.8379
  * **Inference Latency**: ~8.9 ms/scan (CPU)
