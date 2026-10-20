# Histopathology Patch Classifier

Fine-tunes an ImageNet-pretrained ResNet18 to classify colorectal histology
patches into 9 tissue types using PathMNIST (64x64).

## Notebook
`pathology_classifier.ipynb` (outputs included)

## Setup
pip install torch torchvision medmnist scikit-learn

Runs in Google Colab (T4 GPU) in about 10 minutes plus dataset download.

## Method
- ResNet18 (pretrained), final layer replaced with a 9-class head
- Adam, lr 1e-3, 5 epochs, random horizontal/vertical flips
- Best epoch chosen on the validation set; test set used once at the end

## Results (single run, seed 0)

| Metric | Value |
|---|---|
| Best validation accuracy | 97.75% |
| Test accuracy | 93.05% |
| Majority-class baseline | 18.6% |
| Macro F1 (test) | 0.905 |

Weakest class: cancer-associated stroma (recall 0.58), mostly confused with
smooth muscle and debris.

## Limitations
Low-resolution patches, classification only, single short run.
