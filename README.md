# **Finding Lane Lines on the Road** 
# Author: Anirudh Kumar Agrawal
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.
1. Conver a RGB image to grayscale, this is done to be able to apply a gradient based edge detector
2. Use Gaussian Blurring, the idea of gaussian blur is reduce hte impact of noise in the image. Noise can be introduced to a variety of reasons ranging from faulty camera or low resolution camera. The reason that would affect the current task is that because noisy pixels will affect edge detection algorithm
3. Use Canny Edge Detector, it is gradient based Edge Detector. The idea is to find gradeint at each pixel and then find pixels which have gradient given above the thresholds. The two thresholds are used to classify weak and strong edge pixels.
4. Apply Hough transform, which be able to identify points belonging to a line by converting the image to Hough space.
5. Combine the individual line segements to a single left and right lane. This is describe in detail in the coming section

In order to draw a single line on the left and right lanes,
a. Partition the line segments into left and right lane. For the current image set this could be done by comparding slopes of the line segments. Left lane has negative slope while hte right lane has positive slope( this might be non-intuititve seeing the image but this is so because y-axis is inverted in opencv space)
b. Run a polynomial line fitting algorithm on the given points. I have used NumPy polyfit algorithm
c. Choose ymin and ymax from our region of interest and then find the corresponding x values, this will use line segement extending over the full Region of Interest

Below are some of the failed attempts the learninig that I derived from them
1. To separate line segments into left and right lane I tried using avergae of x as the separator. While this worked great for a single image this didn't work so well while using vidoes. Some points was being misclassified causing errorneous line segements to appear.

![image text](test_image_output/solidWhiteRight.jpg "Lane for Solid White Right")

### 2. Identify potential shortcomings with your current pipeline

There a few shortcomings in the current pipeline as used
1. Clipping of the image is very subjective to given dataset and isn't universal. It will be an entire task to identify which the part of hte image should be our region of interest.
2. The algorithm can't handle curved lines right now
3. If there is a car also very close to lines and white in the color it impacts algorithm. In the curren task this was overcome by definining a very tight Region of Interest

### 3. Suggest possible improvements to your pipeline

Possible improvements to the current pipeline could be the following
1. Instead of using an line approximation we can use higher order curve fitting algorithm, to accomodate this with hough transform we we will have set values such that its able to give very small line segments.
