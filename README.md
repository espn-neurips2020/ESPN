## ESPN: Extremely Sparse Pruned Networks

This is the code used to generate results for our NeurIPS submission.

### Setup

To setup the environment, use the requirements.txt file. 

Basic requirements:

1. Pytorch == 1.5.0
2. Torchvision == 0.6.0
3. Numpy == 1.18.4
4. Pytorch-Ignite == 0.3.0 
5. tqdm == 4.46.0

### Experiments

We separate the experiments based on followings: "prune_espn_finetune.py" (ESPN-Finetune) and "prune_espn_rewind.py" (ESPN-Rewind) for LeNet300, LeNet5-Caffe, ResNet32, and VGG19 for MNIST, Fashion-MNIST, CIFAR-10/100, and Tiny-ImageNet. 

For ImageNet training, "prune_espn_imagenet_finetune.py" (ESPN-Finetune) and "prune_espn_imagenet_rewind.py" return a model and masking function. Then use "train_imagenet_finetune.py" or "train_imagenet_rewind.py" to train the network.




