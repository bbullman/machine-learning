
Probabilistic Model for Autoencoders
* Inference
* Generation
* Joint Distribution
* Maximize Marginal Likelihood (intractable)

* Bayes Rule
	* Posterior
	* Prior
	* 

## Amortized Variational Inference

* Approximate the posterior 
* Kullback-Leibler divergence
* Minimize the distance between q and p


VAE

* Autoencoder + Variational Inference
* We take a regular autoencoder to start
* Seems to take a point and build a radius around it, then map the datapoints to that based on a generalized distance, then propagate back errors.
* Apply Gaussian Noise

## Encoder

* Encoding itself and adding the noise/sampling process.
* Encoding layer in the middle has a special form
* Looks like a normal layer of neurons with a layer size of 2M but we assign a special meaning to these neurons
* Half of the neurons (M) are designated as the means of a Gaussian Normal
* The other half are designated as the standard deviations of the Gaussian
* The encoder is a vector of length 2M
* We don't normally just connect these neurons to the next layer
	* Instead the encoding is a multidimensional gaussian dimension so this actually represents a probability distribution and not a value
	* This is called a probability distribution
		* Q(Z/x)
	* Note that the distribution depends on the input **x** because it is encoding **x**
* We may also call the encoding space **latent space**
* For easy visualization we can think of 4 neurons in the latent space, 2 will be the means and 2 will be the variance (standard deviations)
* For visualizing higher dimensionals, you simply use PCA to reduce to 2-dimensions

## VAE Cont'd

* Is it okay to assume the neuron activations are okay to use as the means?
* We need to ensure the **standard distributions are positive**
* Use an activation such as ReLU or Softplus for the standard deviation nodes
	* Softplus is like a smooth ReLU
	* np.loglp(np.exp(x)) for better numeric stability on log(1+e^x)

## Decoder

* To start decoding, a random sampling takes place
* The decoder originally takes a sample z from the Gaussian distribution represented by the encoding layer
* Now it connects with the sampled vector z as usual to additional layers that expand it out into the original vector size (recall that the goal is to reconstruct the input)

## Training Process

* Sampling process is difficult
* Mapping the distribution is not tractable, we don't have to max it thanks to Bayes Rule
* We train the VAE by:
	* Random Sampling
	* Loss function boundaries
* Backpropagation through Random Operations
	* VAE uses random sample z as a part of the model
	* Solution: Use the reparamaterization trick 
* We can calculate the gradient by using the backpropagaiton
* But for loss we can't use MSE
	* Need to add terms to make the encoding layer behave like a Gaussian layer
	* Need to handle the output like a distribution

### ELBO Loss

* Loss function for VAEs
* Evidence Lower Bound (ELBO)
* Want to maximize ELBO; minimize -ELBO
* Loss Function is the expected log-likelihood
* Term 1 - Minimizing the Likelihood itself
	* Output looks like Input
* KL Divergence
	* KL divergence let's us compare two probability distributions
	* if p and q are identical Dkl = 0, otherwise it's > 0
	* This encourages q(z|x) to look like N(0,1) and this is how we make the network learn to encode the input into a normal distribution
## Variations on VAEs

### Conditional VAEs

* Tell the VAE each class of input
* IE: Use a one-hot encoding vector C for each class
* Concatenate with the input so x +o C
* Also concatenate with the input to the decoder z: z+o C
* Train the network as usual
* Generate samples of output, concatenate with the desired output:
	* Create a Cat-like Dog
	* Create a Dog-like Cat
## Summary on VAEs

* Easy to visualize the output as we have samples from different parts of the encoding space
* Generated sample images are often blurry
* Active research area
* Recent work is involving VAEs combined with GANs (Generative Adversarial Networks)
