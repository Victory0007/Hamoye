# Amazon Satellite-Image Multi-Label Classification

This project explores multi-label classification of satellite images from the Planet: Understanding the Amazon from Space competition. Each image may have several tags describing land cover, weather and human activity. The original competition is hosted on [Kaggle](https://www.kaggle.com/competitions/planet-understanding-the-amazon-from-space).

## Current status

The notebook is a cleaned adaptation of an existing competition workflow found in this repository. The original author and source URL were not recorded, so its provenance must be established before this is presented as independently authored work. The notebook has not yet been rerun end to end in a clean environment, and no reproduced performance results are claimed.

## Approach in the notebook

- Explore the distribution of the 17 image tags and identify rare classes.
- Visualise a sample of the image dataset.
- Use an ImageNet-pretrained ResNet-18 with a multi-label output layer.
- Train with binary cross-entropy and evaluate using sample-averaged F-beta scores.
- Explore class-specific decision thresholds and confusion matrices.
- Apply test-time augmentation during inference.

## Dataset setup

Download the competition data and the additional test images. Arrange the extracted files as follows:

```text
data/planets-dataset/
├── planet/
│   └── planet/
│       ├── train-jpg/
│       ├── test-jpg/
│       ├── train_classes.csv
│       └── sample_submission.csv
└── test-jpg-additional/
    └── test-jpg-additional/
```

The dataset is not committed to this repository.

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/amazon_deforestation_classification.ipynb
```

On Windows, activate the environment with `.venv\\Scripts\\activate`.

## Review required before reporting results

- Verify the original notebook's author and source, then add an explicit attribution.
- Run the notebook from a clean environment with the dataset in the documented layout.
- Review the training/validation split and threshold-selection procedure. Thresholds are currently selected using validation predictions, so reporting the same validation score as an unbiased final estimate would be misleading.
- Check the saved model and result-artifact workflow, then record reproduced metrics and hardware/runtime details.
- Confirm that all model parameters and data loaders behave as intended during training.

The original notebook remains at the repository root as a reference. This project copy removes saved outputs and hosted-notebook shell setup, and uses a local dataset path. It is not yet a fully validated implementation.
