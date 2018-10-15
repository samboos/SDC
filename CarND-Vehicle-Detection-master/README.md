

The goals / steps of this project are the following:

From the vehicle(8792) and non vehicle(8968) dataset, I used the standard code for color_hist, bin_spatial and get_hog_features.
In addition a class (Parameters) was made to hold all the parameters as objects of the class.  
The function extract_features combine the functions above to extract the features. 

Next I trained the SVC using the vehicle and non-vehicle dataset. 
As part of this :   
1. We create an array of feature vectors.
2. Scale the data and transform it in the X direction
3. Split the data into training and test data
4. train using the training dataset
5. Test accuracy using the test data

Based on the standard examples, a draw_boxes function was developed to draw boxes around a detected image ( this will be used in later parts of the code ) 

To search the image for vehicles, a sliding window function was made. 
This function accepts an image, start and stop positions in both x and y co-ordinates, window size desired and fraction of overlap. 

This sliding window function is then used in the search function. The search function makes use of the extract_features function defined prior. 
If a vehicle is found using the search function in the sliding window, that window is appended as a box to the image. 

Above process though results in multiple boxes, and we need a heat map function. Here we have used the standard functions provided by Udacity : add_heat, apply_threshold and draw bounding boxes. 

Applying these functions, we can detect better bounding boxes. 

At this point, we have a good foundation after experimentation to make the final pipeline. This is implemented in findBoxes function which uses many of the lessons learnt in the previous functions. 
We also improve the the performance with HOG subsampling. 
This function is used in the final pipeline during the processing of image. 

With the foundation function available to process an image, we make use use of moviepy editor functions to process the video frame by frame. 



Discussion : 

Even though SVC has been used, there are many advanced deep learning techniques available for vehicle detection. 
Another update could be to detect the horizon and automatically mask out only those places where a vehicle can show up.
The pipeline to process images is slow, Using well trained CNN's can make this process faster. 
Another option would be to change for different X and Y values to minimize the number of windows to process.