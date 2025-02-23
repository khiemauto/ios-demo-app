# Object Detection with YOLOv5 on iOS

## Introduction

[YOLO](https://pjreddie.com/darknet/yolo/) (You Only Look Once) is one of the fastest and most popular object detection models. [YOLOv5](https://github.com/ultralytics/yolov5) is an open-source implementation of the latest version of YOLO (for a quick test of loading YOLOv5 from PyTorch hub for inference, see [here](https://pytorch.org/hub/ultralytics_yolov5/#load-from-pytorch-hub)). This Object Detection with YOLOv5 iOS sample app uses the PyTorch scripted YOLOv5 model to detect objects of the [80 classes](https://github.com/ultralytics/yolov5/blob/master/data/coco.yaml) trained with the model.

## Prerequisites

* PyTorch 1.9 and torchvision 0.10 (Optional)
* Python 3.8 (Optional)
* iOS Cocoapods LibTorch-Lite 1.9.0 and LibTorchvision 0.10.0
* Xcode 12 or later

## Quick Start

To Test Run the Object Detection iOS App, follow the steps below:

### 1. Prepare the Model

If you don't have the PyTorch environment set up to run the script, you can download the model file [here](https://pytorch-mobile-demo-apps.s3.us-east-2.amazonaws.com/yolov5s.torchscript.ptl) to the `ios-demo-app/ObjectDetection/ObjectDetection` folder, then skip the rest of this step and go to step 2 directly.

The Python script `export.py` in the `models` folder of the [YOLOv5 repo](https://github.com/ultralytics/yolov5) is used to generate a TorchScript-formatted YOLOv5 model named `yolov5s.torchscript.ptl` for mobile apps.

Open a Mac/Linux/Windows Terminal, run the following commands (note that we use the fork of the original YOLOv5 repo to make sure the code changes work, but feel free to use the original repo):

```
git clone https://github.com/jeffxtang/yolov5
cd yolov5
pip install -r requirements.txt
```

Finally, run the script below to generate the optimized TorchScript Lite Interpreter model and copy the generated model file `yolov5s.torchscript.ptl` to the `ios-demo-app/ObjectDetection/ObjectDetection` folder:

```
python models/export.py
```

Note that small sized version of the YOLOv5 model, which runs faster but with less accuracy, is generated by default when running the `export.py`. You can also change the value of the `weights` parameter in the `export.py` to generate the medium, large, and extra large version of the model.

### 2. Use LibTorch-Lite

Run the commands below:

```
pod install
open ObjectDetection.xcworkspace/
```

### 3. Run the app
Select an iOS simulator or device on Xcode to run the app. You can go through the included example test images to see the detection results. You can also select a picture from your iOS device's Photos library, take a picture with the device camera, or even use live camera to do object detection - see this [video](https://drive.google.com/file/d/1pIDrUDnCD5uF-mIz8nbSlZcXxPlRBKhl/view) for a screencast of the app running.

Some example images and the detection results are as follows:

![](screenshot1.png)
![](screenshot2.png)

![](screenshot3.png)
![](screenshot4.png)
