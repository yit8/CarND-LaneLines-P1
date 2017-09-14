# CarND-LaneLines-P1
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Pipeline description. 

My pipeline consisted the following steps:

First, the images are pre-processed with grey scale transforming, gaussian blurring, canny edge and masking;

After that, hough line detection is used with tuned parameters. The returning values are a list of rho and theta;

In last step, since the required result are two lines representing left and right sides of lane, k-means clustering is used to average the results. Two centers are returned, ie the two lines.

In order to draw a single line on the left and right lanes, theta and rho are used to find two points, by combining which a line could be formed. 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be this technique requires that only segments of the two target lines should be found in houghline stage, otherwise any other lines will heavily affect the centers returned by k-means. To achieve this, threshold for houghline is set pretty high. However, other lines still could get detected.

Another shortcoming could be that the result is not stable. 


### 3. Suggest possible improvements to your pipeline

For the first shortcoming, an outlier rejection technique could be used, through which influence from line segments that are too far from center can be removed.

For the second shortcoming, a tracking algorithm such as Kalman filter could be used. 
