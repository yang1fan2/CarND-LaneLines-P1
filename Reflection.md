# **Finding Lane Lines on the Road** 
---

**Finding Lane Lines on the Road**


[gray]: ./test_images_output/gray.jpg "Grayscale"
[canny]: ./test_images_output/canny.jpg "Grayscale"
[canny_region]: ./test_images_output/canny_region.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
- Convert the images to grayscale and apply Gaussian Blur with kerner size 5
![alt text][gray]
- Detect edges via Canny with low threshold 40 and high threshold 150
![alt text][canny]
- Only keep edges within the region of interest
![alt text][region]
- Find lines using Hough Transform
![alt text][/test_images_output/hough_short_wo_filters.jpg?raw=true]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...





### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
