# **Finding Lane Lines on the Road** 

## Term 1, Project 1 Submission writeup

**Project 1: Find Lane Lines on the Road**

The goals of this project are the following:
* Implement a pipeline that finds lane lines on the road
* Reflect on my work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/original.png "Original"
[image2]: ./test_images_output/gaussian.png "Gaussian"
[image3]: ./test_images_output/canny.png "Canny-Edges"
[image4]: ./test_images_output/hough.png "Hough Transformed"
[image5]: ./test_images_output/merge.png "Merged"
[image6]: ./test_images_output/Unannotated_left_lane.PNG "Incomplete annotated"

---

### Reflection on my "ever in works" P1 commit

### 1. Lane Detection Pipeline Description: 

My pipeline consists of following key steps:-

 - Convert RGB to grayscale 
 - Apply a Gaussian blur 
 - Perform Canny edge detection 
 - Define a region of interest to develop a mask 
 - Retrieve Hough lines  
 - Apply lines to  the original image

The key concept for identification of lines within an image revolves around two functions: 

 1. Edge detection using [Canny algorithm](https://en.wikipedia.org/wiki/Canny_edge_detector)
 2. Specific line detection using [Hough transform](https://alyssaq.github.io/2014/understanding-hough-transform/)

The supporting actions like grayscaling and color threshold matching are implemented to ensure higher fidelity of extraction of features of interest in the image.

Here are the images after each of the steps above starting with original image to see the pipeline in action.

*Original Image*
![alt text][image1]

*Gaussian Blurred Image*
![alt text][image2]

*Canny Edge Detected Image*
![alt text][image3]

*Hough Transformed Image*
![alt text][image4]

*Final Merged Imaged*
![alt text][image5]

The key effort was also involved in extracting and extrapolating lines of interest after the image was processed with all the edges. This was done with following key steps:-

 1. Adjusting threshold parameters for proper edge detection
 2. Region selection to apply mask; this requires many variables to be adjusted mainly to get the mask aligned within an image to extract the features of interest (lanes in our case) in a best manner.
 3. Adjusting Hough transform parameters such as voting threshold for line identification, line segment and distance separation parameters, "rho" and radian selection for grid resolution.

The above iteration was quite time consuming and often times due to incorrect selection, I would end up having annotation within image mainly on a solid line which is an easier feature to extract as seen below.

*Incomplete Annotated Image*
![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline

My initial solution ran well on the sample image and video streams. 
However there were times when the image showed up unannotated which led to lines appearing jumpy when the video was running. This was mentioned in the previous section. 


Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

These are some of the ways I have explored to improve my solution:-

 - Operate on a modified color map of the video to allow of greatest  emphasis to contrast the yellow and white lanes
 - Extract color channel information from properly modified map to use for further feature emphasis 
 - Develop elaborate region of interest polygon shape to clearly mask out areas which are not of interest
 - Draw line function can further be improved if we calibrate range of slopes to select for the lane lines
 - Tweak the parameters for Hough transform to improve the line detection for the lanes especially on the
 - Implement averaging pipeline of 3 frames in a video stream before am a new averaging pipeline can be added to average say 3 frames before running lane detect to eliminate lane jumping from frame to frame.

Effects of some of the improvements are shown in the solution on the challenged video. 
