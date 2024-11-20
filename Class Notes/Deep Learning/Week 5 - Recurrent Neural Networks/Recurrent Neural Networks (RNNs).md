## History

Recurrent Neural Networks tend to feed back into themselves.
### Elman Network vs. Jordan Network

Jordan Network is less powerful than Elman network. Prior input may be forgotten as only outputs can be remembered. Easier to train. Jordan network has a self-loop or cycle.

## Training RNNs

* Unfolding a network over time is a common training method.

![[lesson05_rnns_unfolding.png]]

* There is some similarity to CNNs on unfolded recurrent networks with weight sharing and that each node only looks at the previous.

Plot out your learning curve to see if it's what you're expecting.

![[lesson05_bptt_nn.png]]
## BPTT: Backpropagation Through Time

* How do we train a network like this? Treat it like a normal feedforward network and perform backpropagation.
* How do we deal with reused weights? Each weight matrix w1, w2, w3 shows up everywhere. As many copies as the sequence length.
* BPTT: apply regular backpropagation to the unrolled computation graph.
	* Reused weights: compute gradients separately for each copy and sum the weight changes together to compute the total gradient.

* Extremely small or big weights cause problems. This is called the Vanishing Gradient problem.
* Sensitivity to the inputs decays over time as new inputs overwrite activations of the hidden layer and the network forgets the first inputs.
## TBPTT: Truncated Backpropagation Through Time

* For a long sequence you don't want to unroll all the way to the final time step.
* Instead process one timestep at once, and run BPTT every K1 timesteps.
### Long Short-Term Memory (LSTM)

* Another solution to vanishing gradients
* Will cover this more later on...
## Architecture Choices

* **Regular FF Network:** Input -> Hidden -> Output
* **Generative Network:** Get the input, then generate the entire thing. Can be used backwards as well. Multiple inputs, to a sidechained set of hidden networks, and then a single output.
* **Sequence to Sequence:** Take an input sequence and generate an output sequence in response. Language translation is a good example. 
	* The hidden state is known as a context vector. The network has represented the entire input as this vector.
	* After computing the context vector, the network decodes the context vector into an output sequence.
* **Sequence Classification**: Many-to-one. Predict category of a sequence.
* **Sequence Prediction**: Many-to-many. Generate a new sequence.

## Keras RNNs

* Datasets for RNNs in Keras require an extra sequence index or timestep tensor dimension.
* Data is usually like this:
	* (Batch, Timestep, Feature)
	* If you have different-length sequences you'll need to pad them in the "timestep" dimension.
	* Use keras.preprocessing.sequence.pad_sequences(...)

## Autoregressive Language Models

* Markov assumption (probability * (probability * next probability) etc.)
* ARLMs
	* Need a model to predict the next token given context
		* N-grams
		* Hidden Markov models

## Typical Steps

* Tokenization
	* **One-hot encoding** is one technique to add to this
	* **Lemmatization**
	* **Embeddings**
		* If we have a large vocabulary we need to use embedding.
		* Represent every word in a vocabulary as a high-dimensional floating-point vector
		* All words have the same size representation
		* **Bonus**: similar words can be represented as similar vectors
		* Ex: word = [0,4, 0.2, 0.1]
		* Ex: Sequence = [ word, word2, word 3,...] 
		* Or a matrix.
		* Use Word2Vec
			* CBOW (Continuous Bag of Words): Distance doesn't matter
			* Skip-Gram
* Run a forward pass
* Predict probabilities of next token
	* Use softmax for last layer
	* Logits
* Sample some data
	* Top K
	* "Temperature"
* Detokenization