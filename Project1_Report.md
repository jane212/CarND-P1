# **Project 1: Finding Lane Lines on the Road** 

## 1. Pipeline Description

### 1.1 Image preprocessing

There are 5 basic steps in image preprocessing:

a) converting the color image into gray scale. 

b) using Gaussian kernel with size of 7 to blur the gray image to remove the noise. 

c) using Canny function with specific low and high thresholds to detect the egde.

d) defining region of interest based on the image dimensions, and masking it on the edges.

e) using Hough Transform with parameters (set in the IPYNB file) to find lines among those edges.

After preprocessing, a basic line image could be obtained. 

### 1.2 Finding targets and drawing full lines

#### a. Finding left and right groups

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

#### b. Finding left and right targets

If you'd like to include images to show how the pipeline works, here is how to include an image: 

#### c. Finding left and right drawing positions

d

## 2. Shortcomings with Current Pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


## 3. Possible Improvements

A possible improvement would be to ...

Another potential improvement could be to ...
