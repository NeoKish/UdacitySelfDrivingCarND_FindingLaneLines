# **Finding Lane Lines on the Road** 


Reflection:

My pipeline consists of 8 steps. First we read the image and convert it into gray scale.Before identifying the edges, I have used gaussian blur to smoothen the image and remove noise.After Gaussian Blur, I used canny edge algorithm to identify the edges.This gives edges in the whole image. To remove the region which are not important like trees and surroundings, a polygon image mask was applied on the edged image to filter out the road lanes section of the image. With the filtered out image , a probablistic hough line transform is used to identify the lane lines (this gives us extreme x and y points of the line segments) and then lines are drawn over the image where lane lines are present. For drawing the lines that are consistent over a set of images or in a video, I had to separate out the left and right lane lines identifed by hough transform algorithm by using x-coordinates of the image and then finding the slope for the left line segments and right lines segments. Slope average was found out and then unknown x values were extrapolated using the slope formula. One the all the x and y points were found out, single lines for left and right lanes starting from bottom to the top of masked image.

The shortcoming of the pipeline is that in the SolidYellowleft video, it mistakes the car at the beginning of the video as edge which causes the slope to change but once it goes ahead the lane detection works fine throughout the video unless there is a horizontal white line passing on either lane which cause the line drawn to deflect from the lane line but both left and right lane lines are maintained annotated throughout most of the video.

The possible improvements could be to improve the draw lane lines algorithm by checking for outliers in the line that are a way off and removing them while averaging the slope. 



