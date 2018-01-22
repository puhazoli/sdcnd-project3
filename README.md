# **Behavioral Cloning** 

---
### The files

My project includes the following files:
* model.ipynb containing the notebook to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md summarizing the results

### Architecture and Training Documentation 

#### Data collection

In order to get this project working, I have collected my own data.

To avoid overfitting, I did 2 normal laps, 1 lap in the opposite direction and made some data about recovering from the side of the road. I have also added some additional data about taking sharp turns. I have also added flipped images of the center pictures and tried to convert the pictures to grayscale, but I have got worse results, than my submission. Moreover, I used images from the left and tight camera, adjusting the steering angle with +-0.2.

I have randomly shuffled the data before creating the training set, so I could further reduce overfitting.

##### Model architecture

I started out with a normal fully connected network, with only one layer (100 nodes). I tried this out to see, if the model is receiveing the data correctly and to see if the predictions are in a reasonable scale. After this, I started to build in convolutional layers, however I faced the problem of running out of the GPUs memory, as the original picture size was too big. I then decided to resize the picture, that helped me to use bigger networks, with not a lot of loss of information. I have also changed the pictures to RGB as opposed to the default of opencv, that reads in pictures as BGR. 
Finally, after reading so much good about it, I tried the Nvidia [architecture](https://devblogs.nvidia.com/deep-learning-self-driving-cars/) for the model. This model was working well, however it slightly overfitted the data. By applying dropout, I have reduced this issue (dropout of 0.2 on 2 dense layers). I used relu activation functions on all the layers. I was happy with this architecture, as it drived perfectly on the first lap. For future work, I could build a model (ie: get data from the second lap) that would be able to drive through the whole second lap.

#### Training

I have trained the model on a p2.xlarge AWS instance, so I could fit all the data into memory. I have modified the drive.py, so it also reduces the size of the image. The ipython notebook contians all the code that was used for data generation and model training. I used 5 epochs for the training with Adam optimizer, and used random subset of the images for the validation data. The error on the validation set was comparable to the one that was on the training set, that means that the model could generalize well.

#### Result
The model was able to guide the car sucessfully through the track, without going down, with a speed of 9. The start of the track is a bit shaky, however later the driving is really smooth and always gravitates towards the center of the track. 
