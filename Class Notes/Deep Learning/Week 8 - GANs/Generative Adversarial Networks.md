## General Notes

### Related Mathematical Subjects:
* Calculus
* Linear algebra
* Probability
* Statistics
* Information Theory
### Will Touch:
* Game Theory
### Some Ideas and Questions?

* Can we easily distinguish AI generated content?
* Can we start from rules, instead of training samples?
* Can AI learn strategies?
### Reap of Information Theory

* Entropy
* Conditional Entropy
* Cross Entropy
* Mutual Information

## Introduction to GANs

* Generative - Learning a generative model
* Adversarial - Trained in an Adversarial setting
* Networks - Using Deep Neural Networks

Generator and Discriminator are two models that try to train against one another in an adversarial setting. GANs are easy to attack with FGSM (Fast Gradient Sign Method).

Adversarial Training is important because it allows us to build up our defense to noise and FGSM attacks. Adversarial training provides regularization and semi-supervised learning. A lot of GANs are trained to avoid tons of fake content.

Possible futures for Reinforcement Learning such as robots. Useful for generating examples of images, photographs, cartoon characters, image-to-image translation, text-to-image translation, semantic-image-to-video or image-to-photo translation, generate new poses, labels to street scenes, aerial to map view, inputs-groundtruths-outputs, etc.

![[lesson08_taxonomy_of_gans.png]]
**Discriminator** outputs values between 0 and 1
**Discriminator** tries to maximize a value function V that depends on D and G
**Generator** is trying to minimize a value function V that depends on D and G
![[lesson08_gans.png]]

In practice the generator loss does not do so well. Instead of minimizing the log(1-D(G(Z))), minimize logD(G(z))This is an acyclic training process.

1. First step is train the discriminator
	1. Two types of inputs:
		1. Real Samples
		2. Generated Samples
2. Second step is train the generator
![[lesson08_gan_discriminator_training.png]]![[lesson08_gan_generator_training.png]]

* Lock the Discriminator, and backpropr error to update the discriminator.
* Lock the Discriminator, calculate the gradient for the generator weights and update the Generator.
* Algorithm: Minibatch stochastic gradient descent training of generative adversarial nets. The number of steps to apply to the discriminator k is a hyperparameter.
* ![[lesson08_training_gans.png]]

In practice the G's cost function is not the opposite of D's.
* G maximizes logD(G(z)) instead
* For each update of G, do k updates of D
	* Retracted statement in 2016
* D is usually deeper and sometimes has more filters per layer than G
* Mode collapse: G maps a lot of z values to single x where D is failing, this is still an open problem and why G is shallow most likely

## Deep Convolutional GANs

You can make GANs pretty deep. Usually factors of 4 or 2.

### Problems of GANs

* May not converge properly
	* GANs have two or more players
	* Generator to minimize discriminators' reward
* 
* Problems with counting and perspective

## Other GAN Types

Types of Generative models:
* Boltzmann Machine
* Deep belief Networks
* Variational autoencoders
GANS
* Sampling (generation) is straightforward
* Training without maximum likelihood
* Robust to overfitting
* In practice, GANs capture model distribution

