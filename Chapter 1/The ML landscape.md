# The Machine Learning Landscape 

## What is Machine Learning?

The science of programming computers so they can learn from data.

## Why use Machine Learning?

- A ML model can often simplify code and perform better than the traditional approach.

- It is great for complex problems.

- Also, getting insights.

## Types of Machine Learning Systems

To classify them in broad categories, based on the following criteria:

- How they are supervised during training? - Supervised, unsupervised, semi-supervised, self-supervised, others.

- Whether or not they can learn incrementally - Online versus Batch learning.

- Instance-based versus Model-based learning.

## Training Supervision 

### Supervised learning

The training set you feed to the algorithm includes the desired solutions, called *labels*.

Can be used for *Classification* or *Regression*.

*Target* or *Label* are treated as synonyms. But, *target* is more common in regression and *label* is more common in classification tasks. 

*Features* are sometimes called *predictors* or *attributes*. These terms may refer to individual samples. 

### Unsupervised learning

The training data unlabeled. The system tries to learn without a teacher. 

Can be used for *Clustering* algorithm to try to detect groups of similar visitors. Can be used for *Hierarchical Clustering* algorithm, it may also subdivide each group into smaller groups. Also, can be used for *Visualization* algorithm so that you can understand how the data is organized and perhaps identify unsuspected patterns. 

A related task is *Dimensionality Reduction*, in which the goal is to simplify the data without losing too much information. It's often a good idea to reduce the number of dimensions in your training data using a dimensionality reduction algorithm.

Another important task is *Anomaly Detection*: When it sees a new instance, it can tell whether it look like a normal one or whether it is likely an anomaly. 

A very similar task is *Novelty Detection*: It aims to detect new instance that look different from all instances in the training set. 

Another common task is *Association rule learning* in which the goal is to dig into large amounts of fata and discover interesting relations between attributes. 

### Semi-supervised learning 

Some algorithms can deal with data that's partially labeled. 

Most semi-supervised learning algorithms are combinations od unsupervised and supervised algorithms. For example, *clustering* algorithm may be used to group similar instances together, and then every unlabeled instance can be labeled. 

### Self-supervised learning

Generating a fully labeled dataset from a fully unlabeled one. 

"Transferring knowledge from one task to another is called *Transfer learning*."

### Reinforcement learning

The learning system, called an *agent* in this context, can observe the environment, select and perform actions, and get *rewards* in return (or *penalties* in the form of negative rewards).

## Batch versus Online Learning

### Batch learning

In *batch learning*, the system is incapable of learning incrementally: it must be trained using all the available data. It take a lot of time and computing resources, so it is typically done offline. It just applies what it has learned. This is called *offline learning*.

The performance tends to decay slowly over time, the world continues to evolve while the model remains unchanged. It is often called *Model rot* or *Data Drift*.

The solution is to regularly retrain the model on up-to-date data.

### Online learning

You train the system incrementally by feeding it data instances sequentially, either individually or in small groups called *mini-batches*. 

It is useful for systems that need to adapt to change extremely rapidly. 

Also, it can be used to train models on huge datasets that cannot fit in one machine's main memory (this is called *out-of-core* learning).

One important parameter of online learning systems is how fast they should adapt to changing data: this is called *Learning rate*. 

- High learning rate: Rapidly adapt to new date, but it will also tend to quickly forget the old data. 

- Low learning rate: The system will have more inertia, that is, it will learn more slowly, but it will also be less sensitive to noise or to sequences of nonrepresentative data points (outliers).

"Online learning can be confusing name, once out-of-core learning is usually done offline. Think of it as *incremental learning*.

Challenge: If bad data is fed to the system, the system's performance will decline, possibly quickly. 

To reduce risk, you need to monitor your system closely and promptly switch learning off (and possibly revert to a previously working state).

## Instance-based versus Model-based learning

It's about how they *generalize*.

Having a good performance measure on the training data is good, but insufficient; the true goal is to perform well on the new instances.

### Instance-based learning

The system learns the examples by heart, then generalizes to new cases by using a similarity measure to compare them to the learned examples (or a subset of them).

### Model-based learning

To generalize from a set of examples is to build a model of these examples and then use that model to make *predictions*.

### A typical Machine Learning workflow

You have data about Better Life Index from OECD's website. So you decide to model life satisfaction as a linear function of GDP per capita. This step is called *model selection*: you select a linear model of life satisfaction with just one attribute, GDP per capita.

- How can you know which values will make your model perform best?

You need to specify a performance measure. You can either define a *utility function* (or *fitness function*) that measures how *good* your model is, or you can define a *cost function* that measures how *bad* it is. 

For linear regression, people typically use a cost function that measures the distance between the linear model's predictions and the training examples; the objective is to minimize this distance.