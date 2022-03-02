Installing MLRun package and sklearn, this may take a few minutes!: `> pip install mlrun[api] scikit-learn`

This part of the tutorial will walk you through the steps to create, test, and deploy serving pipelines. 

**MLRun Serving Pipelines** allow you to easily build serverless pipelines using Nuclio (a real-time serverless engine), and deploy them anywhere.
[Nuclio](https://nuclio.io/) is a high-performance open-source serverless framework that is focused on data, I/O, and compute-intensive workloads.

The real-time pipelines can handle events and data processing across structured and unstructured (text, images, video) data, 
model serving, ensembles, and various built-in or custom activities.
Simple model serving classes can be written in Python or be taken from a set of pre-developed ML/DL classes.
Serving pipelines are tightly integrated with the [MLRun Feature Store](https://docs.mlrun.org/en/stable/feature-store/feature-store.html) 
for real-time feature enrichment and processing.

MLRun Serving supports the full application life cycle.
This includes auto-generation of microservices, APIs, auto-scaling, model logging and monitoring, and configuration management.
For more details and examples, see the [MLRun Serving Graphs](https://docs.mlrun.org/en/stable/serving/serving-graph.html) 
and [Model Monitoring](https://docs.mlrun.org/en/stable/model_monitoring/index.html) documentation.

The tutorial consists of the following steps:

1. Setup and configuration
2. Write and test a simple serving class
3. Deploy the model serving function (to Nuclio)
4. Use the live model serving function (via UI or API)
