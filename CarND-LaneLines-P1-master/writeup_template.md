# **Finding Lane Lines on the Road** 

## Writeup Template


**Finding Lane Lines on the Road**

To find the Lane Lines on the road, I used the same methods as given during the lessons & exercises as part of lessons. 
Similar to the lessons, I first took the grayscale of color image, applied gaussian blur, then canny edge detection.
The region definition also used similar to lesson exercises. Hough lines & weighted image functions also were just a process of making helper functions.
Some of the thresholds had to be change through experimentation. 


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

Most of the pipeline to find lines & get ROI worked right away. I was stuck for a little while in the modification to draw_lines for extrapolation / averaging. 
The logic in draw lines for extrapolation/ averaging is as follows : For all the lines found in the region of interest, only the ones with certain slope are only considered, and rest are ignored.
Assumption is that the lines in this slope ranges are the lane lines. All of these lines are then averaged, and a line from the bottom of the picture is drawn with the slope of this averaged line, and a common point. 


### 2. Identify potential shortcomings with your current pipeline

This logic assumes that lanes are always in certain slope. That may not always be the case. 
This also assumes that the lane markings work for the two cases that we are tasked with. However, if the lighting conditions, or roads coloring/contrast change - then the logic would have to be re-validated again.
Also the image size is considered a constant - So if the camera changed - that would be an issue. 


### 3. Suggest possible improvements to your pipeline

Current code can be improved by dynamically adjusting various parameters to ensure that lanes are always found. Making it such would work for various light & contrast scenarios. 
Also the image size can be made variable. 
Looking for perpendecular lines are of use too.. To find intersections. 
I am not sure if finding intersections is a separate piece of logic in practice. 