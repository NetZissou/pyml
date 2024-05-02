# Types of ML Systems

These criteria are not exclusive, we could combine them in any we want.

Think of what types of data you have, and what task is at hand?

- Whether or not they are trained with human supervision (**supervised, unsupervised, semisupervised, and reinforcement learning**)
- Whether or not they can learn incrementally on the fly (**online versus batch**)
- Whether they work by mapping new data to new data points, or instead, by detecting patterns in the training data and building a predictive model. Different ways to generalization (**instance-based versus model-based learning**)

## Criterion: Supervision

### Supervised Learning
Feed a training set that includes the desired solutions, aka labels. Typical supervised learning task are classification and regression. Here are some important supervised learning algorithms:
- k-Nearest Neighbors
- Linear Regression
- Logistic Regression
- Support Vector Machine
- Decision Trees & Random Forests
- Neural Networks

### Unsupervised Learning
Training data is unlabeled. The system is expected to learn without a teacher. Typical unsupervised tasks are clustering, 2D or 3D visualization, dimensionality reduction, anomaly detection (detecting fraud, catching defects, removing outliers), association rule learning (supermarket customer sales). Some important unsupervised learning algorithms are:
- Clustering
  - K-Means
  - DBSCAN
  - Hierarchical Cluster Analysis
- Anomaly detection & Novelty detection
  - One-class SVM
  - Isolation Forest
- Visualization & Dimensionality Reduction
  - Principal Component Analysis
  - Kernel PCA
  - Locally Linear Embedding
  - t-Distributed Stochastic Neighbor Embedding
- Association rule learning
  - Apriori
  - Eclat

### Semisupervised Learning
You have plenty of unlabeled instances, and few labeled instances. Examples, Google Photos: 
You upload all your family photos to the service, it automatically recognizes the same person A shows up in photos 1, 5 and 11, while person B shows up in photo 2, 5, and 7. Now you tell the system who these people are by adding one label per person, and it can now name everyone in every photo. 

### Reinforcement Learning
The learning system, aka the agent, can **observe** the environment, **select** and **perform actions**, and get **rewards** in return. It must then learn by itself (optimize) what is the best strategy, called a *policy* to obtain the most reward over time. A *policy* defines what action the agent should choose when it is in a given situation.





## Criterion: Batch vs "Online"
Whether the system can learn incrementally from a stream of incoming data. 

### Batch Learning
The batch learning system is **incapable of learning incrementally**: **it must be trained using all the available data.** Hence, it takes a lot of time and computing resources to train, so it's typically done offline. First the system is trained offline, and then it is launched into production and runs without learning. To add new data, we need to train the model using all of the data from scratch. 


### Online Learning (incremental learning)
Train the system incrementally by feeding it data instances sequentially, either individually or in mini-batches. Each learning step is fast and cheap, so that the system could learn new data on the fly.

**Great for adapting changes:**
The system can receive data as a continuous flow and discard afterwards to save disk space.

**Great for huge datasets (out-of-core leaning):**
If you have data that cannot fit in one machine's main memory, the algorithm can load part of the data, runs a training step, and repeat the process until it has run on all data. 

**Learning Rate:**
LR is the parameter of online systems that controls how fast they should adapt to changing data. If LR is high, then the system will rapidly adapt to new data, but it will also quickly forget old data. If you set a low LR, the system will learn more slowly, it will also be less sensitive to noise and non-representative outliers. 

**Challenge in learning:**
If bad data is fed to the system, then system's performance will gradually decline. To reduce this risk, monitor your system closely and promptly switch learning off. You may also want to use anomaly detection algorithm to monitor the input. 


## Instance-based vs Model-based
Another way to categorize ML systems is by how they generalize. Generalization: makes good prediction for examples it has never seen before.

Two main approaches to generalization: instance-based vs model-based

### Instance-based Learning
The system learns all provided examples by heart, generalizes to new cases by using a similarity measure to compare them to learned examples. 

Pros:
- No training time
- Easily adapt to new data
- Handling Complex Non-linear Data Patterns
  
Cons:
- Requires large storage space to keep all data for comparison
- Long prediction time. New instance is compared to all instances
- Distance calculation and sorting ops could be expensive

### Model-based learning
Build a model from the provided examples, then use the model to make predictions. Model is structured by parameters. 

Model-based learning algorithm search for optimal value of parameters such that model will generalize well to new instances.