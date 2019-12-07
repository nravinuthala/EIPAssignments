Used ResNet18 as base code and did the following modifications.

1. Chose n = 2 so as to reduce the depth as the image size is small.
2. Increased number of kernels to 64 so as to capture maximum information at the beginning layers.

Achieved 88% accuracy in 46th epoch.
Used 10 images from internet to show gradcam results on them using the above network.
