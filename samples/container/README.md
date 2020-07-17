# Mask R-CNN Application on Container Classification

This is an application showing the use of Mask RCNN in a real-world dataset.
We use pre-trained coco weights to train the model to detect different types of containers.
Potential classes include: Cola Bottle, Fanta Bottle, Cherry Coke Bottle, Coke Zero Bottle, Mtn Dew Bottle, Cola Can, Fanta Can.



## Installation
1. From the [Releases page](https://github.com/matterport/Mask_RCNN/releases) page, download `mask_rcnn_coco.h5`. Save it in the root directory of the repo (the `mask_rcnn` directory).
2. The annotated image information saved as json files are stored under https://github.com/siyuan-song/Container/tree/master/samples/container/dataset (one for train and one for validation). The files are created manually using VIA (VGG Image Annotator, version 2.0) at http://www.robots.ox.ac.uk/~vgg/software/via/via.html.


## Train the Container model

Train a new model starting from pre-trained COCO weights
```
python container.py train --dataset=/path/to/container/dataset --weights=coco
```

Resume training a model that you had trained earlier
```
python container.py train --dataset=/path/to/container/dataset --weights=last
```

Train a new model starting from ImageNet weights
```
python container.py train --dataset=/path/to/container/dataset --weights=imagenet
```

The code in `container.py` is set to train for 3K steps (30 epochs of 100 steps each), and using a batch size of 1. 


## Test and evaluate the Container model

Use a single image to test and show the performance of the model, calculate the mean Average Presicion (mAP) using all 40 images in validation set.
(Modify the path to the trained model)
```
python demo.py
```
