# **Finding Lane Lines on the Road** 


[gray]: ./test_images_output/gray.jpg "Grayscale"
[canny]: ./test_images_output/canny.jpg "Grayscale"
[canny_region]: ./test_images_output/canny_region.jpg "Grayscale"

---
### Files
- P1.ipynb: the code for finding lanes.
- test_videos_output: generated videos with annotated lanes.


### The pipeline

There are 6 steps. 
- Convert the images to grayscale and apply Gaussian Blur with kerner size 5.
![alt text][gray]
- Detect edges via Canny with low threshold 40 and high threshold 150.
![alt text][canny]
- Only keep edges within the region of interest.
![alt text][canny_region]
- Find lines using Hough transform from canny edges.
![](/test_images_output/hough_short_wo_filters.jpg?raw=true)
- Remove invalid lines using slope (More details explained below).
![](/test_images_output/hough_short.jpg?raw=true)
- Average the position of each of the lines and extrapolate to the top and bottom of the lane.
![](/test_images_output/hough_long.jpg?raw=true)


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding the following stuff
- Only keep lines whose absolute slopes are bigger than 0.3 and lower then 0.3
- If the line is left lane and its slope is positive, remove this line.
- If the line is right lane and its slope is negative, remote this line.
- For all valid lines, calcuate the averaged slope and y intercept.
- Calculate the bottom and top points giving averaged slope and y intercept.
