# Profile Transformer Model

## Overview
The Profile Transformer is a deep learning architecture designed to model vertical oceanographic profiles.

Each temperature–depth profile is treated as a sequence, allowing the model to learn dependencies across depth levels.

## Model Architecture

The model is based on the Transformer architecture with self-attention mechanisms.

Key components include:

- Input embedding layer
- Positional encoding along depth
- Multi-head self-attention layers
- Feed-forward neural network layers
- Output regression layer

## Input Representation

Each profile is represented as a sequence:

[Temperature, Depth, Latitude, Longitude, Time, Seasonal features]

The model processes the entire depth profile simultaneously.

## Handling Variable-Length Profiles

Ocean profiles have varying numbers of depth points.

To address this:

- Padding is applied
- Masked loss functions are used during training

## Advantages

- Captures long-range dependencies across depth
- Learns vertical structure of the ocean
- Suitable for profile reconstruction tasks

## Limitations

- Requires more computational resources
- Training time is higher than tree-based models
