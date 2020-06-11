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

We provide the unpruned pretrained models from this [link](https://drive.google.com/drive/folders/18wHTHOgAxMZhMKGqKzXmPGHiTbZIN7GN?usp=sharing). Download a folder named `models` and save it in the same directory to this directory.

### Codes

We include the codes for experiments conducted in the papers as following: 

`prune_espn_finetune.py`: ESPN-Finetune prunes (1) LeNet300, LeNet5-Caffe for MNIST/Fashion-MNIST, (2) VGG19, ResNet32 for CIFAR-10/100, (3) VGG19, ResNet32 for Tiny-ImageNet. 

`prune_espn_rewind.py`: ESPN-Rewind prunes (1) LeNet300, LeNet5-Caffe for MNIST/Fashion-MNIST, (2) VGG19, ResNet32 for CIFAR-10/100, (3) VGG19, ResNet32 for Tiny-ImageNet. 

`prune_espn_imagenet_finetune.py`: ESPN-Finetune pruning ResNet50 for ImageNet dataset. We use the pretrained model in Torchvision. Returns the mask and the model before finetuning.

`train_imagenet_finetune.py`: Finetuning the ResNet50 on ImageNet dataset from the `prune_espn_imagenet_finetune.py` outputs. The code based on official pytorch implementation on ImageNet training from [main.py](https://github.com/pytorch/examples/blob/master/imagenet/main.py).

`prune_espn_imagenet_rewind.py`: ESPN-Rewind pruning ResNet50 for ImageNet dataset. We use the untrained model in Torchvision. Returns the mask and the model with warmup training.

`train_imagenet_rewind.py`: Finetuning the ResNet50 on ImageNet dataset from the `prune_espn_imagenet_rewind.py` outputs. The code based on official pytorch implementation on ImageNet training from [main.py](https://github.com/pytorch/examples/blob/master/imagenet/main.py).

### Experiments

We list the script to run for the experiments we collected in our paper. ESPN-Finetune requires the `models` file to run it.

### MNIST/Fashion-MNIST

#### MNIST/LeNet300

ESPN-Finetune p=95%: `python prune_espn_finetune.py "mnist" "lenet300" "./output/mnist/lenet300/" "./models/mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet300_95percent.txt" --alpha 8e-5 --lr 0.05 --keep_ratio 0.05`

ESPN-Finetune p=98%: `python prune_espn_finetune.py "mnist" "lenet300" "./output/mnist/lenet300/" "./models/mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet300_98percent.txt" --alpha 8e-5 --lr 0.05 --keep_ratio 0.02`

ESPN-Finetune p=99%: `python prune_espn_finetune.py "mnist" "lenet300" "./output/mnist/lenet300/" "./models/mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet300_99percent.txt" --alpha 0.00015 --lr 0.05 --keep_ratio 0.01`

ESPN-Finetune p=99.6%: `python prune_espn_finetune.py "mnist" "lenet300" "./output/mnist/lenet300/" "./models/mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet300_996percent.txt" --alpha 0.00025 --lr 0.05 --keep_ratio 0.004`

ESPN-Rewind p=95%: `python prune_espn_rewind.py "mnist" "lenet300" "./output/mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet300_95percent.txt" --lr 0.01 --alpha 8e-5 --keep_ratio 0.05`

ESPN-Rewind p=98%: `python prune_espn_rewind.py "mnist" "lenet300" "./output/mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet300_98percent.txt" --lr 0.01 --alpha 8e-5 --keep_ratio 0.02`

ESPN-Rewind p=99%: `python prune_espn_rewind.py "mnist" "lenet300" "./output/mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet300_99percent.txt" --lr 0.01 --alpha 0.00015 --keep_ratio 0.01`

ESPN-Rewind p=99.6%: `python prune_espn_rewind.py "mnist" "lenet300" "./output/mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet300_996percent.txt" --lr 0.01 --alpha 0.0006 --keep_ratio 0.004`

#### MNIST/LeNet-5_Caffe

ESPN-Finetune p=95%: `python prune_espn_finetune.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" "./models/mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet_5_caffe_95percent.txt" --alpha 6e-5 --lr 0.05 --keep_ratio 0.05`

ESPN-Finetune p=98%: `python prune_espn_finetune.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" "./models/mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet_5_caffe_98percent.txt" --alpha 6e-5 --lr 0.05 --keep_ratio 0.02`

ESPN-Finetune p=99%: `python prune_espn_finetune.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" "./models/mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet_5_caffe_99percent.txt" --alpha 0.0001 --lr 0.05 --keep_ratio 0.01`

ESPN-Finetune p=99.6%: `python prune_espn_finetune.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" "./models/mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_mnist_lenet_5_caffe_996percent.txt" --alpha 0.0003 --lr 0.05 --keep_ratio 0.004`

ESPN_Rewind p=95%: `python prune_espn_rewind.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet_5_caffe_95percent.txt" --lr 0.1 --alpha 8e-5 --keep_ratio 0.05`

ESPN_Rewind p=98%: `python prune_espn_rewind.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet_5_caffe_98percent.txt" --lr 0.1 --alpha 0.0001 --keep_ratio 0.02`

ESPN_Rewind p=99%: `python prune_espn_rewind.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet_5_caffe_99percent.txt" --lr 0.1 --alpha 0.00025 --keep_ratio 0.01`

ESPN_Rewind p=99.6%: `python prune_espn_rewind.py "mnist" "lenet_5_caffe" "./output/mnist/lenet_5_caffe/" --epochs_warmup 1 --logname "espn_rewind_mnist_lenet_5_caffe_996percent.txt" --lr 0.1 --alpha 0.0005 --keep_ratio 0.004`

#### Fashion-MNIST/LeNet300

ESPN_Finetune p=95%: `python prune_espn_finetune.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300" "./models/fashion_mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet300_95percent.txt" --alpha 8e-5 --lr 0.05 --keep_ratio 0.05`

ESPN_Finetune p=98%: `python prune_espn_finetune.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300" "./models/fashion_mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet300_98percent.txt" --alpha 8e-5 --lr 0.05 --keep_ratio 0.02`

ESPN_Finetune p=99%: `python prune_espn_finetune.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300" "./models/fashion_mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet300_99percent.txt" --alpha 0.00015 --lr 0.05 --keep_ratio 0.01`

ESPN_Finetune p=99.6%: `python prune_espn_finetune.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300" "./models/fashion_mnist/lenet300/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet300_996percent.txt" --alpha 0.0006 --lr 0.05 --keep_ratio 0.004`

ESPN_Rewind p=95%: `python prune_espn_rewind.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_fmnist_lenet300_95percent.txt" --lr 0.1 --alpha 8e-5 --keep_ratio 0.05`

ESPN_Rewind p=98%: `python prune_espn_rewind.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_fmnist_lenet300_98percent.txt" --lr 0.1 --alpha 8e-5 --keep_ratio 0.02`

ESPN_Rewind p=99%: `python prune_espn_rewind.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_fmnist_lenet300_99percent.txt" --lr 0.1 --alpha 0.00025 --keep_ratio 0.01`

ESPN_Rewind p=996%: `python prune_espn_rewind.py "fashion_mnist" "lenet300" "./output/fashion_mnist/lenet300/" --epochs_warmup 1 --logname "espn_rewind_fmnist_lenet300_996percent.txt" --lr 0.1 --alpha 0.0004 --keep_ratio 0.004`

#### Fashion-MNIST/LeNet5-Caffe

ESPN_Finetune p=95%: `python prune_espn_finetune.py "fashion_mnist" "lenet_5_caffe" "./output/fashion_mnist/lenet_5_caffe/" "./models/fashion_mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet_5_caffe_95percent.txt" --alpha 8e-5 --lr 0.05 --keep_ratio 0.05`

ESPN_Finetune p=98%: `python prune_espn_finetune.py "fashion_mnist" "lenet_5_caffe" "./output/fashion_mnist/lenet_5_caffe/" "./models/fashion_mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet_5_caffe_98percent.txt" --alpha 0.00015 --lr 0.05 --keep_ratio 0.02`

ESPN_Finetune p=99%: `python prune_espn_finetune.py "fashion_mnist" "lenet_5_caffe" "./output/fashion_mnist/lenet_5_caffe/" "./models/fashion_mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet_5_caffe_99percent.txt" --alpha 0.0002 --lr 0.05 --keep_ratio 0.01`

ESPN_Finetune p=99.6%: `python prune_espn_finetune.py "fashion_mnist" "lenet_5_caffe" "./output/fashion_mnist/lenet_5_caffe/" "./models/fashion_mnist/lenet_5_caffe/checkpoint.pth.tar" --logname "espn_finetune_fmnist_lenet_5_caffe_996percent.txt" --alpha 0.0003 --lr 0.05 --keep_ratio 0.004`

### CIFAR10/100








