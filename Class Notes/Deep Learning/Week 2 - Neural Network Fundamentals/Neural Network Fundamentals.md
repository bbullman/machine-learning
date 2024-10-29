# History Continued

* 1980s: AI Hype
	* Backpropagation successes along with Expert Systems made companies and governments excited about AI again (end of AI winter)
	* New AI-specific ocmputing devices appeared such as the LISP machine
		* 1987: The market collapsed again
		* Specialized hardware was replaced by commodity hardware again
		* By the early 1990s a second winter had begun
* Mid-Late 2000s it came back
	* 2009: Deep Learning
# Deep Learning

* Deep Learning is simply neural network learning with backprop, but with many hidden layers.
* One hidden layer is enough to represent (not learn) an approximation of any function to an arbitrary degree of accuracy
* So why deeper?
	* Shallow net may need more (exponential width)
	* Shallow net may overfit more
* GPUs massively accelerated backprop with parallelism
* New software techniques arrived to improve backprop speed
* Cynical answer:
	* Nothing is any different. Computers and GPUs got faster.
	* People trained some deep networks in the 1990s.
* 2015: Google TPUs created
* Nvidia, Nervana, AMD and Microsoft used FPGAs.

### Advances: Pre-Training

* Weight Initialization
	* Idea: train a small network (1 hidden layer first) on a simple problem. Given input x, output the same thing, x.
	* This is known as an **auto-encoder**
	* Trick: make the hidden layer smaller than the input layer
* Auto-Encoders
	* Forced to learn a complete representation of the input x in order to output it on the other side
	* After training, cut off the output.
	* Add a second layer and repeat. A deeper autoencoder to input x and output x, and change the weights calculated earlier to focus on the new weights.
* Backprop
	* Once you've added as many deep layers as you'd like, then you run backprop.

## Activation

![[lesson02_rectified_linear_output.png]]

* Simple: the idea of a "Rectified Linear Unit" or "ReLU"
* The ReLU is simply a neuron with an activation function that is always 0 when z < 0 (think Perceptron) but linear when y=z when z>=0
* **Backprop:** ReLU is smooth everywhere except as z=0, which is smooth enough for backprop to work.
* **Derivative:** G(z) = 0 for z < 0; 1 for z > 0
	* Better than sigmoid because it's faster and less compute-intensive
* **NOTE: Cannot learn with negative inputs!**

## Big Data

* Large advances in big data, distributed systems, and storage systems has helped grow the Deep Learning and ML space
* Too much data can make convergence slower

## GPUs

* OpenCL, CUDA, etc.
* Torch (Lua language) Theano (Python) were two early successful examples that can create a computation graph in memory to represent the desired computation. Computing the gradient (chain rule!) was automatic. Theano would optimize the graph, and then output CUDA code, compile the CUDA, and send it to the GPU.
* TensorFlow, developed by Google, was inspired by Theano and similar libraries.

## Computation Graphs

![[lesson02_computation_graphs.png]]
# Descent 
## Gradient Descent

* Typical training method and extremely simple.
* For every step choose a step size, and how far you are from an ideal state. Small, probably slower gradient. Large, higher gradient.
* In practice it's never that simple.
* Choosing a point, choosing where to go, and figuring out what steps to take to get there.

### Basic Descent Types & Differences

* **Gradient Descent**: Update weights only after each epoch (all examples). All deltas summed into one big update.
* **SGD (Stochastic Gradient Descent):** Update weights after every example.
* **Mini-batches:** SGD with a small batch of examples, somewhere between GD and SGD. Allows massive parallelization of the GPU.

### Descent Learning Rate

* Low learning rate has many diferent steps and high has very few pinging down the descent.
* Usually checking the curve is the best way to go about choosing a good learning rate.

### Other Descent Types & Caveats

* **SGD** is really bad at navigating ravines (IE: where surface curves much more steeply in one dimension than in another). SGD oscillates across the slopes of the ravine only making hesitant progress.
* **Momentum-based strategies**
* **NAG (Nesterov)**
* Adaptive Strategies:
	* **AdaGrad**: adapts learning rate to each parameter
	* **RMSProp** and **AdaDelta**: resolve problems with learning rates getting too small
	* **Adam (Adaptive Moment Estimation)**: similar to above but makes the "ball rolling down the hill of gradient" act like a heavy ball with friction
* Key is to look at the curve for any of these.

# Other Fundamentals
## Regularization

* L1 (lasso) and L2 Regularization
* Reduces complexity of models
* Minimizing error and weight magnitudes

## Dropout

* One of the key strategies to reduce overfitting
* Algorithm is simple: 
	* Randomly turn off outputs for x% of nodes during training. Different outputs turned off for each input for example.
	* When running network, don't turn off outputs and scale down output values to compensate for extra nodes
* Forces multiple "neurons" to take part in the solution for each sample
	* It forces the network to learn a robust and distributed way to solve the problem
	* Think about losing parts of the brain!
* One way is set weight of output to 0 OR one way is also to just have the activation function not send (zero the function)

## Weight Initialization

* Uniform Distribution: [-1, 1]
* Normal Distribution: N(0, 1) (mean 0, std 1)
* Glorot Normal