# Overview

This repository contains Python code used for various image simarility experiments. The primary purpose of these tests was to determine the capabilities and limitations of individual Python modules and various techniques used for image simarility. 

The primary objective of these experiments: Provided a photo of a target person, and a set of other photos, is the target person one of the people in the set of photographs. 

The set of images used in these image simarility experiments were of well-known female actresses wearing earrings.  

![Females_with_earrings](https://github.com/johnbumgarner/image_simarility_experiments/blob/master/females_with_earrings_test_images.jpg)


## Image Simarility Experiments

### Experiment 1

This experiment used the Python module Pillow, which is a folk of PIL, the Python Imaging Library. The function used was PIL.ImageChops.difference(image1, image2), which returns the absolute value of the pixel-by-pixel difference between two images. This function was able to correctly identify the two images of Jennifer Aniston that were exactly the same.  The function produced no false positives.

### Experiment 2

This experiment used the Python module ImageHash, which was developed by Johannes Bucher.  This module has four hashing methods:

1. aHash: average hash, for each of the pixels output 1 if the pixel is bigger or equal to the average and 0 otherwise.

2. pHash: perceptive hash, does the same as aHash, but first it does a Discrete Cosine Transformation (DCT).

3. dHash:  gradient hash, calculate the difference for each of the pixel and compares the difference with the average differences.

4. wavelet: wavelet hashing, works in the frequency domain as pHash but it uses Discrete Wavelet Transformation (DWT) instead of DCT.

All four hashing methods were able to accurately identify the two images of Jennifer Aniston.  All the hashing methods produce similarity scores.  The threshold of these scores are adjustable.  

During testing the threshold for _aHash_ similar images was set at less than 20, which successful matched another Jennifer Aniston image (jennifer_anoston_earrings_03.jpeg), but produced 2 false positives.  The _aHash_ dissimilar image threshold was set at greater than 20.  The third Jennifer Aniston (jennifer_anoston_earrings.jpeg) was in this dissimilar set.  

The threshold for _dHash_ similar images was set at less than 35, which successful matched another Jennifer Aniston image (jennifer_anoston_earrings.jpeg) and produced no false positives. The _dHash_ dissimilar image threshold was set at greater than 35.  The third Jennifer Aniston (jennifer_anoston_earrings_03.jpeg) was in this dissimilar set. 

The threshold for _pHash_ similar images was set at less than 35, which did not match any addtional images of Jennifer Aniston in the control set. Setting this threshold to less than 40 produced 2 false positives. The _pHash_ dissimilar image threshold was set at greater than 40.  Both of the other Jennifer Aniston images were in this dissimilar set. 

The threshold for _wavelet_ similar images was set at less than 15, which did not match any additional images of Jennifer Aniston in the control set. Setting this threshold to less than 20 produced 2 false positives. Setting this threshold to less than 30 produced 3 false positives and identified another Jennifer Aniston (jennifer_anoston_earrings_03.jpeg) image. The _wavelet_ dissimilar image threshold was set at greater than 15.  Both of the other Jennifer Aniston images were in this dissimilar set. 






