# **Project 1: Finding Lane Lines on the Road** 

By Tingting Huang

## 1. Pipeline Description

### 1.1 Image preprocessing

There are 5 basic steps in image preprocessing:

a) converting the color image into gray scale. 

b) using Gaussian kernel with size of 7 to blur the gray image to remove the noise. 

c) using Canny function with specific low and high thresholds to detect the egde.

d) defining region of interest based on the image dimensions, and masking it on the edges.

e) using Hough Transform with parameters (set in the IPYNB file) to find lines among those edges.

All these steps are packed in 'preprocess' function.

After preprocessing, a basic line image could be obtained. Instead of only returning the line image from previous Hough Transform function, here I also returned the lines object for picking and drawing full lines.

### 1.2 Finding targets and drawing full lines

#### a. Finding left and right groups

To draw a line on left and right, first I need to find left and right groups in lines object after preprocessing. My criteria of defining left or right group is using the slope<0 as in left groups and slope>0 as in right groups. This part of coding is embedded in 'find_target' fuction.

#### b. Finding left and right targets

After finding left and right groups, next is finding target line in each group. Here my logic is using the longest line in each group as the target line. Also, the bottom point of that line should be in the bottom area of the image, which means y1<=bottom_boundary. This rule is used to focus on the bottom part of the image to exclude the distraction from objects or curved lane in distance.

This function is written as 'find_target.'

#### c. Finding left and right drawing positions

When the target lines are determined, I could draw the full lines on the original image within the same region of interest. Because that region is defined early in preprocessing, thus, the top and bottom value for y are also determined (y1=bottom, y2=top). In 'find_xs' function, I only focus on finding x position for full lines. The slope and intercept of the target lines could be calculated, and then the bottom and top x values (x1, x2) could also be found.

The 'find_xs' function will return both x and y values for drawing full lines on the left and right.

## 2. Shortcomings with Current Pipeline

The shortcoming with current pipeline is that it's too sensitive to the region selected. If the region is too small, then the program would not find target lines under my current algorithm. Or if the region is too wide, the curb might be detected.

Another shortcoming is the line I detected could sway sharply, because the longest line may not be always the real target.

## 3. Possible Improvements

Since the camera is mounted at the fixed position, and the car should be driven in the lane, thus, considering the continuity of the lane lines is reasonable. The possible improvement is evaluating the slope and intercept of the lines in each frame and updating those two parameters.
