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
        
      !python train.py --img <image size> --batch <batch size> --epochs <# of epochs> --data <path to data.yaml> | 
      --cfg <path to yolov5s.yaml> --weights '' --name <result file>  --cache

# Evaluate YOLOv5 performance
  
  I ran this Notebook in Colab by using its GPU for 100 epochs, and batch size - 16 with model YOLOv5s. Images below present BBox and objectiveness for both training and validation data, detecting precision with recall, mean Average Precision.
  
  We will discuss about BOX and mAP. BOX is one of the most common evaluation metrics applied in object detection. In general, it defines the area of taken into account shapes and is a good indicator of a loss function. Whereas, mAP - mean Average Precision measures the accuracy of the examined object detector. This is correlated with precision and recall. With this model, the results seems to not generalized well. By the Colab, this model trained for around 1hr 23 mins. 
  
  ![results](https://user-images.githubusercontent.com/47291136/147809027-82d22d1c-2a3d-42d7-a1c0-625d187dfb71.png)
  
  # Visualize YOLOv5 results
  
  | Test image 1      | Test image 2 | Test image 3 |
|------------|-------------|-------------|
| ![image_000002235_jpg rf 11c93ed7c29325c2339f9e9e02cd7a5d](https://user-images.githubusercontent.com/47291136/147809778-cc8716af-c91b-4dbb-ac50-6e255761c400.jpg) | ![image_000001892_jpg rf 74044ad2084bf8b09ba4b10f8410ac7e](https://user-images.githubusercontent.com/47291136/147809903-3a868611-ed1d-4ded-9d5b-b9dc61d7ab9e.jpg) | [image_000001892_jpg rf 74044ad2084bf8b09ba4b10f8410ac7e](https://user-images.githubusercontent.com/47291136/147809903-3a868611-ed1d-4ded-9d5b-b9dc61d7ab9e.jpg) |
