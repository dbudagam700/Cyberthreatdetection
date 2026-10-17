# CICIDS-2017 Cyber Threat Detection Using Deep Learning

## Overview

This project explores machine-learning and deep-learning techniques for detecting malicious network traffic using the CICIDS-2017 intrusion detection dataset.

The Jupyter Notebook implements a data-processing and classification workflow that includes data cleaning, feature selection using Mexican Axolotl Optimization (MAO), model training, and performance evaluation. The objective is to distinguish benign network traffic from different categories of cyberattacks.

**Notebook:** [CICIDS-2017.ipynb](https://github.com/dbudagam700/Cyberthreatdetection/blob/main/CICIDS-2017.ipynb)

**Repository:** [Cyberthreatdetection](https://github.com/dbudagam700/Cyberthreatdetection)

## Project Objectives

- Analyze network traffic using the CICIDS-2017 benchmark dataset.
- Clean and preprocess network-flow records.
- Handle missing values and duplicate records.
- Select relevant features using an optimization-based approach.
- Train a deep-learning model for network intrusion detection.
- Evaluate classification performance using multiple metrics.
- Investigate model performance across different random seeds.
- Support cybersecurity research into intelligent intrusion detection systems.

## Dataset

The project uses the CICIDS-2017 dataset developed by the Canadian Institute for Cybersecurity.

The dataset contains benign network traffic and multiple attack categories represented through network-flow attributes.

Examples of the traffic characteristics include:

- Destination port and flow duration
- Forward and backward packet counts
- Packet lengths and packet-length statistics
- Flow and inter-arrival-time statistics
- TCP flag counts
- Active and idle connection statistics
- Traffic classification labels

The notebook loads a combined CSV dataset containing **2,830,743 rows and 79 columns** in its recorded initial output.

**Official dataset:** https://www.unb.ca/cic/datasets/ids-2017.html

### Dataset Configuration

The notebook expects the combined CSV file to be available at this Google Drive location:

```python
DATA = pd.read_csv(
    "/content/drive/MyDrive/Network_Intrusion_Combined.csv"
)
```

You must obtain the dataset separately and update the file path if your storage location differs.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data loading, cleaning, and manipulation |
| NumPy | Numerical computation |
| scikit-learn | Data splitting, feature evaluation, and metrics |
| PyTorch | Tensor processing and deep-learning components |
| Matplotlib | Visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Interactive development and experimentation |
| Google Colab | Cloud-based notebook execution |
| Google Drive | Dataset storage and access |

## Project Workflow

### 1. Data Loading and Inspection

The notebook loads the combined network traffic dataset and examines its dimensions, column structure, and data quality.

### 2. Data Preprocessing

The preprocessing workflow includes:

- Identifying missing values.
- Imputing missing numeric values using median values.
- Identifying duplicate records and removing duplicates.
- Preparing input features and target labels for modelling.

The recorded notebook output identifies missing values in `Flow Bytes/s` and duplicate records before cleaning.

### 3. Feature Selection Using MAO

The notebook implements a feature-selection procedure based on Mexican Axolotl Optimization (MAO).

A Random Forest classifier is used to evaluate candidate feature subsets against validation accuracy. This process aims to identify informative features while reducing unnecessary input dimensions.

### 4. Deep-Learning Model Training

The selected features are used in the notebook's PyTorch-based modelling workflow.

Training and evaluation outputs are used to examine classification performance, learning behavior, and consistency across experiments.

### 5. Model Evaluation

The notebook imports and uses a range of classification metrics, including:

- Accuracy
- Precision
- Recall
- Macro and weighted F1-score
- Specificity
- Matthews correlation coefficient (MCC)
- Cohen's kappa
- ROC-AUC and average precision, where applicable
- Confusion matrices
- Classification reports

These metrics provide complementary perspectives on detection quality, including performance across different attack categories.

## Installation

### Option 1: Google Colab

Google Colab is a convenient way to run the notebook without installing Python and the major machine-learning libraries locally.

1. Open the [CICIDS-2017 notebook](https://github.com/dbudagam700/Cyberthreatdetection/blob/main/CICIDS-2017.ipynb).
2. Open or upload it in [Google Colab](https://colab.research.google.com/).
3. Place the combined CSV dataset in your Google Drive.
4. Confirm that the CSV path in the notebook is correct.
5. Execute the notebook cells sequentially.

The notebook uses Google Drive mounting:

```python
from google.colab import drive
drive.mount("/content/drive")
```

This command is specific to Google Colab.

### Option 2: Local Installation

Install Python and create a virtual environment if desired. Then install the primary dependencies:

```bash
python -m pip install --upgrade pip

python -m pip install \
    pandas \
    numpy \
    matplotlib \
    seaborn \
    scikit-learn \
    torch \
    jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `CICIDS-2017.ipynb`, update the dataset path to your local CSV file, and execute the cells in order.

**Note:** The notebook processes a large dataset. Ensure that your machine has sufficient RAM and disk space. If execution is slow or runs out of memory, consider a representative subset for initial testing.

## Results and Evaluation

The notebook includes evaluation outputs and comparisons across random seeds.

The recorded summary outputs report strong weighted classification metrics, but macro-level metrics are lower. This difference highlights why overall accuracy alone is insufficient for assessing intrusion detection performance.

For a complete evaluation, examine:

- Per-class precision and recall
- Macro-F1 score for minority attack categories
- Confusion matrices
- False-positive and false-negative rates
- Validation versus test performance
- Performance variation across random seeds

The reported results should be independently reproduced before being used to make claims about model effectiveness. Results depend on preprocessing, train/test splitting, feature selection, and class distribution.

## Reproducibility and Limitations

- The dataset is not included in this repository and must be obtained separately.
- The notebook's input path is initially configured for Google Drive.
- Large-scale processing may require substantial memory and computation.
- CICIDS-2017 can contain imbalanced classes, making per-class evaluation important.
- Feature selection and preprocessing must be performed without leaking information from the held-out test set.
- Repeated or near-duplicate flows can influence reported performance.
- Benchmark performance does not guarantee equivalent detection accuracy on live enterprise traffic.

For stronger validation, preserve a final untouched test set and document the dataset version, preprocessing steps, class distribution, and random seeds.

## Repository Structure

```text
Cyberthreatdetection/
├── CICIDS-2017.ipynb
├── CICIDS_2019.ipynb
└── README.md
```

The README describes the CICIDS-2017 notebook. The repository also contains a separate CICIDS-2019 notebook.



## References

1. Sharafaldin, I., Lashkari, A. H., and Ghorbani, A. A. “Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization.” *International Conference on Information Systems Security and Privacy (ICISSP)*, 2018.
2. Canadian Institute for Cybersecurity: [CICIDS-2017 Dataset](https://www.unb.ca/cic/datasets/ids-2017.html).
3. Project source code: [Cyberthreatdetection on GitHub](https://github.com/dbudagam700/Cyberthreatdetection).

# CICIDS-2019 Cyber Threat Detection Using Deep Learning

## Overview

This project explores deep-learning-based network intrusion detection using the CIC-DDoS2019 dataset and an optimization-driven feature-selection approach.

The Jupyter Notebook implements a workflow for loading network traffic data, preprocessing network-flow features, selecting informative features using Mexican Axolotl Optimization (MAO), training a deep-learning model, and evaluating multiclass classification performance across repeated random-seed experiments.

The project aims to improve cyberattack classification by reducing feature dimensionality, handling class imbalance, and analyzing model stability and detection performance.

**Notebook:** [CICIDS_2019.ipynb](https://github.com/dbudagam700/Cyberthreatdetection/blob/main/CICIDS_2019.ipynb)

**Repository:** [Cyberthreatdetection](https://github.com/dbudagam700/Cyberthreatdetection)

## Project Objectives

- Analyze labelled network-flow traffic from the CIC-DDoS2019 dataset.
- Load and combine training data stored in Parquet format.
- Prepare network features and encode attack labels.
- Apply Mexican Axolotl Optimization for feature selection.
- Train a PyTorch-based deep-learning classifier.
- Evaluate multiclass classification performance.
- Examine training and validation accuracy and loss.
- Measure performance consistency across different random seeds.
- Analyze feature importance and classification errors.

## Dataset

The notebook uses data associated with CIC-DDoS2019, a benchmark developed by the Canadian Institute for Cybersecurity to support research into distributed denial-of-service detection.

**Official dataset information:** [Canadian Institute for Cybersecurity — DDoS Evaluation Dataset](https://www.unb.ca/cic/datasets/ddos-2019.html)

### Attack categories

The notebook's recorded data includes seven labelled classes:

- LDAP
- MSSQL
- NetBIOS
- Portmap
- Syn
- UDP
- UDPLag

These labels represent different attack categories in the notebook's data. The exact class distribution depends on the Parquet files available in the configured dataset directory.

The notebook's recorded feature-selection output reports **77 original features and seven classes**.

### Dataset format and storage

Unlike the CICIDS-2017 notebook, which loads a combined CSV file, this notebook searches recursively for Parquet files matching its training-file naming convention.

The default dataset location is:

```python
DATASET_PATH = "/content/drive/MyDrive/DATASET"
SEED = 42
```

The notebook searches for files such as:

```text
LDAP-training.parquet
MSSQL-training.parquet
NetBIOS-training.parquet
Portmap-training.parquet
Syn-training.parquet
UDP-training.parquet
UDPLag-training.parquet
```

It identifies training files whose class prefixes also appear among the available testing filenames, then loads and concatenates the matching training files.

**Important:** The notebook requires the expected Parquet files and naming conventions. Verify that the directory contains the intended training and testing partitions before running the complete experiment.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Loading, combining, and manipulating tabular data |
| NumPy | Numerical computation |
| PyArrow or another compatible Parquet engine | Reading Parquet files through Pandas |
| scikit-learn | Label encoding, class weighting, and classification metrics |
| PyTorch | Neural-network training and tensor processing |
| Matplotlib | Training curves and performance plots |
| Seaborn | Statistical visualization |
| Google Colab | Cloud-based notebook execution |
| Google Drive | Dataset storage |

## Methodology and Workflow

### 1. Environment Setup

The notebook imports libraries for data processing, optimization, neural-network training, visualization, and performance evaluation.

It also mounts Google Drive and configures a random seed for reproducibility.

### 2. Dataset Discovery and Loading

The notebook searches the configured directory recursively for training Parquet files.

It checks the available class-specific files and loads matching training partitions into Pandas DataFrames before concatenating them into a combined dataset.

This approach supports datasets organized into separate files for different attack categories.

### 3. Data Preprocessing

The network-flow data includes attributes such as:

- Protocol
- Flow duration
- Forward and backward packet counts
- Packet lengths and packet-length statistics
- Flow inter-arrival-time statistics
- Subflow and segment-related attributes
- Active and idle connection statistics
- Attack labels

The preprocessing and modelling stages prepare the network-flow attributes for feature selection and classification.

The exact treatment of missing values, infinite values, duplicate records, and class imbalance should be verified against the relevant notebook cells when reproducing the experiments.

### 4. Feature Selection Using Mexican Axolotl Optimization

The notebook applies Mexican Axolotl Optimization (MAO) to identify a reduced set of useful network-flow features.

The recorded optimization configuration includes:

- Population size: 20
- Number of iterations: 40
- Original feature count: 77
- Initial selected feature count: 42

The optimization process evaluates candidate feature subsets and tracks fitness and feature-count changes over iterations.

The objective is to reduce input dimensionality while retaining features that contribute to effective attack classification.

### 5. Deep-Learning Model Training

The selected features are used in a PyTorch-based multiclass classification workflow.

The notebook records training and validation performance across multiple random seeds. This makes it possible to examine both learning behavior and the stability of evaluation metrics.

Training accuracy and validation accuracy are plotted over epochs, alongside corresponding loss curves.

### 6. Model Evaluation

The notebook imports and uses a broad set of classification metrics, including:

- Accuracy
- Precision and recall
- Macro and weighted F1-score
- Macro and weighted specificity
- ROC-AUC
- Average precision
- Matthews correlation coefficient (MCC)
- Cohen's kappa
- Confusion matrices
- Per-class classification reports

Macro-averaged metrics help reveal performance on less-represented attack categories, while weighted metrics summarize performance according to class frequency.

### 7. Repeated-Seed Analysis

The notebook evaluates performance across multiple random seeds and calculates aggregate results for selected metrics.

Repeated-seed experiments help determine whether observed performance is consistent or heavily dependent on a particular random initialization or data split.

### 8. Feature-Importance Analysis

The notebook includes feature-importance analysis to help identify network-flow attributes associated with classification performance.

These outputs can support further investigation into which traffic characteristics are most informative for distinguishing attack categories.

## Installation

### Option 1: Google Colab

Google Colab is the recommended starting point because the notebook is configured to use Google Drive.

1. Open the [CICIDS-2019 notebook](https://github.com/dbudagam700/Cyberthreatdetection/blob/main/CICIDS_2019.ipynb).
2. Open or upload it in [Google Colab](https://colab.research.google.com/).
3. Place the required Parquet files under `MyDrive/DATASET`.
4. Verify the filenames and class-specific training/testing partitions.
5. Execute the notebook cells in sequence.

The notebook mounts Google Drive using:

```python
from google.colab import drive
drive.mount("/content/drive")
```

### Option 2: Local Installation

Install Python and the dependencies required by the notebook:

```bash
python -m pip install --upgrade pip

python -m pip install \
    pandas \
    numpy \
    pyarrow \
    matplotlib \
    seaborn \
    scikit-learn \
    torch \
    jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `CICIDS_2019.ipynb`, update `DATASET_PATH` to your local dataset directory, and run the cells in order.

If you encounter an error while reading Parquet files, confirm that a compatible Parquet engine such as PyArrow is installed.

## Results and Evaluation

The notebook contains recorded outputs for feature selection, repeated-seed evaluation, classification metrics, and feature-importance analysis.

For meaningful evaluation, examine:

- Overall classification accuracy
- Macro and weighted precision, recall, and F1-score
- Per-class recall for individual attack categories
- Confusion matrices and misclassified samples
- ROC-AUC and average precision, where applicable
- Training and validation loss
- Variation in performance across random seeds
- The relationship between selected features and classification quality

The saved outputs are useful for understanding the experiment, but they should not automatically be treated as independently reproduced results.

Before reporting final performance, rerun the notebook using the intended dataset and confirm the training/testing split, class-label mapping, and evaluation procedure.

## Reproducibility and Limitations

- The dataset is not included in the repository and must be obtained separately.
- The notebook uses Google Drive paths by default.
- The data-loading workflow expects class-specific Parquet filenames.
- Large datasets can require substantial RAM, processing time, and accelerator resources.
- Results depend on the dataset partitions, feature-selection procedure, model configuration, and random seeds.
- Feature selection and preprocessing must not use information from the final held-out test set.
- High weighted metrics can conceal weak detection of minority attack classes.
- Results from a benchmark dataset do not guarantee equivalent detection effectiveness in a live production network.

For a stronger experiment, document the dataset version, partitioning strategy, selected features, training configuration, class distribution, and results for every relevant class.

## Repository Structure

```text
Cyberthreatdetection/
├── CICIDS-2017.ipynb
├── CICIDS_2019.ipynb
└── README.md
```

This README describes the CICIDS-2019 notebook. The CICIDS-2017 notebook is a related project with a different data-loading and preprocessing workflow.

## Responsible Use

This project is intended for cybersecurity research, education, and authorized defensive security testing. It is a research notebook, not a production-ready real-time intrusion detection service.

## References

1. Canadian Institute for Cybersecurity: [CIC-DDoS2019 Dataset](https://www.unb.ca/cic/datasets/ddos-2019.html).
2. Project source code: [Cyberthreatdetection on GitHub](https://github.com/dbudagam700/Cyberthreatdetection).

