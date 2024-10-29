![[ml_ops_architecture.png]]

# Data Serving & Data Collection

* APIs

# Model Infrastructure

* Spark
* Docker
* K8s

# Data Pipelines

* Kafka
* MQTT
* Others

# ML Platforms

* Neptune
* MLFlow
* Kubeflow
* Flyte
* Pachyderm

# Deployment Options

* Cloud Streaming - Good for scenarios that require predictions to be available with low latency.
* Cloud Batch - Good for scenarios where we have access to model features before prediction is required.
* Client Deployment - Run all models on the client (SLMs), good for privacy, sensitive data, trained on powerful server and runs on local device
* Hybrid - Federated learning