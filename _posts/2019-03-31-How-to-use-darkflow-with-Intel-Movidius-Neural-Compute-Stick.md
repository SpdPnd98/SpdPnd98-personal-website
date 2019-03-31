---
title: "How to use darkflow with Intel Movidius Neural Compute Stick"
published: true
---

**Note:** The following tutorial explains how to use ```darkflow``` framework, which is a tensorflow implementation, and integrate it with ```Intel Movidius Neural Compute Stick```. This tutorial has been tested on ```Ubuntu 16.04LTS```, ```CUDA9.0``` and ```CUDNN8.0```, and assumes you already have them installed.

# Preface
It has come to my attention that edge image classification is highly under-discussed. This could be due to the lack of large community at the moment, or maybe frameworks are not optimized for edge computing. In the official documentation of ```NCSDK API```, the 2 most used frameworks are ```caffe``` and ```tensorflow```, which inspired me to use my knowledge on ```tensorflow``` to check out ```darkflow```. However, ```Intel Movidius Neural Compute Stick``` is rarely used together with the said framework. Hence I began on my journey scouring the web and all documentations I can find to get ```darkflow``` to work on the ```Intel Movidius Neural Compute Stick```.

Although ```caffe``` is a very powerful framework, and ```tensorflow``` provides a lot of fine tuning and (almost) complete comtrol over models, I have had very great experience with ```darknet```, a ```C/C++``` implemented framework for yolov2 model, hence I was curious to see what ```darkflow```, the ```tensorflow``` implementation of ```darknet```, has in store.

However, finding proper source code for interpreting the graph file passed into movidius stick is difficult, hence here at <href src = "modelconverge.xyz"/>, I would like to show you my research results and steps required for proper training.

Note this blogpost is not for beginners. Check out my blog for 7 steps to Machine Learning in a seperate blogpost for the basic idea of the steps I follow.

The aim of this tutorial is just to setup darkflow, setup ```NCSDK2``` and compile a graph file that is intepretable by the ```Intel Movidius Neural Compute Stick```, and read the output, ending off with an exmaple. 

# Setup 
Clone the ```darkflow``` repository:

```git clone https://github.com/thtrieu/darkflow```

Please see the official docs for training steps, but for TLDR:
- get training data
- use a labeling image tool to label your images in xml format, link [here](https://github.com/tzutalin/labelImg)
- generate your labels in .txt file
- edit cfg file (eg, filter and classes in yolov2 model)
- pass in the above to darkflow with the following command
```./flow --labels labels.txt --model model.cfg --dataset /path/to/dataset --annotations /path/to/xml/annotations --train --trainer your_preference --batch size (Enter your number) --gpu (0.0(min) - 1.0(max)) --load(optional) -1(latest)OR(a recorded weight index)```

After your training, you should see .meta files and .pb files in ckpt directory of darkflow. These are graph files compatible with Tensorflow, but not with NCSDK2. 

Generate the frozen pb file with the following command:
```./flow --model /path/to/cfg --load (your tensorflow weights) --savepb /path/to/output```

Next, clone the following 2 repositories: yolo-darkflow-movidius & NCSDK2

```
git clone https://github.com/SpdPnd98/yolo-darkflow-movidius.git
git clone t clone -b ncsdk2 http://github.com/Movidius/ncsdk && cd ncsdk && make install
```
use ```-b ncsdk2``` to clone NCSDK2, you can clone NCSDK, but will need to make modifications according to this [website](https://movidius.github.io/ncsdk/ncapi/python_api_migration.html)

if you have caffe installed, comment out the path to your caffe directory, as ncsdk examples depend on and comes with a caffe installation. ncsdk2 also uninstalls any installation of OpenCV. If you however wish to ignore their examples, feel free to use ```make api``` instead of ```make```, as we will show below.

Editing the cfg file follows the same format for darknet, please read the documentation [here](https://pjreddie.com/darknet/yolo/)

# Preparing for Intel Movidius Stick
The command to convert the graph file output to a graph file that complies to Intel Movidius Stick is the command below:
```mvNCCompile -s 12 /path/to/graph.pb```
please refer here for more arguments(https://movidius.github.io/ncsdk/tools/compile.html)

the -s argument indicates the amount of SHAVES used. SHAVES is analogous to core counts, max is 12 SHAVES. Read [here](https://movidius.github.io/ncsdk/ncs.html) for more details.

Next, we need to create a symbolic link in ```yolo-darkflow-movidius``` directory
```
cd yolo-darkflow-movidius/
pip install --upgrade cython

ln -s ../darkflow/darkflow darkflow
```
At this point, preparations are all done!

# Example on PC/Laptop

To demonstrate an example, run the following commands to prepare:

```
cd ../darkflow
wget -O tiny-yolo-voc.cfg https://raw.githubusercontent.com/pjreddie/darknet/master/cfg/yolov2-tiny-voc.cfg
wget -O tiny-yolo-voc.weights https://pjreddie.com/media/files/yolov2-tiny-voc.weights

python3 ./flow --model tiny-yolo-voc.cfg --load tiny-yolo-voc.weights --savepb
cd ../yolo-darkflow-movidius
mv  darkflow/built_graph/
mvNCCompile built_graph/tiny-yolo-voc.pb -s 12 -in input -on output -o built_graph/tiny-yolo-voc.graph 
```

Now, run this to see the result, with your ```Intel Movidius Neural Compute Stick``` plugged in:

```
python3 test_movidius.py -i video.avi
```
Congrats, you have succesfully run a TinyYOLO model on movidius stick! Expect similar results when exporting them to the edge!

# Edge example

Grab a coffee and something to do because the procedures are largely the same, but taking a lot longer in an environment like raspberry pi or other device. Do note to use ```make api``` instead of ```make``` when building ncsdk2.

This time, you do not need to train a model, but just import a model like the example above. 

Hope this blog has been of help. Drop me an email if you have any questions. Thanks.