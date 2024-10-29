### Early Years

* **McCollough-Pitts (MCP) neurons**
	* 1943 Paper: A logical calculus of the ideas immanent in nervous activity explained how simple neural building blocks could compute functions in a Turing sense
	* MCP model:
		* Models eventually send a 0 or a 1
		* Weighted inputs to a neuron are added together to provide an output based on a threshold (0 or 1)
		* **Problem:** The weights for the model needed to be input manually and it's also an incredibly simple model that can't learn on its own
* **Hebbian Learning**
	* Neuroscience-based attempt at learning neural connection weights automatically
	* Involves back-propagation
	* "When two neurons send an activation spike together, increase the strength of the connection between them."
	* Learn more gradually by applying a function/weight
	* **Problem**: weights end up growing without any bounds and so it becomes unstable
		* Hebbian variants work for unsupervised learning. Extra modifications are needed to train for supervised manner to learn desired input/output pairs.
* **Perceptron**
	* Rosenblatt (1958) described the model that could learn weights itself based on training.
	* Initialize weights to 0 or a small value
	* For each training dataset with target value, calculate the output, update the weight
	* Repeated until we reach a desired error rate or until we hit a specified max # of errors
	* **Problem**: Is unable to create a plane to separate the dataset and because of that, it cannot represent XOR
	* The limitations of single perceptrons burst the bubble of AI excitement and caused the first "AI Winter"
* **"Hidden Layer" Perceptrons**
	* Trained multi-layer perceptron with weights shown on connections to say if you can "fire" or not
	* Adding more layers of hidden nodes = fundamentally the core of neural networks
	* Only need 4 training samples for XOR

-----
## Step Functions

* Weren't always good with formulas for outputs
* Sigmoid functions were much easier
	* Sigmoid derivative
* One of the fundamentals about deep learning is that there is a large amount of training data and there is a lot of performance overhead
## Backpropagation

* Backpropagation is  about attributing the proportion of the error/loss that each weight contributes to the output. The more error a weight contributes to the output, the larger its adjustment during backpropagation to minimize the overall error.
* Compute dE/du
* 4 terms are multiplied together and then a couple of subtractions
* Minimize the errors we make over time
	* Obviously there's issues like overfitting/underfitting, lack of data, optimization
* **Generalized Algorithm:**
	* Set a learning rate: n
	* Compute all terms: the derivatives of the loss with respect to each weight in the network
	* For all weights w (w stands for both w and u) wNew = wOld - n ( dE / ... )

![[deeplearning_lesson1_backprop.png]]

* Come back to this methodology often!
* Pitfalls of new MLEs:
	* Looking at the output without looking at the intermediary steps
* 