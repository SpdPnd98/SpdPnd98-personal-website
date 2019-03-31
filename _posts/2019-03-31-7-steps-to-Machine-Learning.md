---
title: "7 Steps to machine Learning"
published: false
---

# Preface
Hello guys, Around 1 year ago, I have been to a talk by YuFeng Guo in Singapore. I have documented his talk in another blog post of different domain but I wish to revise my thoughts after 1 year of digestion.

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

Now, we need to label our precious, clean data. Clone this repository: (labelImg GUI)[https://github.com/tzutalin/labelImg]

``` git clone https://github.com/tzutalin/labelImg ```

Next:

```
cd labelImg
python3 labelImg.py
```

this step includes drawing a boundary box over your image data (assuming that's what you have). Change the saving Annotations file to path/to/data/Data/Annotations. After 1 annotation, check that there is indeed an xml file at the designated annotation folder.

also, create a labels.txt that has all your classes in different lines.

After this step, congrats! Because you have completed all the boring checklist!

### Step 3: Choosing a model
Now, at this step, you may be tempted to just choose one of the many algorithms and see the result. I have tested some of the algorithms and indeed, sometimes due to data incompleteness, characteristics of data etc, the benchmarks documented may be slightly off compared to what you experience, but for scientific reasons I believe looking at the various models darkfow support is beneficial. Nonetheless, I chose Tiny YOLO V2 as my model due to its speed while being relatively accurate.

Some things to note when choosing this model:
- change the classes to the amount of classes you are training
- change the filter according to (N+5) * 5, N being amount of classes
- changing batch size doesn't affect actual training using darkflow, but does on darknet

More details on TinyYOLO algorithm and how it compares to other algs here: [https://pjreddie.com/darknet/yolo/]

### Step 4: Training
Finally, pass in your dataset, labels, annotations, cfg file into darkflow. You can edit the batch size to any number your GPU can handle. I left mine at default. Specify the input layer as "input" and output layer as "output".