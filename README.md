# Classical vs Quantum Machine Learning on Small Datasets

This project compares classical machine learning models with a small quantum machine learning model on a classification dataset.

The classical models used in the experiment are Logistic Regression, Support Vector Machine (SVM), and Random Forest. For the quantum machine learning experiment, Principal Component Analysis (PCA) is used to reduce the original features to two components, which are then used as inputs to a Variational Quantum Classifier (VQC).

The experiments also examine how model performance changes when different amounts of training data are used.

## Research Question

How do classical and quantum machine learning methods compare when training on small datasets?

## Objective

To compare classical machine learning models with a quantum machine learning approach on a small classification dataset and examine how the observed VQC performance changes with different training dataset sizes.

## Dataset

The project uses the Breast Cancer Wisconsin dataset available through `scikit-learn`.

- Number of samples: 569
- Number of features: 30
- Classes: malignant and benign

The dataset is divided into training and testing sets using an 80/20 split. Stratified splitting is used so that the class distribution is maintained between the training and testing sets.

## Methods

### Classical Machine Learning

Three classical machine learning models were evaluated:

- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest

The classical models were trained using the original 30 features.

### Quantum Machine Learning

For the quantum machine learning experiment:

1. The features were standardized.
2. PCA was used to reduce the data from 30 features to 2 components.
3. The two PCA components were encoded using a 2-qubit ZZ feature map.
4. A Real Amplitudes ansatz was used as the trainable circuit.
5. A Variational Quantum Classifier (VQC) was trained using COBYLA as the optimizer.

The VQC was evaluated using 20%, 40%, 60%, and 80% of the available training data while keeping the test set fixed.

Learning approach: This project uses supervised learning for a binary classification task, with labelled data indicating malignant or benign cases.

Classical models: Logistic Regression, Support Vector Machine (SVM), and Random Forest.

Quantum model: Variational Quantum Classifier (VQC), using a quantum feature map and variational circuit.


## Evaluation

The models were evaluated using two classification metrics:

- **Accuracy** — the proportion of test samples that were classified correctly.
- **F1 Score** — a metric that combines precision and recall into a single score.

For the training-size experiments, the same test set was used for all training sizes so that the observed differences could be compared under the same test conditions.

## Main Observations

The classical machine learning models achieved higher test performance than the VQC in this experiment. Logistic Regression and SVM achieved the highest test performance among the classical models, while Random Forest had slightly lower scores.

The VQC performance varied across the four training sizes tested and did not show a consistent improvement as the training size increased.

These results should be interpreted carefully because the classical models used all 30 original features, whereas the VQC used only 2 PCA components. The VQC experiments also reused the same classifier object across training sizes.

## Limitations

- The classical models used all 30 original features, while the VQC used only 2 PCA components.
- The training-size experiments used the same fixed test set.
- The training subsets were selected from the available training data rather than using repeated random or stratified sampling.
- The same VQC classifier object was reused across the different training sizes.
- The quantum model was evaluated using a simulator rather than a physical quantum computer.
- The experiment used one dataset and one train-test split, so the results should not be generalized to other datasets.

  ## Tools and Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Qiskit
- Qiskit Machine Learning
- Google Colab
