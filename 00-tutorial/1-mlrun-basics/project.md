Installing MLRun package and sklearn (using: `pip install mlrun[api] sklearn plotly`), this may take a few minutes !

We will start by reviewing the MLRun project and function objects:

**MLRun project**

[MLRun **Project**](https://docs.mlrun.org/en/latest/projects/overview.html) is a container for all your work on a particular activity/application. Projects hosts `functions`, `workflow`, 
`artifacts`, `secrets`, and more. Projects have access control and can be accessed by one or more people, they are usually assosiated with a GIT repo.
See MLRun [Projects documentation](https://docs.mlrun.org/en/latest/projects/overview.html).

The project root contains an optional project specification file, you can create it manually
(see the `project.yaml`{{open}} file), or preferably use MLRun SDK for generating it. 

Example: Defining a project with two functions using the SDK:
```python
project = mlrun.new_project("coda", "./", user_project=True)
project.set_function("gen_iris.py", "gen-iris", image="mlrun/mlrun")
project.set_function("trainer.py", "gen-iris", 
                     handler="train", image="mlrun/mlrun")
project.export()
```

**MLRun Functions**

[MLRun Serverless **Function**](https://docs.mlrun.org/en/latest/runtimes/functions.html) can be defined in the project spec 
(for simplicity), or in a separate function object/file (for full control).
The basic function attributes include the source code, base `image`, extra package `requierments`, runtime engine `kind`,  
and desired resources (cpu, gpu, mem, storage, ..). The runtime engines (local, job, nuclio, spark, ..) accept runtime specific attributes, and automatically 
transform the function code and spec into fully managed and elastic services that run over Kubernetes.

MLRun supports batch functions (for data processing, training, etc.) or real-time functions (for serving, APIs, and stream processing), 
and provide an extensive [Function Marketplace](https://www.mlrun.org/marketplace/functions/).

Function source code can come from a single file (.py, .ipynb, ..) or a full archive (git, zip, tar), 
MLRun can execute an entire file/notebook (see `gen_iris.py`{{open}}) or specific function classes/handlers (see `trainer.py`{{open}}).

Functions are executed (using the `run` command) with optional `handler`, various `params`, `inputs` and resource requirements, this will generate a `run` object 
which can be tracked through the CLI, UI, and SDK. Multiple Functions can be executed and tracked as part of a multi-stage Pipeline (workflow). 
