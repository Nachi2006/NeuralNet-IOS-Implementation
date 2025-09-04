# NeuralNet-IOS-Implementation
PyTorch to Core ML: Iris Classifier

This project demonstrates how to train a simple PyTorch model on the Iris dataset and convert it into a Core ML .mlpackage file.
The Core ML format is optimized for on-device inference on Apple platforms like iOS, macOS, and watchOS.

# Project Overview

The script main.py performs the following steps:

## Define a neural network

A small IrisNet model is implemented using PyTorch’s nn.Module.

The model classifies flowers from the Iris dataset.

## Train the model

The model is trained for a few epochs using a subset of the Iris dataset.

## Trace the model

Uses torch.jit.trace to create a TorchScript representation of the trained model.

This step is required since Core ML needs a static computation graph.

## Convert to Core ML

The TorchScript model is converted to the modern .mlpackage format using coremltools.

# How It Works

## TorchScript conversion:
PyTorch models are typically dynamic, but Core ML requires a static computation graph.
torch.jit.trace records the operations on a sample input and produces a TorchScript representation.

## Core ML conversion:
coremltools takes the TorchScript graph and compiles it into an optimized Core ML format (.mlpackage).

## On-device inference:
The resulting model runs efficiently on Apple devices, accelerated by CPU, GPU, or Neural Engine.

Save the Core ML model

The final model is stored as iris_net.mlpackage, ready to be integrated into an Apple application
