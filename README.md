# SIPaKMeD Binary Classification (ResNet-18)

End-to-end mini pipeline for biomedical image classification:
data loading → augmentation → ResNet-18 fine-tuning → evaluation (ROC-AUC + confusion matrix).

## Dataset
- SIPaKMeD (cervical cell images)
- Prepared as a binary task with folder structure:
  - train/negative, train/positive
  - val/negative, val/positive
  - test/negative, test/positive

## Method
- Model: ResNet-18 (ImageNet pretrained)
- Head: 1 logit (Linear) + BCEWithLogitsLoss
- Augmentations (train): resize 224×224, random horizontal flip, random rotation (10°)
- Eval: ROC-AUC + confusion matrix, sensitivity, specificity, precision, F1

## Results (Test Set)
- Test ROC-AUC: 0.999225
- Threshold = 0.50:
  - Confusion matrix [[TN, FP], [FN, TP]] = [[358, 4], [3, 243]]
  - acc=0.9885, precision=0.9838, sensitivity=0.9878, specificity=0.9890, f1=0.9858
- Threshold (Youden’s J) = 0.56878:
  - Confusion matrix = [[360, 2], [3, 243]]
  - acc=0.9918, precision=0.9918, sensitivity=0.9878, specificity=0.9945, f1=0.9898

## How to run
Open and run the notebook:
- `sipakmed_resnet18_pipeline.ipynb`

> Note: Paths in the notebook refer to Google Drive locations used in Colab. Update `PREP_ROOT` to your local dataset path if running outside Colab.
