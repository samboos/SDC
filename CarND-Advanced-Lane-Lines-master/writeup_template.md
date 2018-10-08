## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Advanced Lane Finding Project**

The goals / steps of this project are the following:

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.


## [Rubric](https://review.udacity.com/#!/rubrics/571/view) Points

---


#### 1. I started with importing all the necessary libraries ( added as I developed the code for various parts ).
First up was displaying any image. I cycled through the images to see that they followed a consistent pattern of 9 corners in the horizontal directions, and 6 in the vertical direction. 
This information is useful when computing the calibration matrix and distortion coefficients using the findChessboardCorners from OpenCV libraries.

#### 2. Distortion Correction.

A function distortion_correction was made which uses OpenCV's standard function to transform image to compensate for lens distortion. cv2.undistort function uses parameters returned by using cv2.calibrateCamera. 
This step helps to remove camera intrinsic and extrinsic variabilities before moving to the next steps of processing. 

#### 3. Apply a perspective transform 

To detect the lane lines, we have to first perform a perspective transform on the image which will give us a birds eye view. It's important to apply distortion correction before we perform perspective transform.  Applying the perspective transform would help in the next steps of thresholding and fitting polynomials. 

#### 4. Thresholding the images
Experimentation with different thresholding methods was needed to conclude which method works best. S from HLS Space, L from LUV space and B from LAB space with different thresholds were used. The results look good at this point. 

#### 4. Detect & Plot Lanes
A function "advanced_lane" is created for detecting lanes and plotting on a chosen image. 
First we use combined binary image to isolate lane line pixels and fit a polynomial to each of the lane lines. Next the space between the identified lane lines are filled to highlight the lane. Position of the vehicle is measured by taking the avg. of the x intercepts of each line. Finally, the lane lines are detected by detecting peaks of image histogram and detecting nonzero pixels in close proximity to the peaks.

#### 5. Develop a Image pipeline class using all the lessons learnt in previous steps 
Some prominent features include :
Use a sliding window to search for lane pixels in close proximity.
Use a slinding window approach to detect peaks in a histogram of the binary thresholded image. 
Pixels in close proimity to the detected peaks are considered belonging to the lane lines.

#### 6. Develop Final Pipeline : 
Function "pipeline" processes a video by decomposing each frame, and outputs vide with lane curvature annotated. 
Previous functions are used, and information about the lane lines across frames is stored to ensure smooth output. 
Additional checks are added to know if lane line was detected in previous frame. 

