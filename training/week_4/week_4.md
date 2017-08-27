# Purdue CAM2: Image Team Training, Week 4

## Overview

This week we will go implement a deep learning model on your computer, preferrably in Caffe. While there are other versions available for these models, such as the original MATLAB version of Faster-RCNN, I will not be much help...

We want to know how to use deep learning models, and how to use them for our specific task of identifying people.

- Faster-RCNN (FRCNN) \[[pdf](https://arxiv.org/abs/1506.01497)\]\[[github](https://github.com/rbgirshick/py-faster-rcnn)\]
- Single Shot Detector (SSD) \[[pdf](https://arxiv.org/abs/1512.02325)\]\[[github](https://github.com/weiliu89/caffe/tree/ssd)\]

For FRCNN I will provide you a set of weights trained on COCO, PASCAL VOC, but fine-tuned on ImageNet. This means the "head" of model will output 200 classes.

For SSD, the weights are made available at the github page. [I've linked the ILSVRC trainval1 weights here](https://drive.google.com/open?id=0BzKzrI_SkD1_a2NKQ2d1d043VXM) :smile:

If you are stuck on any of the material, please email me at gauenk@purdue.edu with your questions!

## Tasks

1. Get training started for your model. No need to finish training. Please send me a screen-shot of the model training.

2. For the PASCAL VOC 2012 training-set and the CAM2 dataset:
   - report the mAP of your model
   - visualize 10 detected images

   For the PASCAL VOC 2012 dataset, also plot the AP plots for each class with (a) not threshold and (b) a threshold at confidence of 0.5 or greater.

   Remember to ignore output for classes that don't exist in the dataset.

## To Submit:
- Screenshot of training
- PASCAL VOC 2012
    1. mAP
    2. 10 detected images
    3. AP Plots
- CAM2
    1. mAP
    2. 10 detected images

## FRCNN Caffe Install Note:

After cloning, we need to update the actual *caffe* to support the current CUDNN. See issue \[[237](https://github.com/rbgirshick/py-faster-rcnn/issues/237)\]

```
cd caffe-fast-rcnn  
git remote add caffe https://github.com/BVLC/caffe.git  
git fetch caffe  
git merge -X theirs caffe/master
```

Now we need to make sure it works with Python2.7. See issue \[[249](https://github.com/rbgirshick/py-faster-rcnn/issues/249)\]. Edit the "python_layer.hpp" file:

```
self_.attr("phase") = static_cast(this->phase_);
```

goes to

```
//self_.attr("phase") = static_cast(this->phase_);
```