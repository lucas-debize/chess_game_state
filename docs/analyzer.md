# Neural Network Analyzer Documentation

## Overview
The analyzer is a neural network implementation designed to analyze chess positions and classify them into different states (checkmate, check, stalemate, or nothing).

## Network Parameters

### Basic Configuration
- `layers`: List of integers defining the network architecture (number of neurons in each layer)
- `learning_rate`: Float value controlling the step size during optimization (default: 0.01)
- `batch_size`: Number of samples processed before updating the model (default: 32)

### Activation Functions
- `activation_hidden`: Activation function for hidden layers
  - "relu": Rectified Linear Unit (better for deep networks)
  - "sigmoid": Sigmoid function (0 to 1 range)
- `activation_output`: Activation function for output layer
  - "softmax": Used for multi-class classification
  - "sigmoid": Used for binary classification

### Optimization Parameters
- `optimizer`: Choice of optimization algorithm
  - "sgd": Stochastic Gradient Descent
  - "adam": Adam optimizer (adaptive moment estimation)
- `momentum`: Parameter for momentum in optimization (default: 0.9)
- `beta1`: First moment estimate exponential decay rate for Adam (default: 0.9)
- `beta2`: Second moment estimate exponential decay rate for Adam (default: 0.999)
- `epsilon`: Small constant for numerical stability (default: 1e-8)

### Regularization
- `dropout_rate`: Probability of dropping neurons during training (default: 0.2)
- `l2_lambda`: L2 regularization parameter to prevent overfitting (default: 0.01)

## Optimizations

### 1. Weight Initialization
- ReLU layers: He initialization (`sqrt(2/n)`)
- Other layers: Xavier initialization (`sqrt(1/n)`)
- Prevents vanishing/exploding gradients

### 2. Adam Optimizer
- Adaptive learning rates for each parameter
- Combines benefits of:
  - RMSprop (adaptive learning rates)
  - Momentum (acceleration in relevant directions)
- Better convergence in practice

### 3. L2 Regularization
- Prevents overfitting by penalizing large weights
- Adds regularization term to loss function
- Controlled by `l2_lambda` parameter

### 4. Early Stopping
- Monitors training progress
- Stops when no improvement for specified patience
- Prevents overfitting
- Saves best model during training

### 5. Data Augmentation
- Horizontal flipping of chess positions
- 180-degree rotation
- Increases training data variety
- Improves model generalization

### 6. Batch Processing
- Processes data in mini-batches
- Improves training efficiency
- Better generalization than single-sample updates

### 7. Progress Monitoring
- Real-time loss and accuracy tracking
- Progress bar visualization
- Checkpoint saving after each epoch

## Usage

### Training Mode
```bash
./my_torch_analyzer --train --save trained_network.nn basic_network_1.nn datasets/training_data.txt
```

### Prediction Mode
```bash
./my_torch_analyzer --predict trained_network.nn datasets/chess.txt
```

## Output Classes
1. "Checkmate White"
2. "Checkmate Black"
3. "Check White"
4. "Check Black"
5. "Stalemate"
6. "Nothing"

## Input Format
- Uses FEN (Forsyth–Edwards Notation) for chess positions
- Converts chess positions to 64-dimensional input vector