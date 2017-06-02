# **Finding Lane Lines on the Road** 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

## Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
The image processing pipeline is as follows:

1. The provided image(s) were converted to grayscale (in preparation for Canny Edge Detection) 
2. The Canny Edge Detection helper function was used to create an image containing the edges. A 3:1 ratio was used for high and low thresholds as was suggested by the developer of this technique (a Gaussian blur with a kernel size of 5 was also applied prior to the Canny application).
3. A 4-sided Polygon mask was used to isolate the region of the interest (i.e. the lane). An approximate of the vertices of this polygon was found manually through observing the images and video streams.
4. The Hough Transform was used to determine which points formed line segments.
5. The draw_lines() function was modified through the addition of another function combine_line_segs (or combine_line_segs_2; an alternative implementation of the function), which was used to combine broken line segments into single, straight lines for each lane line.

Expanding on the combine_line_segs implementation, it classifies the line segments obtained from the Hough Transform through classifying their gradients into 3 bins (one for the right lane, one for the left and the last for all unremarkable features/horizontal lines). A weighted average of the gradients and intercepts for each lane line is then calculated, with the greatest weights assigned to the line segments at the bottom of the image (where the lanes are observed to be thicker and more reliable than the line segments seen further up along the road). 

combine_line_segs_2() is only different in the way lines are classified, using the x-coordinates of the line segments rather than their gradients. This was done in an effort to not rely on gradients as both lanes may exhibit similar gradients along winding roads.

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

The code does not work on the optional challenge video due to shortcomings in the classification of various features along the road which are mistaken for lane lines.

### 3. Suggest possible improvements to your pipeline

A possible improvement to circumventing the above problem might be to use mutliple parameters (e.g. gradient and intercepts) to sort line segments rather than just a single parameter. 
