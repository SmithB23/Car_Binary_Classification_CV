![image](https://github.com/user-attachments/assets/362f9f1c-c5f7-4cbc-9416-e2cf087f7cde)
# Binary Classification of Cop Cars
This project aims to differentiate between police cars and civilian cars.

# Overview
The goal of the project is to classify if a photo of a car has a police or civilian car through binary classification, as well as see how the model would preform given less photos. I will be using transfer learning to speed up the process, use less data, and have a good accuracy.The data was pulled from two seperate datsets within Roboflow Using ResNet50, I determined that the differnce between the amount of photos did not play much significance in increasing the accuracy at this scale. Despite the seemingly randomness of the accuracy depending on the amount of photos, the highest accuracy was achieved with 100 total photos (50 Police/50 Civilian), at 85.93%.

# Summary 
- ## Data
    - Data consistsof two seperate folders containing police cars as well as civilian cars.
    - Police Folder consists of 260 cars
          -https://app.roboflow.com/smithb23/police_cars-5x7fo/1   2.87 MB
    - Car Folder consists of 28,045 vechicles
          -https://app.roboflow.com/smithb23/vehicle-classification-eapcd-al8dr/2 264 MB
    - 80-20 split between training and testing
    
- ## Preprocessing
    - Sorted out all non-vehicles in the Car folder
    - Made all images 224x224 pixels
    - Used minor augmentation for a better model
 
- ## Visualization
-Example of a before and after image regarding augmentation
<img width="757" height="389" alt="image" src="https://github.com/user-attachments/assets/c5aa3d7f-6c40-46fa-b517-2ab1246924ff" />

-50 Civilian/50 Police
<img width="850" height="358" alt="image" src="https://github.com/user-attachments/assets/fbc9f807-2ff1-4688-8957-4b809270e180" />

I used varying amounts of images, but the 50/50 split showed above had the best results. However, regardless of the number of images, the results and their respective graphs for accuracy as well as loss did have a significant enough differnce for a true comparison. They were all really similiar to eachother, which is a result in itself.




## Problem Formulation
-The orginal goal was to use transfer learning and use binary classification to determine if a car was either police or       not_police cars. Resnet50 pre-trained on ImageNet, and multiple different metrics were used, such as accuracy and recall. Initially, the goal was straightforward: fine-tune a transfer learning model and evaluate its performance using standard metrics such as accuracy and recall. I found out early on that my model had a very high preformance. This indicated potential overfitting. With that, I determined a more intersting goal would to be see how few images could yield proper results. With my goal set up now, I began to augment my data work on improving my model nonetheless. After that, I would determine the amount of necessary epochs and find out my results.
  
## Training
- Software: Jupyter Notebook, Python 3, Resnet50, Imagenet
- When the model was working properly, eavh epoch would take on average 60 seconds to complete
- Each epoch gave the accuracy, loss, and and recall for training as well as validation
- Started with 10 epochs and would change the amount based off original results
- I made sure to do this each time I changed the amount of images used, mainly lowering the amount of civilian cars, and occasionally police cars.
- With around 10 epochs taking a minute each, the model was pretty fast, taking only 10 minutes each time.

## Perfomance
- Despite the change in amount of images, my validation accuracy didn't change too much. Ranging from 70-80% on average
- The highest validation accuracy by the end of the 10 epochs was .8593
- The lowest validation accuracy by the end of the 10 epochs was .5861

|Total Images|Police Images|Civilian Images|Epochs|Accuracy|Recall|
|---|---|---|---|---|---|
|660|260|400|10|58.61%|94.23%|
|500|100|400|10|83.89%|90.46|
|300|100|200|10|74.87%|86.84|
|100|50|50|10|85.93%|84.62%|


## Conclusions
Interstingly enough, it seems like the less photo used, the more accurate the model was. While I wish this was simply the case, this is most likely the result of the model guessing, but not having as many points to get wrong. I made sure to add wieghts to prevent the model from only choosing civilian, but the results are still sub-par. With the most amount of images, the accuracy was .6010. The best accuracy was .8593, which is much better than guessing. This accuracy was made when using 50 civilian images and 50 police images. However, the goal was not to get the best accuracy, it was to see how well he model could do without a large amount of images. *50 civilian and 50 police cars had the best results* with the least amount of images. When trying to use even less, 50 images of each, the model began to become worse with a validation accuracy of at the time of the last epoch. 50 images of each seems to be the sweet spot for this binary classification. However, running more epochs could easily lead to better results

## Future Plans
This project was really simple, if I were to add onto this project, I would go about changing the data. Instead of having a singular car in an image and determing if it was a police car or not, I would like to have an image with many cars and determine if it contains a police car. I would then go one step beyond that and use object detection to determine where a police car is. With that being done, instead of the obvious police cars, targeting specfic models of cars could be used incase of amber alerts or other helpful concepts. In regards to this project, l believe looking more into the information like the loss and recall, would give much more depth then what I have taled about. This could include going much more indepth regarding the plots shown.

# Downloading Data
Both datasets were gathered on roboflow

-Police Cars: https://app.roboflow.com/smithb23/police_cars-5x7fo/1   2.87 MB
-Cars: https://app.roboflow.com/smithb23/vehicle-classification-eapcd-al8dr/2 264 MB

# Notebook 
The Car_Pro_Computer_Vision.ipynb file holds everything I did. As of the moment, the neatness could be worked on as well as some more comments, but using the file should note be difficult.
