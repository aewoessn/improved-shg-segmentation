# improved-shg-segmentation

Repository associated with data used in the manuscript titled [_Improved segmentation of collagen second harmonic generation images with a deep learning convolutional neural network_](https://doi.org/10.1002/jbio.202200191).

**DISCLAIMER: We kindly ask that any usage of this data and network be properly referenced.**

# Getting started
This repository houses both the trained collagen-positive UNet, as well as the complete dataset used for network training.

# 1. Trained collagen-positive CNN
The `\trained model` folder contains the trained network in two forms: `unet.pt` and `unet.onnx`. The `.pt` file is specific to pytorch (used to train the model), and the `.onnx` file (see more information [here](https://onnx.ai)) can be used in other programming languages.

The network expects an intensity image that is normalized to have values between 0 and 1. Once an image is put through the network, the output is a raw probability map that needs to be normalized using the [sigmoid function](https://en.wikipedia.org/wiki/Sigmoid_function). The output should then be a value ranging between 0 and 1, where values tending toward 0 are collagen-negative, and values tending toward 1 are collagen-positive.

# 2. Network training datasets
The `\network training datasets` folder contains three zipped files (`training.7z`, `validation.7z`, and `testing.7z`), which contain the training, validation, and testing datasets, respectively. Within each zipped folder are two additional folders: `\images` and `\masks`. 

The `\images` folder contains numbered image patches (64 x 64 pixels), whose intensity is collagen second harmonic generation (SHG) signal intensity. These images are stored as 16-bit images, but the true intensity range of these images is 13-bit.

The `\masks` folder contains the ground truth masks for each corresponding image. These images are stored as 8-bit images, but the true intensity range of these images is a boolean value; 0 corresponds to collagen-negative, and 1 corresponds to collagen-positive.