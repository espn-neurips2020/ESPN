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

We include the codes for experiments conducted in the papers as following: 

`prune_espn_finetune.py`: ESPN-Finetune prunes (1) LeNet300, LeNet5-Caffe for MNIST/Fashion-MNIST, (2) VGG19, ResNet32 for CIFAR-10/100, (3) VGG19, ResNet32 for Tiny-ImageNet. 

`prune_espn_rewind.py`: ESPN-Rewind prunes (1) LeNet300, LeNet5-Caffe for MNIST/Fashion-MNIST, (2) VGG19, ResNet32 for CIFAR-10/100, (3) VGG19, ResNet32 for Tiny-ImageNet. 

`prune_espn_imagenet_finetune.py`: ESPN-Finetune pruning ResNet50 for ImageNet dataset. We use the pretrained model in Torchvision. Returns the mask and the model before finetuning.

`train_imagenet_finetune.py`: Finetuning the ResNet50 on ImageNet dataset from the `prune_espn_imagenet_finetune.py` outputs. The code based on official pytorch implementation on ImageNet training from [main.py](https://github.com/pytorch/examples/blob/master/imagenet/main.py).

`prune_espn_imagenet_rewind.py`: ESPN-Rewind pruning ResNet50 for ImageNet dataset. We use the untrained model in Torchvision. Returns the mask and the model with warmup training.

`train_imagenet_rewind.py`: Finetuning the ResNet50 on ImageNet dataset from the `prune_espn_imagenet_rewind.py` outputs. The code based on official pytorch implementation on ImageNet training from [main.py](https://github.com/pytorch/examples/blob/master/imagenet/main.py).








