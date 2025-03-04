

The dataset is split into:
- **50,000** training images
- **10,000** test images

## Model Architecture
A **fully connected neural network (FNN)** with configurable:
- **Number of hidden layers**: 3, 4, or 5
- **Neurons per layer**: 32, 64, 128
- **Activation functions**: ReLU, Sigmoid
- **Weight initialization**: Xavier, Random
- **Regularization**: L2 (weight decay), dropout

## Training & Evaluation
The model trains using different:
- **Optimizers**:
  - SGD, Momentum, Nesterov, RMSprop, Adam, Nadam
- **Hyperparameters**:
  - Learning rate: `1e-3`, `1e-4`
  - Batch sizes: `16`, `32`, `64`
  - Weight decay: `0`, `0.0005`, `0.5`
  - Epochs: `5`, `10`
- **Train/Test Split**: 90% train, 10% validation

## Best Model Selection
- The script **runs multiple configurations** and selects the best-performing model based on validation accuracy.
- **Final accuracy is evaluated on the test set**.
- A **confusion matrix** is generated for performance visualization.

## Results & Observations
### **Hyperparameter Results Table**
| Epochs | Hidden Layers        | Optimizer | Learning Rate | Weight Decay | Accuracy |
|--------|----------------------|-----------|---------------|--------------|----------|
| 5      | [128, 64, 32]        | SGD       | 0.001         | 0            | 24.14%   |
| 5      | [128, 64, 32]        | SGD       | 0.001         | 0.0005       | 25.4%    |
| 5      | [128, 64, 32]        | SGD       | 0.0001        | 0            | 15.38%   |
| 5      | [128, 64, 32]        | SGD       | 0.0001        | 0.0005       | 14.36%   |
| 5      | [128, 64, 32]        | Adam      | 0.001         | 0            | 36.62%   |
| 5      | [128, 64, 32]        | Adam      | 0.001         | 0.0005       | 35.6%    |
| 5      | [256, 128, 64]       | Adam      | 0.001         | 0            | 39.04%   |
| 5      | [256, 128, 64]       | Adam      | 0.001         | 0.0005       | 36.76%   |
| 10     | [128, 64, 32]        | Adam      | 0.001         | 0            | 38.9%    |
| 10     | [128, 64, 32]        | Adam      | 0.001         | 0.0005       | 37.58%   |
| 10     | [256, 128, 64]       | Adam      | 0.001         | 0            | 39.04%   |

### **Findings**:
- **Adam optimizer consistently outperforms SGD** in convergence speed & accuracy.
- **More hidden layers generally improve accuracy** but **increase training time**.
- **Higher weight decay (L2 regularization) slightly lowers accuracy** but prevents overfitting.

