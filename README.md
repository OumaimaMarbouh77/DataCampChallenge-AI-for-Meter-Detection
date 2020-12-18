# DataCampChallenge-AI-for-Meter-Detection
Meter Detection

## Introduction
We are working on DataCamp Challenge (AI for Meter Detection). SUEZ company aims to minimize the cost of collecting water consumption through the traditional method by sending agents to consumers housers to check the meter. In this new method, it aims to involve the client in the process by collecting images sent by the them.


## Data Processing
We have a dataset composed of Meter Images sent by SUEZ clients that we have to analyse in order to extract the water consumption in m3 and compare it to the registered data in the index file above to calculate the accuracy. We cleaned our data, resize it and normalize it in order to facilitate the analysis.


## Methods
We proceeded in three steps: 
-Meter and ID-Region detection: we used here Open CV library to extract relevant region for us using multiple functions that you can find in DataCamp notbook.
-Digit Segmentation: we used MSER(Maximally stable extremal regions) analysis to detect and extract digits.
-Digit Recognition: we used yolo models.


## Results
### Open CV + MSER: 
for the open cv method method it worked well on some images and on others not we tried to generalize parameters but it's impossible. So we proceeded after that with MSER that was detecting digits and some non digits areas which made our analysis more complicated and with low quality. 

### Open CV + Yolo v3 for 1 class:

We used the tool labellmg: https://tzutalin.github.io/labelImg/ latest version to detect relevant areas(digit areas) manually in our images then we took the coordinates resulted file to train our yolov3 model. We ended up with good results where the detection was done only on digits area but we got full consumption number as an image that we have to seperate to single digits or to transform to a number representing our consumption: for example an image that contains (12345) and we have to extract 12345 number from it or 1-2-3-4-5 seperately as single digits (if anyone has an idea how we can do that we will be grateful for your comment).

### Yolo v3 for multiple classes:

We proceeded with yolo v3 for multiple classes where we tried to detect each digit seperatly(1-2-3-4-5) from the others by selecting the different areas in our previous result from Yolo and open cv. We still didn't do it right and no resuls for themoment but you can find code above.


### Yolo v3 + Resnet 50

In order to detect numbers we used a pretrained model on MNIST dataset to detect single digits and we obtained results but not good quality.





