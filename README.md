<font size="6">**Oyster Image Classification using Transfer Learning**</font>

## **Project Overview**
This notebook documents the complete workflow for a binary image classification. The objective is to classify oyster-related images into two categories: **Oyster Images** and **Oyster Spat Images**, using a pretrained deep learning model and to report standard evaluation metrics.
<br>

## **Objectives**
- Train a binary image classification model using a **pretrained CNN architecture**.
- Evaluate the model using **Accuracy**, **Macro-averaged Precision**, **Recall**, and **F1-score**.
- Visualize performance using a **Confusion Matrix** and **ROC Curve**.
- Apply appropriate techniques to **prevent overfitting** and justify model generalization.
<br>

## **Dataset Description**
The dataset was obtained from Kaggle and contains **1,357 images** organized into two folders:
- `Oyster Images`
- `Oyster Spat Images`

No predefined train/validation/test split was provided. Therefore, the dataset was randomly divided into:
- **70% Training set**
- **15% Validation set**
- **15% Test set**

A fixed random seed was used to ensure **reproducibility**.
***
<br>

## **Methodology**
### Model Architecture
A **ResNet-18** model pretrained on ImageNet was selected due to its balance between performance and computational efficiency. The pretrained layers were frozen, and the final fully connected layer was replaced to adapt the network for binary classification.

### Data Preprocessing
- Images were resized to **224×224** pixels.
- **Data augmentation** (random horizontal flip and rotation) was applied only to the training set.
- Validation and test sets were used without augmentation to ensure fair evaluation.

### Training Strategy
- Loss function: **Cross-Entropy Loss**
- Optimizer: **Adam**
- Training epochs: up to **20 epochs**
- **Early stopping** with a patience of **5 epochs** based on validation loss

These strategies help mitigate overfitting and improve generalization.
***
<br>

## **Evaluation Metrics**
The following metrics were computed on the **held-out test set**:
- **Accuracy**
- **Macro-averaged Precision**
- **Macro-averaged Recall**
- **Macro-averaged F1-score**
- **Confusion Matrix**
- **ROC Curve and AUC**

Macro-averaging was used to ensure equal contribution from both classes, regardless of class distribution.
***
<br>

## **Overfitting Analysis**
Training and validation losses were monitored across epochs, and training vs. test accuracy was compared. A small performance gap between training and test accuracy indicates that the model generalizes well to unseen data.
