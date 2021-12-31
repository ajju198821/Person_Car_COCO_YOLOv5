# Introduction

This project is based on the [YOLOv5 repository](https://github.com/ultralytics/yolov5) by [Ultralytics](https://www.ultralytics.com/). This notebook shows training on Two lable (person and cars) [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/mlinterview/openimages-personcar/trainval.tar.gz). 

### Steps Covered in this Tutorial

In this project, we will walk through the steps required to train YOLOv5 on [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/mlinterview/openimages-personcar/trainval.tar.gz). You can also use this notebook on your own data.

To train our detector we take the following steps:

* Dataset details
* Run YOLOv5 training
* Evaluate YOLOv5 performance
* Visualize YOLOv5 training data
* Run YOLOv5 inference on test images
* Export saved YOLOv5 weights for future inference

# Dataset details

    Number of images: 2239
    Size: 750 MB (approx.)
    Categories: 2 (person and car)
    Annotation format: COCO (.JSON)

The above data set annotation formate is COCO (.JSON). We are using YOLOv5 to train the data and annotation need to be compatible with model i used the [GitHub repo](https://github.com/pylabel-project/samples/blob/main/coco2yolov5.ipynb). Dataset splited as train, validation (val) and test by using [Roboflow](https://roboflow.com). This is a smart web application that automatically interlocks images with labels. It offers many functions such as dataset health check which can recognise incorrectly labelled images or even image transformations like preprocessing and augmentation.

# Run YOLOv5 training

Here, we are able to pass a number of arguments:
- **img:** define input image size
- **batch:** determine batch size
- **epochs:** define the number of training epochs. (Note: often, 3000+ are common here!)
- **data:** set the path to our yaml file
- **cfg:** specify our model configuration
- **weights:** specify a custom path to weights. (Note: you can download weights from the Ultralytics Google Drive [folder](https://drive.google.com/open?id=1Drs_Aiu7xx6S-ix95f9kNsA6ueKRpN2J))
- **name:** result names

      !python train.py --img <inage size> --batch <batch size> --epochs <# of epochs> --data <path to data.yaml> --cfg <path to conf yolov5s.yaml> --weights '' --name <result name> 
      
# Evaluate YOLOv5s performance

The image below shows the performance of model YOLOv5s. We train this model with following imputs
     
        image size : 416
        batch size: 16
        # no epochs: 100
     
From the below metrics, Box is one of the most common evaluation metrics applied in object detection. In general, it defines the area of taken into account shapes and is a good indicator of a loss function. Whereas, mAP - mean Average Precision measures the accuracy of the examined object detector. This is correlated with precision and recall. I ran this Notebook
