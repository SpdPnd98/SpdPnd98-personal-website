---
title: "7 Steps to Image Classification with AI"
published: true
---

# Preface
Hello guys, Around 1 year ago, I have been to a talk by YuFeng Guo in Singapore. I have documented his talk in another blog post of different domain but I wish to revise my thoughts after 1 year of digestion.

Not only that, I have used the same framework in AI, here is my 7 steps to Image Classification with AI.

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

Depending on your framework, you may need to save your data in different formats. 

Of course, to make things easier, a format as such will suffice (minimal):

```Directory
Data
| Images
| Annotations
```
Store all your data in the Images directory

### Step 2: Preparing Data
This step mainly focuses on filtering your data and labeling your data. Take a look at all your data, are there duplicates? Are there images that are irrelevant? Are there images with weird file extensions (.gif, .ico, etc.)? Delete them if need be, make sure your data is as clean as possible.

Congratulations! You've passed a big hurdle for training AI models at this point!

Now, we need to label our precious, clean data. Again, depending on your choice of classification, this may or may not be required.

This step includes drawing a boundary box over your image data (assuming that's what you have) and generate an XML file with your image's classes. 

Also, create a labels.txt that has all your classes in different lines.

Another topic we discuss here would be a train-test split. A lot of people will tell you different train-test split ratios, but generally a 9:1 to a 10:1 is a good split.

After this step, congrats! Because you have completed all the boring checklist!

### Step 3: Choosing a model
Now, at this step, you may be tempted to just choose one of the many algorithms and see the result. I have tested some of the algorithms and indeed, sometimes due to data incompleteness, characteristics of data etc, the benchmarks documented may be slightly off compared to what you experience, but for scientific reasons I believe looking at the various models is beneficial.

More details on algorithms and how it compares to other algs here: [darknet supported algoritms](https://pjreddie.com/darknet/yolo/) and [Other good algorithms](https://medium.com/zylapp/review-of-deep-learning-algorithms-for-image-classification-5fdbca4a05e2)

### Step 4: Training
Finally, pass in your training dataset, labels, annotations, model files into your model/framework. The methods of training differes from framework to framework, but generally this step is considered the easiest.

The AI algorithm will generate layers that contain important features of a class. After this phase the model will be able to recognize objects in images!

### Step 5: Evaluation
Evaluation basically means to see how accurate your weights are by benchmarking your model to the test dataset. Your model (ideally) should not overfit nor underfit. Good accuraccies around 95-98% IMO, but may vary according to algorithms, features, and datasets. 

There are a lot of tools for people to choose from, my favorites being `Tensorboard` and `mAP`. Theories are explained in a seperate blog post.

### Step 6: Hyperparameter Tuning
In Image recognition sense, hyperparameters have a wide range, from augmentation of image to decay rate and learning rate. Upon evaluating the model, you can tune the hyperparameters to improve the performance of your final model, making it converge faster and/or become more accurate. The possibilities are endless, but not for the faint of heart. For beginners, stick to the basic trainings, and tune only if you need to, going back all the way to Step 1 at times just to ge the best model possible.

###Step 7: Prediction
Finally we have reached the last step, which is evaluating the model with data the model has not seen before. This moment in my opinion is the most exciting, as we can see how our model performs outside of a controlled environment, and detect any loopholes the model may have, including more edge cases and retrain the model. Thought it may not be entirely neccessary, this is truly where the fun begins, stress testing your model to its limit.

# Conclusion

These are the 7 steps that I usually follow when training my own image classifier, and has brought me success in evaluating my model's success/failure. Drop me an email if you have any question and I hope this blog post has been of value to you. Thanks