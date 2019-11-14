# EIPAssignments
Repository For Uploading EIP Assignments

# Assignment 1
Formed a group with Manjunath and 2 more and discussed the solution.

# Result
[0.03966653256598884, 0.99]

# Definitions:

# Convulution

Convolution is the process of identifying features in an image using a kernel or filter, by looking at one small part of an image at a time.

# Filters/ Kernels

Filters are the operators used for convolving on an image with an aim to identify distinct features in it like edges and gradients which will later be combined to identify patters / shapes.

# Epochs

An epoch is an instance of making my neural network look at my entire dataset. We need to have multiple epochs so that network learns patterns in the dataset better.

# 1X1 convolution

This will let us get global receptive field which is equal to the size of an image with just one layer, as this will not reduce the number of pixels after convolving on the image.

# 3X3 convolution

This will look at 9 pixels of an input image at a time and will produce one value in output resulting in in a receptive field of 9. So we have to use multiple layers with 3X3 convolution to achieve global receptive field equal to the size of an image in the last layer.

# Feature Maps

These are the outputs of different layers in a neural network, with each layer combining the smaller pieces identified by the previous layers into a larger and combined features.

# Activation function
I do not remember this being discussed in class, hence leaving it.

# Receptive field

This is the part of the image seen by a layer of neural network. In case of internal layers, we call this as local receptive field as this will be smaller than that actual image. In case of the final layer, this will be called global receptive field, which should be of at least the size of the original image for the neural network to be able to identify it.
