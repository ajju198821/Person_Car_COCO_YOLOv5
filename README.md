# Introduction

This project is based on the [YOLOv5 repository](https://github.com/ultralytics/yolov5) by [Ultralytics](https://www.ultralytics.com/). This notebook shows training on Two lable (person and cars) [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/mlinterview/openimages-personcar/trainval.tar.gz). 

### Steps Covered in this Tutorial

In this project, we will walk through the steps required to train YOLOv5 on [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/mlinterview/openimages-personcar/trainval.tar.gz). You can also use this notebook on your own data.

To train our detector we take the following steps:

* Dataset details
* Run YOLOv5 training
* Evaluate YOLOv5 performance
* Run YOLOv5 inference on test images
* Results

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
     
From the below metrics, Box is one of the most common evaluation metrics applied in object detection. In general, it defines the area of taken into account shapes and is a good indicator of a loss function. Whereas, mAP - mean Average Precision measures the accuracy of the examined object detector. This is correlated with precision and recall. I ran this [Notebook](https://github.com/ajju198821/Person_Car_COCO_YOLOv5/blob/main/Person_Car_COCO_Train_YOLOv5s.ipynb) on Google Colab. It seems that, even the model trained for 100 epochs, the model not generalized well. 

![results](https://user-images.githubusercontent.com/47291136/147813544-5a629d04-b54e-4169-87c2-1d6f29749700.png)

# Run YOLOv5 inference on test images

    !python detect.py --weights <path to trained weights> --img <image size> --conf <confedance score> --source <path to test images>

# Results

Below are the some results on test data after training the model.

| Test Image 1      | Test Image 2     | Test Image 3 |
|------------|-------------|-------------|
|![image_000001576_jpg rf 5250624f2e5af885ea1d1a20f518ac2b](https://user-images.githubusercontent.com/47291136/147813946-bd3dba49-4c45-4a66-8412-2425022e7a7b.jpg) | ![image_000001892_jpg rf 74044ad2084bf8b09ba4b10f8410ac7e](https://user-images.githubusercontent.com/47291136/147814306-f0f78969-8c7c-40c7-84de-e02a93303871.jpg) |![image_000002235_jpg rf 11c93ed7c29325c2339f9e9e02cd7a5d](https://user-images.githubusercontent.com/47291136/147814355-83d897cf-6e9e-40ac-bde5-9e73d8096d78.jpg)|
