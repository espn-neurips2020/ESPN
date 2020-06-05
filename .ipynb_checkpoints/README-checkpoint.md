## ESPN: Extremely Sparse Pruned Networks

This is the code used to generate results for our NeurIPS submission.

### Setup

To setup the environment, use the requirements.txt file. 

Basic requirements:

1. Pytorch > 1.4.0
2. Torchvision > 0.5.2
3. Numpy > 1.18.0

### Experiments

Each of the experiments have been separated out into different files. We support training pruned ResNet32, ResNet50 and VGG-19 CIFAR-10/100, tiny-ImageNet and ImageNet. For MNIST results, we use a simple fully connected model based of LeNet300. 

