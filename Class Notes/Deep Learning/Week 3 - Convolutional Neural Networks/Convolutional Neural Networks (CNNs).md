# Examples in Computer Vision

* Image classification
* Object detection: Localization and Classification
* Image Captioning
* Image Segmentation
	* Image contours
* Pose Estimation
* Image Retrieval
* Dense Captioning
* Visual Question Answering
## Challenges for Computer Visions:

* Background clutter in the image.
* Deformation
	* Things look different from different angles
	* Things can change position and this changes the 2-dimensional representations 
* Intraclass variation
	* If it can tell that a kitten is in an image, how does it distinguish between the different kittens in a multi-kitten picture, all in different positions?
* Illumination
	* Lighting
* Occlusion
	* Missing/hidden parts of the image.
## The Problem for Computer Vision

* Semantical Gap between what humans see and what computers see. Computers see a big grid of numbers between [0, 255] (resolution and 3x RGB)
* If the camera point moves, then the entire image moves!
# Why didn't Deep Learning work in the past?

* Too many parameters (Computational improvements helped)
* Overfitting (Common problem)
* Not enough data (Big data helped)
* Lack of computational power and parallelized architectures

# CNN Toolbox

CNNs solve the exploding parameters problem by using:
* Local receptive fields
* Weight Sharing
* Pooling
	
![[lesson03_cnn_tools.png]]

These three techniques will adjust and lower the number of parameters that are necessary to train.

## Local Receptive Field

![[lesson03_lrf_spare_connectivity.png]]
## Parameter Sharing

![[lesson03_parametersharing.png]]

## Pooling

![[lesson03_pooling.png]]

Similar to downsampling. You can apply low-pass filters before scaling down the image size.

### Toolbox Continued

* CNNs solve the viewpoint by weight sharing
* Other approaches:
	* Redundant Invariant features
	* Put a box around the object and use normalized pixels
	* Use a hierarchy of parts that have explicit poses relative to the camera
* CNNs try to mimic visual cortex
	* Hierarchical representations from lines parts to objects
	* Learn a filter bank
	* Combine filter banks to build parts and parts to build objects
* Continuous and Discrete Convolution extend to higher dimensions
* Fast calculation of convolution
	* g is the kernel in the function
* **LCR**:
	* Flip values and then do sliding window to do edge detection
	* Valid and same padding techniques are used
	* Valid padding can use strides instead of shifting windows to the left by 1
	* Make sure to flip and do the sliding window merge!
* **Pooling**:
	* Reduce the number of parameters in the network
	* Gain some translation invariance