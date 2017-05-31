
[solidWhiteCurve]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"
[solidYellowCurve]: ./test_images_output/solidYellowCurve.jpg "solidYellowCurve"



# ** Finding Lane Lines on the Road**

The goal of this project is to find the lane markings on the road using basic image processing techniques by connection/averaging/extrapolating 

## Steps of the Project:


* Convert the image into Grayscale.
* Use Gaussian Blur to remove noise.
* Use Canny edge detection.
* Mark the region of interest.
* Apply Hough Transform and get sharp edges.

## Reflection

### Detailed description:
Most of the changes were brought in the `draw_lines()` :

* It was observed that most of the slopes of lines required to mark the lanes fall in the range of `(0.5,1)` and `(-1, -0.5)`. So, only the lines falling in that range were only considered.
* As for the Left Lane Line the slope of the line would be positive and negative for the Right Lane Line.
* This was used in order to find the dominant line for the left lane and the right lane by averaging the points.
* After this the two lines are averaged over 20 frames so that the lines are not jittery.
* And then the lines are extrapolated for uniformity.

### Sample Images

Here are some sample images, please check the folders `test_images_output` and `test_video_output` for more:

![alt text][solidWhiteCurve]
![alt text][solidYellowCurve]

## Potential Shortcomings:
* There is a assumption that we have to make that the divider lines are white/yellow and the road is always black. But as shown in the challange video when the road color changes form black to white the algorithm fails to identify the lane markings.
* This pipeline will also not work in changing light conditions for example, under the street light or in pitch darkness.

## Possible improvements to the pipeline:

* If a white and yellow filters are also use along with grascale then we can improve the accuracy of detection.
* Alternate color spaces may also help to know more about the given image.
* We can also find out the pattern in change in gradient in the edges of the lane lines which may lead to better lane recognition. 