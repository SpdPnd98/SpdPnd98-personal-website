---
title: "How to use darkflow with Intel Movidius Neural Compute Stick"
published: false
---

**Note:** The following tutorial explains how to use ```darkflow``` framework, which is a tensorflow implementation, and integrate it with ```Intel Movidius Neural Compute Stick```. This tutorial has been tested on Ubuntu 16.04LTS, CUDA9.0 and CUDNN8.0, and assumes you already have them installed.

# Preface
It has come to my attention that the Intel Movidius Neural Compute Stick is rarely spoken of. This could be due to the lack of large community at the moment, or maybe darkflow is not a widely used framework. In the official documentation of Intel Movidius Neural Compute Stick, the 2 most used frameworks are caffe and tensorflow. 

Although caffe is a very powerful framework, and tensorflow provides a lot of fine tuning and (almost) complete comtrol over models, I have had very great experience with darknet, a C/C++ implemented framework for yolov2 model, hence I was curious to see what darkflow, the tensorflow implementation of darknet, has in store.

However, finding proper source code for interpreting the graph file passed into movidius stick is difficult, hence here at modelconverge.xyz, I would like to show you my results and training procedure.

Almost a year ago, I have listened Mr. YuFeng Guo's presentation on 7 steps to machine learning and here I shall show you how top use them as well.

## Easy 7 steps
I have found great succes over the course of applying the following 7 steps, so here they are:
1. Gathering Data 
2. Preparing that Data 
3. Choosing a Model 
4. Training 
5. Evaluation 
6. Hyperparameter Tuning 
7. Prediction

### Step 1. Gather Data
Gathering data is easy right? Well, maybe. Sometimes, you just have the data you need before you even think of solving the problem, but for AI/ML enthusiasts like us, data is like the new oil, if you get it, sprinkle a little bit of AI, ~ BAM ~, a fresh hot recipe for a startup is brewed. I recommend using a batch downloader and gather your initial training data from the public domain, just to get a proof of concept. Another (even better) way is to check if the problem you have at hand has ever been somewhat involved in an online competiton like Kaggle's competitions etc.

Depending on your framework, you may need to save your data in different formats. For darkflow, you don't need any special way of naming/formating of the image, as we'll be using a simple labeling image tool.

Of course, to make things easier, a format as such will suffice (minimal):

```Directory
Data
| Images
| Annotations
```
Store all your data in the Images directory
We'll annotate the images and save the .xml files in Annotations

### Step 2: Preparing Data
This step mainly focuses on filtering your data and labeling your data. Take a look at all your data, are there duplicates? Are there images that are irrelevant? Are there images with weird file extensions (.gif, .ico, etc.)? Delete them if need be, make sure your data is as clean as possible.

Congratulations! You've passed a big hurdle for training AI models at this point!

Now, we need to label our precious, clean data. Clone this repository: