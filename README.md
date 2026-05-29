## Overview
- This project implements a simplified D-GEX-inspired deep learning pipeline for transcriptomic prediction using TCGA breast cancer RNA-seq data.
- The workflow reconstructs target gene expression profiles from landmark genes derived from the L1000 assay. The pipeline includes transcriptomic preprocessing, Ensembl-to-gene mapping, landmark gene selection, neural network training, and evaluation of transcriptomic prediction performance.
- The goal of the project is to explore how deep learning models can capture transcriptomic structure and infer genome-wide expression patterns from a smaller subset of biologically informative genes.

## Workflow
- Downloaded TCGA BRCA RNA-seq expression matrix from UCSC Xena
- Loaded GENCODE v36 probemap file
- Mapped Ensembl gene IDs to gene symbols
- Formatted expression matrix into ML-ready input file
- Loaded L1000 landmark gene list
- Constructed:
    - Landmark gene matrix (X)
    - Target gene matrix (Y)
- Built deep neural network using TensorFlow/Keras
- Trained model to predict target gene expression
- Evaluated model using:
    - Mean Squared Error (MSE)
    - Pearson correlation
- Visualized:
    - Training/validation loss
    - Predicted vs actual expression
    - Gene-wise correlation distribution

## Dataset
- TCGA Breast Cancer (BRCA) RNA-seq expression data
- Downloaded from UCSC Xena
- Expression values: log2(count + 1) normalized STAR counts
- Gene annotation: GENCODE v36 probemap

## Model Architecture
Input Layer:
- Landmark gene expression matrix
Hidden Layers:
- Dense layer (128 neurons, ReLU activation)
- Dropout (0.2)
- Dense layer (64 neurons, ReLU activation)
- Dropout (0.2)
Output Layer:
- Predicted target gene expression values

## Results
- The neural network successfully learned transcriptomic relationships between landmark and target genes.
- Observed performance:
    - Pearson correlation ≈ 0.97
    - Moderate Mean Squared Error values during reconstruction
- Although the reconstruction error remained non-trivial due to the high dimensionality of transcriptomic prediction and the use of dropout regularization, the strong correlation suggests that the model effectively captured global gene expression patterns and transcriptomic structure.
- Visualization of training loss and prediction accuracy demonstrated effective learning of transcriptomic structure from landmark genes.

## Future Improvements
- Experiment with deeper neural network architectures
- Compare different hidden layer sizes and dropout rates
- Implement batch normalization and alternative activation functions
- Use early stopping to prevent overfitting
- Train models for more epochs and compare convergence behavior
- Evaluate gene-wise prediction accuracy in greater detail
- Identify biological pathways associated with highly predictable genes
- Analyze poorly predicted genes and their biological characteristics
- Compare prediction performance across different cancer subtypes
- Compare deep learning performance against:
    - Linear regression
    - Random forest regression
    - XGBoost-based models

## Key Learning Outcomes
- Transcriptomic data preprocessing
- Ensembl ID to gene symbol mapping
- Landmark-target gene matrix construction
- Deep learning for gene expression prediction
- TensorFlow/Keras model development
- Biological interpretation of transcriptomic prediction performance
- Gene-wise evaluation of predictive accuracy

## Limitations
- Simplified implementation inspired by D-GEX
- Limited hyperparameter optimization
- Global MSE values remained moderately high due to the complexity and dimensionality of transcriptomic reconstruction.
- Model trained on a subset of transcriptomic features
- Biological interpretability of neural network predictions remains limited
