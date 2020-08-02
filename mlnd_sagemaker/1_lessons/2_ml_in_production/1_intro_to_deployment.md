# 1. Introduction to deployment

## ML workflow
![ML WorkFlow](img/ml_workflow.jpg)
Major steps in ML workflow are:
1. Explore and process dara
2. Modeling
3. Deployment
Each major cloud provide have their own ML workflow defined.
1. Amazon Web Services (AWS) discusses their definition of the [Machine Learning Workflow](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-mlconcepts.html).

2. Google Cloud Platform (GCP) discusses their definition of the [Machine Learning Workflow](https://cloud.google.com/ai-platform/docs/ml-solutions-overview).

3. Microsoft Azure (Azure) discusses their definition of the [Machine Learning Workflow](https://docs.microsoft.com/en-us/azure/machine-learning/overview-what-is-azure-ml).

## What is cloud computing and why we use it 

**Cloud computing** can simply be thought of as transforming an Information Technology (IT) product into a service.Generally, think of **cloud computing** as using an internet connected device to log into a cloud computing service to access an *IT resource*. These IT resources are stored in the cloud provider’s data center.
Most of the factors related to choosing cloud computing services, instead of developing on-premise IT resources are related to time and cost. The capacity utilization graph below shows how cloud computing compares to traditional infrastructure (on-premise IT resources) in meeting customer demand. 
![Capacity utilization](img/capacityutilizationcurve3.png)
Looking at the graph, notice that traditional infrastructure doesn't scale when there are spikes in demand, and also leaves excess when preparing for future demand. This ability to easily meet unstable, fluctuating customer demand illustrates many of the benefits of cloud computing.
### Risks of using loud computing

1. Potential) Increase in Security Vulnerabilities
2. Reduced Operational Governance Control (over cloud resources)
3. Limited Portability Between Cloud Providers
4. Multi-regional Compliance and Legal Issues

### Benefits
1. Proportional cost
2. Increased Availability
3. Increased Realiability

**Deployment** is typically critical part of the machine learning *in the workplace* which is not the case *with academic or personal usage* therefore it is *sometimes* included in as part of ML workflow.

## Deployment to production

`Deployment to production` can simply be thought of as a method that integrates a machine learning model into an existing production environment so that the model can be used to make decisions or predictions based upon data input into the model. 

There are `three primary methods` used to transfer a model from the modeling component to the deployment component of the machine learning workflow. Following are listed in order of least to most commonly used. The third method that's most similar to what’s used for *deployment within Amazon’s SageMaker.*
Paths to Deployment:
1. Python model is recoded into the programming language(like Java,C+ etc) of the production environment.
	This method is rarely used anymore because it takes time to recode, test, and validate the model that provides the same predictions as the original.
2. Model is coded in *Predictive Model Markup Language* (PMML) or *Portable Format Analytics* (PFA).
	The Data Mining Group developed both `PMML` and `PFA` to provide vendor-neutral executable model specifications for certain predictive models used by data mining and machine learning. Certain analytic software allows for the *direct import of PMML* including but not limited to IBM SPSS, R, SAS Base & Enterprise Miner, Apache Spark, Teradata Warehouse Miner, and TIBCO Spotfire.
3. Python model is converted into a format that can be used in the production environment.
	Use libraries and methods that convert the model into code that can be used in the production environment. Specifically most popular machine learning software frameworks, like PyTorch, TensorFlow, SciKit-Learn, have methods that will convert Python models into intermediate standard format, like [`ONNX (Open Neural Network Exchange format)`](https://onnx.ai/). This intermediate standard format then can be converted into the software native to the production environment. 
	- This is the easiest and fastest way to move a Python model from modeling directly to deployment.
    - Moving forward this is typically the way models are moved into the production environment.
    - Technologies like containers, endpoints, and APIs (Application Programming Interfaces) also help ease the work required for deploying a model into the production environment.

### ML Models and Devops
![ML Models and Devops](img/mlworkflow-devops-1.png)
Considering the components of the Machine Learning Workflow, one can see how Exploring and Processing Data is tightly coupled with Modeling. The modeling can’t occur without first having the data the model will be based upon prepared for the modeling process.

Comparatively deployment is more tightly coupled with the production environment than with modeling or exploring and processing the data. Therefore, traditionally there’s was a separation between Deployment and the other components of the machine learning workflow. Specifically looking at the diagram above, the `Process Data and Modeling` are considered `Development`; whereas, `Deployment` is typically considered `Operations`.
In the past typically, `development was handled by analysts`; whereas, `operations was handled by software developers` responsible for the production environment. With recent developments in technology (containers, endpoints, APIs) and the most common path of deployment; this division between development and operations softens. The softening of this division enables analysts to handle certain aspects of deployment and enables faster updates to faltering models. 

The application communicates with the model through an interface to the model called an endpoint
Communication between the application and the model is done through the endpoint (interface), where the endpoint is an Application Programming Interface (API).
- An easy way to think of an API, is as a set of rules that enable programs, here the application and the model, to communicate with each other.
- In this case, our API uses a REpresentational State Transfer, REST, architecture that provides a framework for the set of rules and constraints that must be adhered to for communication between programs.
- This REST API is one that uses HTTP requests and responses to enable communication between the application and the model through the endpoint (interface).
- Noting that both the HTTP request and HTTP response are communications sent between the application and model.
### Request consists of 4 parts
1. Endpoint
   This endpoint will be in the form of a URL, Uniform Resource Locator, which is commonly known as a web address.
2. HTTP Method
   Below you will find four of the HTTP methods, but for purposes of deployment our application will use the POST method only.
3.HTTP Headers
  The headers will contain additional information, like the format of the data within the message, that’s passed to the receiving program.
4. Message (Data or Body)
   The final part is the message (data or body); for deployment will contain the user’s data which is input into the mode

![HTTP METHODS](img/httpmethods.png)

### Response consists of 3 parts
- HTTP Status Code
  - If the model successfully received and processed the user’s data that was sent in the message, the status code should start with a 2, like 200.
- HTTP Headers
  - The headers will contain additional information, like the format of the data within the message, that’s passed to the receiving program.
- Message (Data or Body)
  - What’s returned as the data within the message is the prediction that’s provided by the model.






