# Chess Position Analyzer Neural Network

## Overview
A neural network-based system for analyzing chess positions and classifying them into different states (checkmate, check, stalemate, or normal position).

## Project Structure
```
.
├── README.md
├── docs/
│   ├── analyzer.md
│   ├── generator.md
│   ├── benchmarks.md
│   └── design_choices.md
├── my_torch_analyzer
├── my_torch_generator
├── my_torch_network.nn
└── basic_network.conf
```

## Quick Start
```bash
# Generate a neural network
./my_torch_generator basic_network.conf 1

# Train the network
./my_torch_analyzer --train --save trained_network.nn basic_network_1.nn datasets/training_data.txt

# Make predictions
./my_torch_analyzer --predict trained_network.nn datasets/chess.txt
```

## Documentation
- [Analyzer Documentation](docs/analyzer.md)
- [Generator Documentation](docs/generator.md)
- [Benchmarks](docs/benchmarks.md)
- [Design Choices](docs/design_choices.md)