# Person_Car_COCO_YOLOv5

  # Introduction
  
  This project is based on the [YOLOv5 repository](https://github.com/ultralytics/yolov5) by [Ultralytics](https://www.ultralytics.com/). It shows training on **two label (person and car) object detection**.
  
  ### Steps Covered in this Tutorial

In this project, we will walk through the steps required to train YOLOv5. We use a [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/ml-interview/openimages-personcar/trainval.tar.gz) with 2 classes (person and car).

To train our detector we take the following steps:

* Data preparation
* Run YOLOv5 training
* Evaluate YOLOv5 performance
* Visualize YOLOv5 training data
* Run YOLOv5 inference on test images
* Export saved YOLOv5 weights for future inference

### Data Preparation
    Dataset details
       Number of images: 2239
       Size: 750 MB (approx.)
       Categories: 2 (person and car)
       Annotation format: COCO (.JSON)
       
 Annotation formate of the given dataset (.JSON) is converted to YOLOv5 annotation format by using the [GitHub repo](https://github.com/pylabel-project/samples/blob/main/coco2yolov5.ipynb) and image data splited as test, validation and test sets by [Roboflow](https://roboflow.com). This is a smart web application that automatically interlocks images with labels. It offers many functions such as dataset health check which can recognise incorrectly labelled images or even image transformations like preprocessing and augmentation.

# Train Custom YOLOv5 Detector

Here, we are able to pass a number of arguments:
- **img:** define input image size
- **batch:** determine batch size
- **epochs:** define the number of training epochs. (Note: often, 3000+ are common here!)
- **data:** set the path to our yaml file
- **cfg:** specify our model configuration
- **weights:** specify a custom path to weights. (Note: you can download weights from the Ultralytics Google Drive [folder](https://drive.google.com/open?id=1Drs_Aiu7xx6S-ix95f9kNsA6ueKRpN2J))
- **name:** result names
- **cache:** cache images for faster training
        
      !python train.py --img <image size> --batch <batch size> --epochs <# of epochs> --data <path to data.yaml> --cfg <path to yolov5s.yaml> --weights '' --name <result file>  --cache

