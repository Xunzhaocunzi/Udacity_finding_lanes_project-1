# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

1. Identify the regions that include most of the lane lines and screen them out. 

2. Using color threshold to find out the yellow and white lane lines. The thresholds need careful selections otherwise they may not work well, either they will select more than the lane lines, or they will select only a portion of lane lines. Both of them will make edge detection work worse.

3. Apply Canny Edge detection and Hough Transform to process the chosen image. 

4. Connect the segments of the lines together, and only keep one solid line for each lane line. In order to draw a single line on the left and right lanes, I modified the draw_lines() function by obtaining the slope for left and right lane line, and averaging all the points of left and right lane lines seperately to get 2 points for each lane. Then y=Ax+B equation can be obtained for each lane. This method works well in most cases, however,  

5. Complete the process_image() function to integrate all the previously defined functions and generate the result with plt.imshow() function. 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane line markers are rarely clear in the image. This would cause canny edge detection function not work well. In this case, low and high thresholds need to carefully selected.  

Another shortcoming could be that yellow lane line and road surface are mixed and the code cannot diffientiate them well apart. It is very obvious in the challenge video. Possible improvement would be using different color thresholds and small region to reduce noise. 

### 3. Suggestions for improving the algorithem

1. One of improvements might be to use convert the image to HSL first to better identify yellow and white colors. 

2. The other one I can image is to use a better described trapzoid to identify the region of interest. 

