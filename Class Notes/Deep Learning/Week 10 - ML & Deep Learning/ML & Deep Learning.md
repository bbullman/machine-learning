Model building, deployment, best practices and considerations.

## Model Building Process

1. Define the objective and quantify the metrics
	1. Might with constraints
	2. Does it require domain knowledge?
2. Collect and understand data
	1. Deal with vagaries and biases
	2. Missing data, outliers
3. Frame the problem into machine learning
	1. Classification, regression, ranking, generation, diffusion, etc.
	2. Needs domain knowledge
4. Feature Construction
	1. Transform raw data into modeling dataset
	2. Needs domain knowledge
	3. Needs to be consistent with the metric quantified in objective
	4. Train, test, and evaluate
		1. Train/Test Split
		2. Feature Selection / Model Scoring
		3. Model Training -> Model Scoring
		4. Evaluate the model ![[lesson10_iterate_model.png]]
## Model Deployment

1. Model versioning
2. Model rollback
3. Model updates
4. SLA guarantees
5. Choices (examples):
	1. Tensorflow serving
	2. TorchServe
	3. Triton Server
	4. RayServe
6. Flask Server API (FOSS web microserver)![[lesson10_flaskserver_api.png]]
7. Tensorflow Serving (Google)![[lesson10_tensorflowserving1.png]]![[lesson10_tensorflowserving2.png]]
8. Triton Server (Nvidia) ![[lesson10_tritonserver.png]]
9. Ray Serve (Python-based) ![[lesson10_rayserve.png]]

## Model Payloads

* "Model as Data"
	* Native server typically
	* Blob model
	* Pros: Simple, flexible, scalable, portable
* "Model as Code"
	* Typically python server
	* Pros: transparency, tied to frameworks, customization, iteration speed

# Rules of ML

1. Phase 1 : First Pipeline
2. Feature Engineering
3. Refinement & Complex Models

High Train Error?
* Inspect data for defects
* Inspect software for bugs
* Tune learning rate (and other hyperparams)
* Make model bigger

## Debugging

* Use TensorBoard
	* Visualize your graphs
	* Plot metrics
	* Show additional data

## Hardware Accelerators

* CPUs
	* General purpose processors with fewer, powerful cores
	* Smaller, faster caches
	* High power consumption per core
* GPUs
* DSPs (Digital Signal Processors)
	* Useful for speech recognition and image processing
* FPGAs (Field-Programmable Gate Arrays)
* ASICs (Application specific) (TPUs and GPUs)
* NPUs (Neural Processsing Units)


## Distributed ML Computing

## Model Parallelism

* One model, several chunks
* Can process very large models
* Split into different compute subgraphs
* Subgraphs are distributed into different accelerators
* The same full training data is being processed

In model parallelism, you want to separate the layers by GPU(s). There is a link between GPUs.

* Model partitioning - Each worker node is responsible for training specific parts
* Data sharing - same dataset is shared across all worker nodes but this is difficult
* Communication overhead - exchange intermediate results between worker nodes


## Data Parallelism

* Can process large amounts of data split into mini-batches
* Different batch is processed on different accelerators
* Each accelerator will have a whole model replica
* Model replicaiton - model is replicated on multiple workers
* Data partitioning - the dataset is divided into smaller subsets and each worker trains the model on its subset
* Parameter synchronization - after each training iteration, the model parameters are synchronized across all workers

## Hybrid Parallelism

* Combination of data and model parallelism - combines the benefits of both data and model parallelism
* Complex Implementation - Requires careful coordination between data and model partitioning
* Suitable for large models and can be used to train massive models that cannot fit on a single device(s)


## Synchronization

How do models with more workers share and synchronize information?
* Parameter server
* All-reduce

## Parameter Server

* Centralized parameter store - centralized model parameter base
* Worker nodes fetch parameters from the server and compute gradients and push back to the server
* Scalability - can scale to large clusters but can become a bottleneck with more workers

## All-Reduce

* Peer-to-Peer communication - worker nodes communicate directly with each other to exchange gradients and model parameters
* Scalability - can scale to large clusters efficiently
* Complex communication pattern requires careful optimizations of communication protocols

## Challenges in Distributed ML

* Data distribution and partitioning strategy
* Fault tolerance and checkpointing
* Consistency, synchronization
* Communication overhead
* Heterogeneity
* AI is getting huge, so inference usage scale, cost, latency...

## Pruning

* Goal: Reduce number of parameters with minimum quality loss
* What to prune?
	* Synapses: turn dense matrix into sparse matrix; packing and padding operations. 
	* Neurons
* Remove less important parameters
	* Can use L1 norm
	* Single element
	* Block-based (e.g. row)
* Knowledge Distillation
	* Have a student-teacher framework
	* Match prediction between students and teacher

## Quantization

Trained models can be fp16 or bf16, less bit-width means less energy used in compute, faster computation, and less memory required.

Unsigned integer, signed integer, fixed point (integer + fraction), and floating point options (sign bit, 8 bit exponent, 23-bit fraction).

* K-means quantization for compression is quite good.
* Linear quantization (Affine transform) is good too.

## Federated Learning

* Basic Idea for centralized-federated learning:
	* We only need statistics
	* Forward pass: collect statistics locally, **only forward aggregated data**
	* Backward pass:
		* Server: calculate gradient and weight updates
		* Client: update weights after server does the calculation
* Gossiping protocol can be used for totally decentralized federated learning
* Learning Procedures
	* Initialization: edge nodes activated
	* Client selection: different criteria (battery, network, amount of data, etc.)
	* Configuration: edge aggregation
	* Reporting: server aggregation
	* Updating: edge updating weights