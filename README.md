# DeepND

DeepND is an interpretable deep learning framework for identifying sequence features associated with nucleosome positioning. The framework combines a modified residual neural network architecture with downstream kernel analysis to discover biologically meaningful sequence motifs from MNase-seq data.

The overall workflow consists of three steps:

1. Mapping MNase-seq fragments and generating nucleosome occupancy profiles.
2. Training a deep learning model to classify nucleosomal and non-nucleosomal DNA sequences.
3. Converting trained convolutional kernels into sequence motifs by identifying nucleotide preferences at each kernel position.

A key feature of DeepND is its emphasis on interpretability. In addition to achieving accurate classification, the framework enables the extraction and analysis of sequence motifs learned by the network, providing insights into the sequence determinants of nucleosome positioning.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/USERNAME/DeepND.git
cd DeepND
```

Create and activate a virtual environment:

```bash
python -m venv deepnd_env
source deepnd_env/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## Requirements

DeepND has been implemented using the following software versions:

- Python 3.8 or later
- TensorFlow 2.x
- Keras
- NumPy
- SciPy
- Pandas
- Matplotlib
- Scikit-learn

A typical installation can be completed using:

```bash
pip install tensorflow keras numpy scipy pandas matplotlib scikit-learn
```

---

## Data Preparation

The framework requires two groups of sequences:

- Positive samples (nucleosomal DNA)
- Negative samples (non-nucleosomal DNA)

In our study, sequences were extracted from the GEO dataset GSE36979. Positive and negative samples were represented using one-hot encoding, where each nucleotide is converted into a four-dimensional binary vector:

| Nucleotide | Encoding |
|------------|----------|
| A | 1 0 0 0 |
| C | 0 1 0 0 |
| G | 0 0 1 0 |
| T | 0 0 0 1 |

For nucleosomal sequences, the central nucleotide corresponds to the nucleosome dyad position.

---

## Training

The main training script is:

```bash
python ResNet.py <DatasetName> <ExtensionSize>
```

Example:

```bash
python ResNet.py Human 0
```

The model is based on a modified residual network architecture consisting of one-dimensional convolutional layers and residual connections.

To improve training stability and reduce overfitting, DeepND continuously monitors validation performance during training. The best-performing model is stored, and if validation performance stagnates, the framework restores the best snapshot and continues training using an alternative optimizer.

---

## Motif Extraction

Following model training, the first-layer convolutional kernels can be analyzed to identify sequence motifs associated with nucleosome positioning.

The motif extraction procedure involves:

1. Extracting trained convolutional kernels.
2. Converting kernel weights into nucleotide preference matrices.
3. Selecting the nucleotide with the highest weight at each position.
4. Generating sequence motifs for downstream biological interpretation.

The resulting motifs can be visualized as sequence logos or position weight matrices.

---

## Citation

The citation will be available after the paper is published.

---

## License

This project is distributed under the MIT License. See the `LICENSE` file for details.

---

## Contact

Yosef Masoudi-Sobhanzadeh (yms3786@yahoo.com)

For questions, bug reports, or collaboration opportunities, please open an issue in this repository.
