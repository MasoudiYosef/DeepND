# DeepND
DeepND is an interpretable deep learning framework (Figure 1) that combines deep residual networks with statistical analyses of trained convolutional kernels to identify sequence features associated with nucleosome positioning.

In general, DeepND consists of three main steps:

Mapping 147-bp MNase-seq fragments and generating nucleosome occupancy profiles.
Training a deep learning model to classify nucleosomal and non-nucleosomal DNA sequences.
Converting convolutional kernels of different lengths into sequence motifs by selecting the nucleotide with the highest weight at each position.

This framework is implemented in Python and is freely available under the MIT License.

The training data were obtained from the GSE36979 dataset. Two groups of sequences were extracted: positive samples (nucleosomal DNA) and negative samples (non-nucleosomal DNA). Each sequence is 201 bp in length, with the central nucleotide corresponding to the nucleosome dyad position in the positive class. The sequences were converted into a one-hot encoded representation and used as input for the model implementation provided in ResNet.py.

The source code contains comments describing the purpose of each major procedure. The proposed residual network architecture differs from the original ResNet design in several aspects. In particular, model snapshots are periodically saved during training and can be restored when overfitting is detected, allowing training to resume using alternative optimization strategies. This approach improves model stability and facilitates the identification of robust sequence patterns associated with nucleosome positioning.
