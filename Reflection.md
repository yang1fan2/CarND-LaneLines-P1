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





### 2. Identify potential shortcomings with your current pipeline


a. If there are noises near the lanes, the lines cannot be detected using Canny algorithm. The same issue will happen in bad weather or during night.
![](/test_images_output/challenge4.jpg?raw=true)

b. All the hyper-parameters (e.g. thresholds) need to update when more complicated driving scenarios are added.

c. When the car is switching lane, the current pipeline will fail.

...

### 3. Suggest possible improvements to your pipeline

a. Using more advanced filters to get rid of noises, or we can leverage deep learning models to detect edges.

b. Hard code different hyper-parameters for different scenarios. For example, one pipeline for sunny day and another pipeline for rainy day.
