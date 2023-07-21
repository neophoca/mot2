# Deep SORT

## Introduction

This repository provides the implementation of an object tracking system based on Deep SORT. The system integrates YOLOv5 for object detection and customizable deep learning models for ReID (Re-Identification). 


## Run in Google Colab


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/neophoca/mot2/blob/master/Modified_Deep_Sort.ipynb)


## Usage

Initialize the ModifiedDeepSort class with the desired configuration parameters:

```
mds = ModifiedDeepSort(
            device= 'cuda',
            detector_weights='./detector/yolov5x.pt',
            conf_threshold = 0.25,
            iou_threshold = 0.45,
            max_cosine_distance = 0.3,
            nms_max_overlap = 1.0,
            encoder_model_name = 'reid_model',
            encoder_model_path = './reid_models/reid_model.pt',
        )

```

Use the get_detections_and_track2 method to perform tracking on a video file:

```
detection_boxes, tracker_results, fps = mds.get_detections_and_track2('video_file_path.mp4', sort=True, save_result=True)
```

## Evaluation

You can run the evaluation script to evaluate the performance of the tracking algorithm on a set of benchmark videos:

```
results = run_evaluation(yolo_model='yolov5x', reid_model='reid_model', reid_model_path='./reid_models/reid_model.pt', conf_threshold=0.25, iou_threshold=0.45, max_cosine_distance=0.3, nms_max_overlap=1.0)
```
