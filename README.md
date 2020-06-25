# opencv_attention_detection
OpenCV based attention detection demo: using Caffe models as well as cascade classifiers

## Scope

This is a C++ based demo for an attention detection system using OpenCV.

In detail, we have been analyzing the camera feed of a laptop to detect a simple set of relevant features to infer if the person in front of the camera pays attention to the screen yes or no.

The set of features extracted in this demo are face plus eyes of a person.

We are using a very simple algorithm to detect if a person pays attention (e.g., is currently working on the computer or not):
We assume a person is sitting right in front of a camera (i.e., in a roughly 90 degrees angle to the camera), and we analyze the position of the detected eyes. From the position of eyes we infer if a person pays attention to the screen.

## Main contribution to share with the community

### Jupyter notebook

The included notebook demonstrates how to use the C++ Jupyter kernel [xeus-cling](https://github.com/jupyter-xeus/xeus-cling). Jupyter notebooks are a great way quickly iterating on ideas before moving them to production.
Mostly people use python based Jupyter notebooks, but this demo demonstrates that C++ (up to C++-17) kernels are available too and work great.

### Attention detection with OpenCV using two different methods

First, we are using OpenCV's deep neural network module with some openly available Caffe model for face detection.
Second, if a face has been successfully detected, we are using a Haar feature-based cascade classifier to detect eyes within the previously face region.

#### Optimization

Note, at least on a not so powerful laptop computer it took in the order of 100ms to run a single iteration of the cascade classifier. when cropping the video frame to the detected face and running the classifier just within this region of interest, we successfully reduced the runtime complexity by 5 to 10x.

### Results


