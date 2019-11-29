# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

---

### Reflection


My pipeline consisted of 4 steps. 
1) First, I applied the canny function, 
2) then I choose the region of interest of the canny filter output
3) then I applied the hough transform
4) and then cut the output of hough transform by the region on interest again

In order to draw a single line on the left and right lanes, I modified the draw_lines() function to saparate all found line by positive and negative slopes (so that data points from the left line do not interfere with the right line) then I calulated the mean of the slope and y intercept of all lines on left and lines on the right and created a new line based on both

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][test_images_output/solidYellowLeft.jpg]


### 2. Identify potential shortcomings with your current pipeline


1) One potential shortcoming is that the current algoritem requires the cameras to always be in the same position and the cars all be the same hight
2) Another shortcuming is that it requires all lane lines to straight meaning no curves caused by perspective
3) Another shortcuming is that I have to predefine the region of intereset for the road in advance, but there would some cases for example against a hill or a vally where the road will take a very different area of the captured video
4) another is that only 2 lane lines are captured, it is very likely that when changing lanes for example you would like to know at least 3
5) since the captured information is video, there are some frames where the lane lines move erraticly where some part of of the lane is more visible then before or perspective effects it


### 3. Suggest possible improvements to your pipeline

1) A possible improvement would be applying the haugh transoform to curves and not just straight lines
2) take into consideration pervious frames of the video to adjust better to information as it appears in context
3) remove the need for a region of interest by classifying the location of the road as opposed to the sky
4) using an avarage slope is very primitive and will not work well for more complex curves, should be replaced with a regression or other optimiztion solution
5) remove the hard coded two output lines and implement a clustering like knn to be able to saparate different lines
6) take into consideration perspective and adjust to vehicle speed and surounding vehicles location to allow driving in areas where lighting or road paint is not as good