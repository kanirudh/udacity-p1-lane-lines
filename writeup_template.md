# **Finding Lane Lines on the Road** 
# Author: Anirudh Kumar Agrawal
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

My pipeline consisted of 5 steps.
1. Conver a RGB image to grayscale, this is done to be able to apply a gradient based edge detector
2. Use Gaussian Blurring, the idea of gaussian blur is reduce hte impact of noise in the image. Noise can be introduced to a variety of reasons ranging from faulty camera or low resolution camera
3. Use Canny Edge Detector, it is gradient based Edge Detector
4. Apply Hough transform, which be able to identify points belonging to a line by converting hte image to Hough space.
5. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

There multiple shortcomings in the current pipeline
1. Clipping of the image is very subjective to given dataset and isn't universal
2. The algorithm can't handle curved lines right now
3. If there is a car also very close to lines and white in the color it impacts algorithm.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
