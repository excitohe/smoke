This repository is forked from the official implementation [SMOKE: Single-Stage Monocular 3D Object Detection via Keypoint Estimation](https://arxiv.org/pdf/2002.10111.pdf) with some updates. Private function only.

## Resource

The pretrained weights can be downloaded [here](https://drive.google.com/open?id=11VK8_HfR7t0wm-6dCNP5KS3Vh-Qm686-).

## Requirements
All codes are tested under the following environment:
*   Ubuntu 16.04
*   Python 3.8
*   Pytorch 1.8.1
*   CUDA 11.1

## Dataset
We train and test our model on official [KITTI 3D Object Dataset](http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=3d). 
Please first download the dataset and organize it as following structure:
```
kitti
│──ImageSets
│──training
│    ├──calib
│    ├──label_2 
│    └──image_2
└──testing
     ├──calib
     └──image_2
```  

## Install

```
git clone git@github.com:excitohe/smoke.git

python setup.py develop

mkdir datasets

ln -s /path_to_kitti_dataset datasets/kitti
```

## Getting started
First check the config file under `configs/`. 

We train the model on 4 GPUs with 32 batch size:
```
python tools/plain_train_net.py --num-gpus 4 --config-file "configs/smoke_dla34_gn.yaml"
```

For single GPU training, simply run:
```
python tools/plain_train_net.py --config-file "configs/smoke_dla34_gn.yaml"
```

We currently only support single GPU testing:
```
python tools/plain_train_net.py --eval-only --config-file "configs/smoke_dla34_gn.yaml"
```
