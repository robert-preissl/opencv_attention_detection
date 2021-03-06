# opencv_attention_detection
This is an OpenCV based attention detection demo: using Caffe models as well as cascade classifiers.

## Scope

This is a C++ based demo for an attention detection system using OpenCV.

In detail, we have been analyzing the camera feed of a laptop to detect a simple set of relevant features to infer if a person in front of the camera pays attention to the screen yes or no.

The set of features extracted in this demo are face plus eyes of a person.

We are using a very simple algorithm to detect if a person pays attention (e.g., is currently working on the computer or not):
We assume a person is sitting right in front of a camera (i.e., in a roughly 90 degrees angle to the camera), and we analyze the position of the detected eyes. From the position of eyes we infer if a person pays attention to the screen.

## Main contributions to share with the community

### Jupyter notebook

The included notebook demonstrates how to use the C++ Jupyter kernel [xeus-cling](https://github.com/jupyter-xeus/xeus-cling). Jupyter notebooks are a great way of quickly iterating on ideas before moving them to a production environment.

Most popular are python based Jupyter notebooks, but not always is Python the language for a production system.

This demo demonstrates that C++ (up to C++-17) kernels are available too and work great even with more sophisticated libraries such as OpenCV.

### Attention detection with OpenCV using a combination of two different methods

First, we are using OpenCV's deep neural network module with an openly available Caffe model for face detection.

Second, if a face has successfully been detected, we are using a Haar feature-based cascade classifier to detect eyes within the previously detected facial region.

#### Optimization

Note, at least on a not so powerful laptop computer it took in the order of 100ms to run a single iteration of the cascade classifier. when cropping the video frame to the detected face and running the classifier just within this region of interest, we successfully reduced the runtime complexity by 5 to 10x.

### Results

Below is an image showing a scenario where the operator does not focus on the computer screen. Despite the cascade based classifier successfully detecting both eyes, our simple attention checking algorithm (using the eye positions) infers a negative attention to the screen. 
![Example of negative attention to the computer screen ](https://github.com/robert-preissl/opencv_attention_detection/blob/master/pics/attention_negative_1.png "Attention detection is negative")

In contrast, this is an example of a positive attention detection. For a positive detection, we need to detect the face + both eyes and, in addition, the eye positions have to fulfill certain symmetry requirements in respect to the facial region.
![Example of positive attention to the computer screen ](https://github.com/robert-preissl/opencv_attention_detection/blob/master/pics/attention_positive_1.png "Attention detection is positive")


