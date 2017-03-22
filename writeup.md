# Finding Lane Lines on the Road

The goals/steps of this project are the following:

- Make a pipeline that finds lane lines on the road.
- Reflect on your work in a written report.

# Reflections

## Description
The pipeline consists on six steps represented by six different functions:

- **grayAction**: Returns a gray scaled version of the input image using **cv2.cvtColor** method.
- **blurAction**: Applies a Gaussian blur to the provided image using **cv2.GaussianBlur** method.
- **cannyAction**: Use a [Canny transformation](https://en.wikipedia.org/wiki/Canny_edge_detector) to find edges on the image using **cv2.Canny** method.
- **maskAction**: Eliminate parts of the image that are not interesting in regards to the line detection (for now...).
- **houghAction**: Use a [Hough transformation](https://en.wikipedia.org/wiki/Hough_transform) to find the lines on the masked image using **cv2.cv2.HoughLinesP**. It also adjust a line to the set of lines returned by the Hough transformation in order to have a clearer-two-lines representation of the road lines using **np.polyfit** method.
- **weighted_img**: Merges the output of **houghAction** with the original image to represent the lines on it.

The output of each step is saved in a directory:

- [test_images_gray](test_images_gray)
- [test_images_blur](test_images_blur)
- [test_images_canny](test_images_canny)
- [test_images_region](test_images_region)
- [test_images_hough](test_images_hough)
- [test_images_merged](test_images_merged)

To average and interpolate the lines on the **draw_lines** function, I try to find the lines going on the left and right side of the image. Each point of those sides were accumulated and first degree polynomial was fit to those points using **numpy.polyfit**. When the line equation was found, it was evaluated on the region of interest to define the points where the line would be shown on the image.

## Potential shortcomings/suggestions

- The lines shake a lot on the videos, a better way to average them should be possible.
- The line size should be improved.
- Bright points outside the lines were taking into account.
