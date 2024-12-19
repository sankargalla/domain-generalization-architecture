Domain Generalization Architecture:
A novel approach combining Margin Disparity Discrepancy (MDD) and Self-Supervised Semantic Alignment
(S³A) to enhance domain adaptation in neural networks. Addressed challenges like domain shifts, unseen target classes,
and label imbalance by aligning global feature distributions and improving category-level semantic alignment. Validated
the model on Office-Home and VisDA datasets, achieving superior domain generalization performance compared to
baseline methods. Utilized Python, PyTorch, and TensorFlow for implementation and analysis, contributing to
advancements in explainable AI and domain-invariant learning.

Setting up Python Environment

Following the instructions provided here to install all necessary packages used in this code base.

Compatible PyTorch version
We test this project with PyTorch version 2.0. Emprically it has shown to speed up the training progress.

However, the code does not use any PyTorch 2.0 features and should be compatible with older versions of PyTorch, such as version 1.12.0.

Installation:

pip install -r requirements.txt

Download and Preparation of Datasets:

Before running the data preparation script, make sure to update the configuration file in data_preparation/dataset.yaml with the correct settings for your dataset. In particular, you will need to update the dataset_dir variable to point to the directory where your dataset is stored.

dataset_dir: /path/to/dataset
To download and prepare one of these datasets, run the following commands:

cd data_preparation

python data_preparation.py --dataset <DATASET>

Eg: Replace <DATASET> with OfficeHome to download OfficeHome dataset

Replace with the name of the dataset you want to prepare (e.g. DomainNet, OfficeHome). This script will download the dataset (if necessary) and extract the text data which specify the way to split training, validation, and test sets. The resulting data will be saved in the format described above.

After running the data preparation script, you should be able to use the resulting data files in this repository.

Running the model

To run the main Python file, use the following command:

python main.py --method mme --dataset OfficeHome --source 0 --target 1 --seed 1102 --num_iters 10000 --shot 3shot

This command runs the model on the 3-shot A -> C Office-Home dataset, with the specified hyperparameters. You can modify the command to run different experiments with different hyperparameters or on different datasets.

