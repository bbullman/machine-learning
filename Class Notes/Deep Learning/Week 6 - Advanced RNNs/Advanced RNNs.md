## Generative Character RNN

* Start with a "Seed" character in a string
* Generate an output vector
* Sample from output vector
	* Use softmax to convert the outputs into probability vectors assuming they were trained with the appropriate loss
	* Now roll a die weighted with the output softmax vector to choose the output character
	* Feed this in as a character and repeat the process!
* Advanced RNNs can be used for a large variety of tasks:
	* Writing
	* Making formatted entries (Markdown, HTML)
	* Formatted journals and figures
	* Code
	* Handwriting generation
	* Can be used for song generation

## Bidirectional RNN

* Bidrectional RNNs can go from Input->Forward or Input->Backward or from Forward->Output
* Useful for adding onto LSTMs and GRU layers
* Can be extended to higher layers
* Use the Keras bidrectional wrapper, can override go_backwards and write your own

## LSTM

* Tries to solve vanishing gradients
* Maintains state from timestep to timestep
* tanh is a good activation function to use as it squashes between (-1 and 1)
* LSTM cell == LSTM layer
	* Cell and layer are the same and cover a lot of stuff
	* The contents are basically 4 layers of neurons connected in a specific way
	* Different diagrams use vastly different conventions
		* In practice just create a single layer with N neurons and let the problem abstract itself
* Maintain **State** in a Cell
	* The network determines what state to maintain
	* States are maintained via gating functions where you can control how much is input, output, and "forgotten"
* Use Tanh activation to add new layer value to add to the cell state
* Use Sigmoid on the input layer
* Multiply the tanh vector by the input vector and add it to the forget layer mulitplied by the original layer
* Use Sigmoid for output
* The state vector Ct is squshed and passed to an ext layer as Ht
* Common addition to LSTMs are Peephole Connections
## GRU

* Simplification of LSTM
* Single update gate controls the forgetting factor and the state-update function
* New reset gate is added
* Only one hidden state
* Faster training than LSTM

### Additional Information

* Initializing the bias of LSTM forget gate to 1 makes LSTM almost as strong as all other options
* Dropout helps LSTM and GRU
* Forget gate is crucial
* Most variants perform similarly
* RNNs are more difficult to train in general

## Helping RNNs Learn

## Gradient Clipping

* If there are steep cliff-like occurences in the loss function, the gradient can become too large
* "Clip" the gradient, as you move define a maximum that you can move
* For some RNNs this is required to train properly

## Recurrent Dropout

* Normally dropout happens with regularization (increased generalization ability)
* However dropout before an RNN layer harms learning
* Different dropout schemes are required for RNNs
	* Use the same dropout Mask
	* Also apply a time-invariant dropout mask in the recurrent connections
* Keras already does this
	* Use dropout in the layer input to the recurrent layer in the attributes of the layer
	* Use recurrent_dropout argument to specify the temporarily constant dropout for recurrent connection
	* Mask is still randomized between layers but not timesteps
## Teacher Forcing

* After the first timestep feed forward the ideal output to the recurrent layer
* Useful for Hidden-Hidden and Output-Input connections
* Use a mixed strategy "Curriculum" learning to eventually ease into using the models own outputs

## Attention Networks

* Attenton networks are used to pay attention to what parts of the input are relevant
* Google Translation network

## Deep RNNs

* RNNs can be multiple layers deep
* Multiple vectors of hidden state passed from timestep to timestep
* The output of the bottom RNN is sent to the next layer
* Keras: return_sequences=True
* Top layer can be whatever your model is modeled after

## Recursive Neural Networks

* Used for text processing and music analysis

## Networks with Memory

* Adding actual memory to a Neural Network
* NTMs
* Differentiable Neural Computer
	* Extension of NTMs -- RNN with associative memory
* Lots of new research in this area
* 