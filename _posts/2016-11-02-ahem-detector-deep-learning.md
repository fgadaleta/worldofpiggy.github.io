---
layout: post
title: Ahem detector with deep learning  
tags: [analytics, deep learning, audio, podcast, sound, feature engineering]
comments: true
type: post
---

Do you know why you can't hear the ugly *ahem* sounds on the podcast [Data Science at Home](http://worldofpiggy.com/podcast)?

Because we remove them. 
Actually not us. A neural network does.

Let me introduce the *ahem detector*, a deep convolutional neural network that is trained on transformed audio 
signals to recognize "ahem" sounds.
The network has been trained to detect such signals on the episodes of Data Science at Home, the podcast about data science at 
[worldofpiggy.com/podcast](http://worldofpiggy.com/podcast) 


## Project description

Slides and technical details are provided provided [here](https://docs.google.com/presentation/d/1QXQEOiAMj0uF2_Gafr2bn-kMniUJAIM1PLTFm1mUops/edit?usp=sharing).

Before getting to the details, a few concepts should be clarified.

Two sets of audio files are required, very similarly to a cohort study:

- a negative sample with clean voice/sound and 

- a positive one with "ahem" sounds concatenated

While the detector works for the aforementioned audio files, it can be generalized to any other audio input, provided enough data 
are available. The minimum required is ~10 seconds for the positive samples and ~3 minutes for the negative cohort. 
The network will adapt to the training data and can perform detection on different spoken voice.


### How do I get set up? ###
Once the training audio files are provided, just load the training set and train the network with the code in the ipython notebook.
Make sure to create the local folder that has been hardcoded in the script files below.
Build training/testing set before running the script. 
Execute first 

    % python make_data_class_0.py
    % python make_data_class_1.py

A GPU is recommended as, under the conditions specific to this example at least 5 epochs are required to obtain ~81% accuracy.


### How do I clean a new dirty audio file?
A new audio file must be trasformed in the same way of training files.
This can be done with

    % python make_data_newsample.py
    
Then follow the script in the ipython notebook that is commented enough to proceed without particular issues.
The whole project is on [github](https://github.com/worldofpiggy/deeplearning-ahem-detector)



Enjoy!
