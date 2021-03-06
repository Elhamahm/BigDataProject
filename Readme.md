## Observed objects classification based on fMRI data

### **Abstract** 

Neuroimaging is one of the fields that related to big data for some reasons. First of all, with the development of 
MRI scanner, now we can capture images of brain in ultra-high resolution. But this development comes with the issue 
that MRI data become big data that is difficult to be stored and processed by personal computers. In the other hand,
MRI data can be analyzed to structure human brain, research brain functions and activities using different techniques
including machine learning algorithms. In this project, we present a classification problem using fMRI images and 
neural network. We also analyze the performance of the algorithms in terms resource usage.


### **I. Introduction**

Neuroimaging is a relatively new field emerged with the development in neuroscience, psychology and computer science 
which works with brain images to capture and analyze the structures and functions in parts of nervous system.
Thanks for the development of MRI techniques, compute and storage capability of modern computers as well as 
the efficiency machine learning algorithms, nowadays we can capture human brain images in high resolution, 
and use this data to analyze the structure of human brain. When it comes to computer science, using 
machine learning algorithms, now we are able to investigate how brain functions in certain activities. 

In this project, we apply deep learning algorithms to classify objects observed by subjects using fMRI data. 
Subjects involved in the experiments were shown different images of static objects as well as animated images. 
The fMRI data of their brains when they were looking at the images was recorded in time steps.
This is the input for our classification algorithm.

Since the neuroimaging data is considered big data, in many applications, 
the problems that neuroscientists as well as computer scientists are tackling with are not only which algorithms 
to apply, what is the best configuration for the algorithms, but also the problems in resource optimization, 
reproducibility and fault-tolerance.  Thus, in this project, we also profile the performance of the algorithm 
on used data set  in terms of used resources such as CPU and memory in different steps, from data pre-processing 
to model training,  validation and testing. By doing this analysis, our expectation is to have an idea of 
where could be the bottleneck, what could be improved to optimize resource usage.

### **II. Materials and methods**. 

#### **1.  Materials**
    
#### **1.1 Dataset**

The dataset used is fMRI images from BOLD5000, which is a large-scale, slow event-related fMRI dataset.
The training data, which consists of 2047 samples recorded in 10 seconds, is split into 6 files, 5 image files 
and 1 label file, 1.94 GB each file.
Data from all input files will be stacked together and split into training set and test set.

#### **1.2 Technologies**

In this project, we use **_tensorflow_**, **_keras_**, which is widely used for deep learning,
and **_sklearn_** for data preprocessing and performance evaluation. 
 
#### **2. Method**

For this classification problem, since the fMRI images are in time series and are related,
we choose LSTM as our classifier. 
The model is trained with batch size of 50 and Adam as the optimizer. 
After the model is trained, we use some metrics to measure the performance of out model. Apart from accuracy, 
we will use ROC curve and confusion matrix to evaluate since this is a multiclass classification problem and 
the classes are imbalance.

Since we want to analyze the resource usage when the model is trained, we do not pre-process the data 
and train our model with the original data. By doing this, the training will be compute-intensive as well as 
memory consuming, and the impact of model and hyperparameter choices can be more visible. This may make the bottlenecks 
to be identified and the improved more easily.

When it comes to resource profiling, we focus on CPU time, memory usage and cache used if possible as these usually 
are the possible bottlenecks to be optimized.

