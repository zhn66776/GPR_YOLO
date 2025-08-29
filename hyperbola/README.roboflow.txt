
hyperbola - v6 2025-08-16 3:05pm
==============================

This dataset was exported via roboflow.com on August 29, 2025 at 8:28 PM GMT

Roboflow is an end-to-end computer vision platform that helps you
* collaborate with your team on computer vision projects
* collect & organize images
* understand and search unstructured image data
* annotate, and create datasets
* export, train, and deploy computer vision models
* use active learning to improve your dataset over time

For state of the art Computer Vision training notebooks you can use with this dataset,
visit https://github.com/roboflow/notebooks

To find over 100k other datasets and pre-trained models, visit https://universe.roboflow.com

The dataset includes 2137 images.
Objects are annotated in YOLO v5 PyTorch format.

The following pre-processing was applied to each image:
* Auto-orientation of pixel data (with EXIF-orientation stripping)
* Resize to 640x640 (Fit (black edges))

The following augmentation was applied to create 3 versions of each source image:
* 50% probability of horizontal flip
* Random brigthness adjustment of between -24 and +24 percent
* Random exposure adjustment of between -14 and +14 percent
* Random Gaussian blur of between 0 and 2 pixels
* Salt and pepper noise was applied to 1.7 percent of pixels


