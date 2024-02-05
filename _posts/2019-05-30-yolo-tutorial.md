---
layout: post
categories: posts
title: You only look once (YOLO) - Real-Time Object Detection Tutorial
tags: [Python]
date-string: MAY 30, 2019
---

### Download YOLO (Darknet)
``` sh
$ git clone https://github.com/pjreddie/darknet
$ cd darknet
```

### Makefile
First, you should adjust the setting of 'Makefile'  
```
# If you have GPU and GPU driver is installed, set this option as GPU=1
# Also, set other options as 1 if you already prepared, if not set them 0.
GPU    = 1
CUDNN  = 0
OPENCV = 0
OPENMP = 0
DEBUG  = 0
```
Then, use ```make``` command to make environment.  
``` sh
$ make

gcc -Iinclude/ -Isrc/ -DGPU -I/usr/local/cuda/include/ -Wall -Wno-unused-result -Wno-unknown-pragmas -Wfatal-errors -fPIC -Ofast -DGPU -c ./src/gemm.c -o obj/gemm.o
gcc -Iinclude/ -Isrc/ -DGPU -I/usr/local/cuda/include/ -Wall -Wno-unused-result -Wno-unknown-pragmas -Wfatal-errors -fPIC -Ofast -DGPU -c ./src/utils.c -o obj/utils.o
...
gcc -Iinclude/ -Isrc/ -DGPU -I/usr/local/cuda/include/ -Wall -Wno-unused-result -Wno-unknown-pragmas -Wfatal-errors -fPIC -Ofast -DGPU obj/captcha.o obj/lsd.o obj/super.o obj/art.o obj/tag.o obj/cifar.o obj/go.o obj/rnn.o obj/segmenter.o obj/regressor.o obj/classifier.o obj/coco.o obj/yolo.o obj/detector.o obj/nightmare.o obj/instance-segmenter.o obj/darknet.o libdarknet.a -o darknet -lm -pthread -L/usr/local/cuda/lib64 -lcuda -lcudart -lcublas -lcurand -lstdc++ libdarknet.a
```

### Dataset
Construct dataset as <a href="http://host.robots.ox.ac.uk/pascal/VOC/">PASCAL VOC</a> form.  
```
Dataset
└─ {Set Name}
   ├─ Annotations
   │   └─ 1.xml, 2.xml, ... n.xml
   ├─ ImageSets
   │   └─ Main
   │       └─ train.xml, val.xml, test.xml
   ├─ JPEGImages
   │   └─ 1.jpg, 2.jpg, ... n.jpg
   ├─ labels
   │   └─ 1.txt, 2.txt, ... n.txt
   └─ Originals
       └─ 1.jpg, 2.jpg, ... n.jpg
```

You can achieve 'labels' directory of above structure by processing the dataset using following python script.  
``` sh
$ wget https://pjreddie.com/media/files/voc_label.py
$ python voc_label.py
```

However, you can manually construct 'labels' directory as following form.
```
# class number, center x of ROI, center y of ROI, width, height
# All values are provided with ratio form
# 0             0.63             0.43             0.21   0.39
# If you have multiple ROI in one image, list it sequentially.
0 0.63 0.43 0.21 0.39
```

Then, make the text file ('train.txt', 'val.txt', and 'test.txt') containing with image path as following.
```
# {Root dirtetory of dataset}/{Set Name}/JPEGImages/{jpg name}.jpg
/home/yeonghyeon/darknet/VOCdevkit/VOC2007/JPEGImages/1.jpg
/home/yeonghyeon/darknet/VOCdevkit/VOC2007/JPEGImages/2.jpg
/home/yeonghyeon/darknet/VOCdevkit/VOC2007/JPEGImages/3.jpg
...
/home/yeonghyeon/darknet/VOCdevkit/VOC2007/JPEGImages/n.jpg
```

You need to change the contents of 'cfg/voc.data'
```
classes = {number of classes}
train   = {location of train.txt}/train.txt
valid   = {location of test.txt}/test.txt
```

### Training
Finally, you can train the YOLO Network. You can choose the network architecture in 'cfg' directory such as 'yolov3-voc.cfg'. Also, you can construct another new architecture as you want.
```
$ ./darknet detector train cfg/voc.data cfg/yolov3-voc.cfg
```

You can also use a pretrained parameter for training with the existing architecture.
``` sh
# Download the pretrained parameter.
$ wget https://pjreddie.com/media/files/darknet53.conv.74
# Append option to the tail of the command 'darknet53.conv.74'
$ ./darknet detector train cfg/voc.data cfg/yolov3-voc.cfg darknet53.conv.74
```

I used yolov3-tiny after modifying the input shape.
``` sh
layer     filters    size              input                output
    0 conv     16  3 x 3 / 1  2016 x2816 x   3   ->  2016 x2816 x  16  4.905 BFLOPs
    1 max          2 x 2 / 2  2016 x2816 x  16   ->  1008 x1408 x  16
    2 conv     32  3 x 3 / 1  1008 x1408 x  16   ->  1008 x1408 x  32  13.080 BFLOPs
    3 max          2 x 2 / 2  1008 x1408 x  32   ->   504 x 704 x  32
    4 conv     64  3 x 3 / 1   504 x 704 x  32   ->   504 x 704 x  64  13.080 BFLOPs
    5 max          2 x 2 / 2   504 x 704 x  64   ->   252 x 352 x  64
    6 conv    128  3 x 3 / 1   252 x 352 x  64   ->   252 x 352 x 128  13.080 BFLOPs
    7 max          2 x 2 / 2   252 x 352 x 128   ->   126 x 176 x 128
    8 conv    256  3 x 3 / 1   126 x 176 x 128   ->   126 x 176 x 256  13.080 BFLOPs
    9 max          2 x 2 / 2   126 x 176 x 256   ->    63 x  88 x 256
   10 conv    512  3 x 3 / 1    63 x  88 x 256   ->    63 x  88 x 512  13.080 BFLOPs
   11 max          2 x 2 / 1    63 x  88 x 512   ->    63 x  88 x 512
   12 conv   1024  3 x 3 / 1    63 x  88 x 512   ->    63 x  88 x1024  52.320 BFLOPs
   13 conv    256  1 x 1 / 1    63 x  88 x1024   ->    63 x  88 x 256  2.907 BFLOPs
   14 conv    512  3 x 3 / 1    63 x  88 x 256   ->    63 x  88 x 512  13.080 BFLOPs
   15 conv    255  1 x 1 / 1    63 x  88 x 512   ->    63 x  88 x 255  1.448 BFLOPs
   16 yolo
   17 route  13
   18 conv    128  1 x 1 / 1    63 x  88 x 256   ->    63 x  88 x 128  0.363 BFLOPs
   19 upsample            2x    63 x  88 x 128   ->   126 x 176 x 128
   20 route  19 8
   21 conv    256  3 x 3 / 1   126 x 176 x 384   ->   126 x 176 x 256  39.240 BFLOPs
   22 conv    255  1 x 1 / 1   126 x 176 x 256   ->   126 x 176 x 255  2.895 BFLOPs
   23 yolo
Loading weights from darknet53.conv.74...yolov3-tiny
Done!
Learning Rate: 0.001, Momentum: 0.9, Decay: 0.0005

...
```
