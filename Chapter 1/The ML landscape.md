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

In summery:

- You studied the data,
- You select da model,
- You trained it on the training data,
- Finally, you applied the model to make predictions on new cases.

## Main Challenges of Machine Learning 

The bad model and the bad data.

### Insufficient Quantity of Training Data

Very different machine learning algorithms, including fairly simple ones, performed almost identically well on a complex problem of natural language disambiguation once they were given enough data.

The idea that *data matters more than algorithms for complex problems*.
- paper "The Unreasonable Effectiveness of Data".

### Nonrepresentative Training Data

It is crucial that your training data be representative of the new casas you want to generalize to. 

If the sample is too small, you will have *sampling noise*, but even very large samples can be nonrepresentative if the sampling method is flawed. This is called *sampling bias*.

### Poor-Quality data

If your training data is full of errors, outliers, and noise, it will make it harder for the system to detect the underlying patterns. 

### Irrelevant features

Your system will only be capable of learning if the training data contains enough relevant features and not too many irrelevant ones. This process is called *feature engineering*.

- *Feature selection*: selecting the most useful features to train on among existing feature. 

- *Feature extraction*: combining existing features to produce a more useful one. 

- Creating a new feature by gathering new data.

### Overfitting the Training Data 

The model performs well on the training data, but it does not generalize well. 

Complex models such as deep neural networks ca detect subtle patterns in the data, but if the training set is noisy, or if it is too small introduces sampling noise, then the model is likely to detect patterns in the noise itself.

Overfitting happens when the model is too complex relative to the amount and noisiness of the training data. 

Constraining a model to make it simpler and reduce the risk of overfitting is called *regularization*. 

You want to find the right balance between fitting the training data perfectly and keeping the model simple enough to ensure that it will generalize well.

The amount of regularization to apply during learning can be controlled by a *hyperparameter*.

If you set the regularization hyperparameter to a very large value, you will ger an almost flat model. Tunning hyperparameter is an important part of building a machine learning system. 

### Underfitting the Training Data

It occurs when your model is too simple to learn the underlying structure of the data.

Here are the main options for fixing this problem:

- Select a more powerful model, with more parameters. 
- Feed better features to the learning algorithm (feature engineering).
- Reduce the constraints on the model (for example by reducing the regularization hyperparameter).

## Testing and Validating

The only way to know how well a model will generalize to mew cases is to actually try it out on new cases. 

A better option is to slip your data into two sets: the *training set* and the *test set*.

The error rate on new cases is called the *generalization error* (or *out-of-sample error*). This value tells you how well your model will perform on instances it has never seen before. 

If the training error is low (your model makes few mistakes on the training set) but the generalization error is high, it means that your model is overfitting the training data. 

### Hyperparameter Tunning and Model Selection

- How do you choose the value of the regularization parameter?

A common solution to this problem is called *Holdout validation*: you simply hold out part of the training set to evaluate several candidate models and select the best one. The new held-out set is called *Validation set*.

After this holdout validation process, you train the best model on the full training set (including the validation set). Lastly, you evaluate this final model on the test set to get an estimate of the generalization error.

- If the validation is too small or if the validation set is too large: One way to solve this problem is to perform repeated *cross-validation*, using many small validation sets. By averaging out all the evaluation of a model, you get a much more accurate measure of its performance. However, the training time is multiplied by the number of validation sets.

### Data Mismatch

It's easy to get a large amount of data for training, but this data probably won't be perfectly representative of the data that will be used in production.

Both the validation set and the test set must be representative as possible of the data you expect to use in production.

One solution is to hold out some of the training pictures, the *train-dev set*. After the model is trained, you can evaluate it on the train-dev set. If the model performs poorly, then it must have overfit the training set, so you should try to simplify or regularize the model, get more train data, and clean up the training data. But if it performs well on the train-dev set, then you can evaluate the model on the dev set. If it performs poorly, then the problem must be coming from the data mismatch. 

Once you have a model that performs well on the train-dev set and the dev set, you can evaluate it one last time on the test set to know how well it is likely to perform in production. 

