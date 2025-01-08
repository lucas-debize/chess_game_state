# Neural Network Generator Documentation

## Overview
The generator is a tool designed to create and initialize neural networks based on configuration files. It allows for the generation of multiple networks with the same architecture but different initial weights.

## Usage
```bash
./my_torch_generator config_file_1 nb_1 [config_file_2 nb_2...]
```

### Parameters
- `config_file_i`: Configuration file containing the neural network description
- `nb_i`: Number of neural networks to generate based on the configuration file

## Configuration File Format

The configuration file should be a JSON file containing the following parameters:

### Required Parameters
```json
{
    "name": "network_name",
    "layers": [64, 512, 256, 128, 64, 6],
    "activation_hidden": "relu",
    "activation_output": "softmax",
    "optimizer": "adam",
    "learning_rate": 0.0005,
    "batch_size": 64,
    "dropout_rate": 0.3,
    "momentum": 0.9,
    "beta1": 0.9,
    "beta2": 0.999,
    "epsilon": 1e-8,
    "l2_lambda": 0.01
}
```

### Parameter Details

#### Network Structure
- `name`: String identifier for the network
- `layers`: Array of integers defining the network architecture
  - First number: Input layer size (64 for chess board)
  - Middle numbers: Hidden layer sizes
  - Last number: Output layer size (6 for chess position classification)

#### Activation Functions
- `activation_hidden`: Activation function for hidden layers
  - "relu": Recommended for deep networks
  - "sigmoid": Alternative option
- `activation_output`: Activation function for output layer
  - "softmax": For multi-class classification
  - "sigmoid": For binary classification

#### Optimization Parameters
- `optimizer`: Choice of optimization algorithm
  - "adam": Adam optimizer (recommended)
  - "sgd": Stochastic Gradient Descent
- `learning_rate`: Learning rate for optimization (typical range: 0.0001 to 0.01)
- `batch_size`: Number of samples per training batch
- `momentum`: Momentum coefficient for optimization
- `beta1`: First moment estimate decay rate (Adam)
- `beta2`: Second moment estimate decay rate (Adam)
- `epsilon`: Small constant for numerical stability

#### Regularization Parameters
- `dropout_rate`: Dropout probability (typical range: 0.2 to 0.5)
- `l2_lambda`: L2 regularization coefficient

## Weight Initialization

The generator uses smart weight initialization strategies:

1. For ReLU activation:
   - He initialization: `scale = sqrt(2/n_inputs)`
   - Better for deep networks with ReLU

2. For other activations:
   - Xavier/Glorot initialization: `scale = sqrt(1/n_inputs)`
   - Suitable for sigmoid/tanh activations

## Output Format

Generated networks are saved as JSON files with the following naming convention:
```
basic_network_x.nn
```

Each file contains:
- All configuration parameters
- Initialized weights for each layer
- Network architecture information

## Example Configuration
```json
{
    "name": "basic_network",
    "layers": [64, 512, 256, 128, 64, 6],
    "activation_hidden": "relu",
    "activation_output": "softmax",
    "optimizer": "adam",
    "learning_rate": 0.0005,
    "batch_size": 64,
    "dropout_rate": 0.3,
    "momentum": 0.9,
    "beta1": 0.9,
    "beta2": 0.999,
    "epsilon": 1e-8,
    "l2_lambda": 0.01
}
```

## Example Usage
```bash
# Generate 5 networks using basic_network.conf
./my_torch_generator basic_network.conf 5

# Generate multiple sets of networks
./my_torch_generator basic_network.conf 3 advanced_network.conf 2
```

## Error Handling
The generator includes robust error checking for:
- Invalid configuration files
- Missing required parameters
- Invalid parameter values
- File system errors
- Invalid command-line arguments