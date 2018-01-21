# **Behavioral Cloning** 

---

**Behavioral Cloning Project**


## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/432/view) individually and describe how I addressed each point in my implementation.  

---
### Files Submitted & Code Quality

#### The files

My project includes the following files:
* model.ipynb containing the notebook to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md summarizing the results

#### The network and data

In order to get this project working, I have collected my own data.

To avoid overfitting, I did 2 normal laps, 1 lap in the opposite direction and made some data about recovering from the side of the road. I have also added some additional data about taking sharp turns. Ihave used the Nvidia architecture for the model and applied dropout, so the model won't overfit. I have also added flipped images of the center pictures. I resized the pictures, so the model has to deal with a fewer amount of pixels per picture. I have also tried to convert the pictures to grayscale, but I have got worse results, than my submission.
I have trained the model on a p2.xlarge AWS instance, so I could fit all the data into memory. I have modified the drive.py, so it also reduces the size of the image.

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

I have randomly shuffled the data before creating the training set, so I could further reduce overfitting.

#### Result
The model was able to guide the car sucessfully through the track, without going down, with a speed of 9. The start of the track is a bit shaky, however later the driving is really smooth and always gravitates towards the center of the track. 