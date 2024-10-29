# Softmax

* Generalization of the logistic function.
* All middle layers are used in sigmoid
* Typically applied to the last layer of classificaton problems

## Cross Entropy Loss

**Loss functions:** 
* Gradient Descent error...
* Full Size of error
* Mini Batch
* And now...Cross Entropy
	* Actual distribution of the target versus the prediction.

* Try different learning rates and regularization parameters to determine how fast we want to converge.
* Maximize our GPU memory as much as possible and don't overflow.
![[lesson04_lenet5_optimization.png]]
![[lesson04_SGD.png]]
* GPU cycles need to be sufficiently occupied
* With batch size 32 we are feeding 32 images into the NN at one.

![[lesson04_lenet5_keras.png]]

* 5 is a very interesting size
* Before we flatten we add a 1, 1 layer
* Add two dense hidden layers
	* The first dense layer is experimental, with more numbers leading to more overfitting.
	* The second 10 is intuitive (10 different digits in an image for example)
* Then softmax

## AlexNet

* Convolution then Fully Connected (FC) layers
* ReLU for the first time
* Used 2 GPUs (2xGTX580s)
* Overlapped pooling
* Only 8 layers deep

![[lesson04_alexnet.png]]

## Foundational Models vs. Tuning Models

* Large companies can utilize a lot of their resources to create foundational models
* Tuning models is what a lot of smaller companies are doing
## VGG

## ResNet

### Motivation behind ResNet

Deeper network with more layers had higher training error. Why?
* Vanishing gradients?
* Overfitting?
* Representation Power?

ResNets resemble ensembling shallower networks
Can model recurrent computations
Learning unrolled iterative estimations

## Transfer Learning

* In practice it is very difficult and rare to come up with a novel architecture and train that completely from scratch. This is why only large companies can do it.
	* Data, time, proven architecture, computation power, cost, are all problems
* The idea is to use complex, successfully pre-trained DNN models and transfer the learned weights of the successful model to your problem set. Think Stable Diffusion.
	* How many layers to keep is part of the challenge.
* ![[lesson04_transferlearning.png]]