# Udacity Self-Driving Car Nanodegree - Finding Lane Lines on the Road

This repo contains the code written to complete the first project on Udacity Self-Driving Car Nanodegree. This project consists of algorithms to identify lane lines on the road on a video. The video is taken from a camera at the center of a vehicle.

# Prerequisites

To run this project, you need [Miniconda](https://conda.io/miniconda.html) installed(please visit [this link](https://conda.io/docs/install/quick.html) for quick installation instructions.)

# Installation
To create an environment for this project use the following command:

```
conda env create -f environment.yml
```

After the environment is created, it needs to be activated with the command:

```
source activate carnd-term1
```
and open the project's notebook [P1.ipynb](P1.ipynb) inside jupyter notebook:

```
jupyter notebook P1.ipynb
```

# Overview

The repo contains the jupyter notebook [P1.ipynb](P1.ipynb) where the processing pipeline is implemented.
The pipeline consists on six steps represented by six different functions:

- **grayAction**: Returns a gray scaled version of the input image using **cv2.cvtColor** method.
- **blurAction**: Applies a Gaussian blur to the provided image using **cv2.GaussianBlur** method.
- **cannyAction**: Use a [Canny transformation](https://en.wikipedia.org/wiki/Canny_edge_detector) to find edges on the image using **cv2.Canny** method.
- **maskAction**: Eliminate parts of the image that are not interesting in regards to the line detection (for now...).
- **houghAction**: Use a [Hough transformation](https://en.wikipedia.org/wiki/Hough_transform) to find the lines on the masked image using **cv2.cv2.HoughLinesP**. It also adjust a line to the set of lines returned by the Hough transformation in order to have a clearer-two-lines representation of the road lines using **np.polyfit** method.
- **weighted_img**: Merges the output of **houghAction** with the original image to represent the lines on it.

First, the pipeline is tested agains the images contained at [test_images](test_images). The output of each step is saved in a directory:

- [test_images_gray](test_images_gray)
- [test_images_blur](test_images_blur)
- [test_images_canny](test_images_canny)
- [test_images_region](test_images_region)
- [test_images_hough](test_images_hough)
- [test_images_merged](test_images_merged)

After that test, the pipeline is consolidated on a single function **process_image** to apply it on a video frame. The sample videos could be found [here](test_videos).
The video after the transformation are saved on the [test_videos_output][test_videos_output] directory.

An html version of the output is [here](P1.html).

# License
This project copyright is under [MIT](LICENSE) License.
