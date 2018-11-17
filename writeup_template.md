# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied Gaussian smoothing with a defined kernel_size. Afterwards, Canny was applied with low_threshold of 50 and high_threshold of 150. region_of_interest was set by fine-tuned vertices. Hough line were created, which then used for "color" binary image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by using the slope as indicator of left and right. As I figured whether it is left line or right line, I simply took min() or max of each line segment accordingly for extrapolation.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are lines too short or a blob is located between lines. 

Another is objects at the top of region_of_interest. When there are objects like vehicle along the edges of region_of_interest, erroneous lines could be created.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to fine tune Hough transfrom parameters so that the pipeline gets the line reliably.
