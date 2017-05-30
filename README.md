# Project: Lane Finding on Images and Videos

This project is completed as part of the Udacity Self-Driving Car Nanodegree Program. The objective of this project was to detect lane lines on test images and videos provided by the course administrators.

## Overview

This project largely uses the `OpenCV` library to apply transformations to the images making up a video stream, to detect lane lines. Classification techniques for lines were more open-ended, and were done using Hough Transforms and weighted interpolation across the results.

## Files and Folders

The `P1.ipynb` is a Jupyter Notebook (Python3 environment) that contains the code to execute the tests on provided image and video files. To use your own images/videos, change the file paths in the code accordingly.

Under the `test_videos/` folder are the results of running the code on the provided sample videos by Udacity.

The `writeup.md` file contains more detail on the image processing and lane classification pipeline used to achieve the desired results
