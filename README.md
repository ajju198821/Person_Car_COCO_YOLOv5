# Person_Car_COCO_YOLOv5

  # Introduction
  
  This project is based on the [YOLOv5 repository](https://github.com/ultralytics/yolov5) by [Ultralytics](https://www.ultralytics.com/). It shows training on **two label (person and car) object detection**.
  
  ### Steps Covered in this Tutorial

In this project, we will walk through the steps required to train YOLOv5. We use a [COCO dataset](https://evp-ml-data.s3.us-east-2.amazonaws.com/ml-interview/openimages-personcar/trainval.tar.gz) with 2 classes (person and car).

To train our detector we take the following steps:

* Data preparation
* Install YOLOv5 dependencies
* Download custom YOLOv5 object detection data
* Write our YOLOv5 Training configuration
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
       Annotation format: COCO 
