# **Finding Lane Lines on the Road** 



**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Pipe line of how to detect edges and draw lines. 
a) Filter colors, only keep White and Yellow, gray out and blur the image. 
When we filter the color, we only keep Yellow and White, it is little aggressive, 
since some countries may use other colors for lane. But this method help lot o the line 
detection precision. 
[image1]: ./test_images_output/solidWhiteRight_white_yellow.jpg "white_yellow"
[image2]: ./test_images_output/solidWhiteRight_gray.jpg "gray"
[image3]: ./test_images_output/solidWhiteRight_blur_gray.jpg "blur gray"


b) Use Canny edge detection, detect the lines
Gt the lines array by Canny edge detection algorithms.
[image4]: ./test_images_output/solidWhiteRight_edges.jpg "Canny edges"

c) Scope to the region of interest, which includes the lane lines
Crop the image to region which we interested in for lane detection. How to crop the region is very empirical, the vertices we use are 
based on the images/video we have in this assignment. It may not fit all conditions.
[image5]: ./test_images_output/solidWhiteRight_region_of_interest.jpg "region of interest"


d) draw lines within the region of interest
We first draw the lines we detected in GREEN, then use linear regression, based on the slope, get two average 
slope lines from bottom to upper region, one on left, another on right. 
[image6]: ./test_images_output/solidWhiteRight_lines.jpg "lines"


e) mask the lines with the original color image. For better debug and understanding the algorithm
    e1) Use GREEN mark the lines, which may solid, may dotted
    e2) Use RED mark the linear regression line
[image7]: ./test_images_output/solidWhiteRight_color_lines.jpg "color lines"



### 2. Identify potential shortcomings with your current pipeline

1. So far the algorithm based on Color, to detect lines. This has limitations, and not fit all kind of road condition. 
Some of the lines maybe not White nor Yellow, which will be filtered out and cause issue.
2. We use several empirical settings, e.g. region of interest, which may not fit all conditions.
3. Line draw algorithms use linear line, which cannot solve curve road (lane lines) good


### 3. Suggest possible improvements to your pipeline

1. We need to use some other ways to remove the noise, then use Gray out algorithms may can help. The way to remove noise various, and not quit easy. 
2. and tune the parameter to get the region of interest more accurate. This depends where the camera installed, and whether the camera is static (not tilt).
3. The line draw algorithm need to support curve line

