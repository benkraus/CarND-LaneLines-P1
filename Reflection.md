# Finding Lane Lines on the Road
### The Pipeline

The pipeline consists of the following process:
* Convert the image to grayscale
* Perform a gaussian blur
* Run the Canny edge detection algorithm
* Apply a region of interest - I made a polygon from the bottom two corners of the image up to a slightly adjusted center of the image
* Run a Hough transform

After running the pipeline, I then iterated through the lines that the pipeline found, and based off the slope of the line, added them into right and left line arrays. I gave the longer lines higher weights and then extrapolated them so that the lane lines would always be bound to the bottom of the image.

### Shortcomings

A big shortcoming of the current approach is that the algorithm fails to work on the challenge video. It loses the lane lines when hitting the shade. Something is also slightly off - the lane detection isn’t as smooth as it could be.

### Possible Improvements

After investigating possible improvements, one thing that has popped up is that at the start of the pipeline you can first convert the image to the HLS color space and use a mask to pick out white and yellow colors. I may continue to explore this avenue some more in hopes of making the challenge video work, but for now this is where it is at. 

Another thing I realized is that the Hough transform is good for lines, but not so for curves. Not all roads are straight like those found in these videos. Another approach would need to be taken in the end to detect and draw curved lines.