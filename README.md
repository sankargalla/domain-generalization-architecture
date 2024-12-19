# Domain Generalization Architecture

A novel approach combining Margin Disparity Discrepancy (MDD) and Self-Supervised Semantic Alignment (S³A) to enhance domain adaptation in neural networks. This architecture addresses challenges such as domain shifts, unseen target classes, and label imbalance by aligning global feature distributions and improving category-level semantic alignment. The model has been validated on the Office-Home and VisDA datasets, achieving superior domain generalization performance compared to baseline methods. Python, PyTorch, and TensorFlow were used for implementation and analysis, contributing to advancements in explainable AI and domain-invariant learning.

---

## Setup Instructions

### Setting up Python Environment

Follow the instructions below to install all necessary packages used in this code base.

### Compatible PyTorch Version

This project has been tested with PyTorch version **2.0**, which empirically speeds up the training process. However, the code does not utilize any PyTorch 2.0-specific features and is compatible with older versions, such as **1.12.0**.

### Installation

```bash
pip install -r requirements.txt
```

---

## Download and Preparation of Datasets

### Configuration

Before running the data preparation script, update the configuration file located at `data_preparation/dataset.yaml` with the correct settings for your dataset. In particular, update the `dataset_dir` variable to point to the directory where your dataset is stored:

```yaml
dataset_dir: /path/to/dataset
```

### Download and Prepare Dataset

Run the following commands to download and prepare your dataset:

```bash
cd data_preparation

python data_preparation.py --dataset <DATASET>
```

#### Example

Replace `<DATASET>` with the name of the dataset you want to prepare (e.g., `OfficeHome`, `DomainNet`). For example:

```bash
python data_preparation.py --dataset OfficeHome
```

This script will:
- Download the dataset (if necessary).
- Extract the text data specifying how to split the training, validation, and test sets.
- Save the resulting data in the appropriate format for this repository.

After running the data preparation script, the resulting data files will be ready for use.

---

## Running the Model

To execute the model, use the following command:

```bash
python main.py --method mme --dataset OfficeHome --source 0 --target 1 --seed 1102 --num_iters 10000 --shot 3shot
```

### Explanation of Parameters
- `--method`: The method to use (e.g., `mme` for MDD and S³A).
- `--dataset`: The dataset to use (e.g., `OfficeHome`, `DomainNet`).
- `--source`: The source domain index.
- `--target`: The target domain index.
- `--seed`: The random seed for reproducibility.
- `--num_iters`: The number of iterations for training.
- `--shot`: The number of shots (e.g., `3shot`).

#### Example

To run the model on the 3-shot A -> C Office-Home dataset:

```bash
python main.py --method mme --dataset OfficeHome --source 0 --target 1 --seed 1102 --num_iters 10000 --shot 3shot
```

You can modify this command to run experiments with different hyperparameters or datasets.

---

## Datasets Used
- **Office-Home**
- **VisDA**
