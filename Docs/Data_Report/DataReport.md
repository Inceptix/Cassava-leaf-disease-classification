# Data Report

## 1. EDA

In this competition, we have 5 classes: 4 diseases and 1 healthy.

### 0. Cassava Bacterial Blight (CBB)
Description: Small lesions on viens, spread to turn leaf brown, yellow ring around lesions
	Treatment: prune infected parts if caught early, otherwise uproot and burn
### 1. Cassava Brown Streak Disease (CBSD)
Description: Brown streaks on leaves
Treatment: detected early - harvest early, otherwise remove and destroy plant

### 2. Cassava Green Mottle (CGM)
Description: Yellow dots on the leaves
Treatment: uproot and destroy

### 3. Cassava Mosaic Disease (CMD)
Description: White/discoloration on leaves, smaller leaf size
Treatment: uproot them, don’t replant from the infected

### 4. Healthy

### Label distribution of the data set:

As seen from the graph above the data set had a clear distribution bias towards class 3 (Cassava Mosaic Disease).  This caused a massive overfitting issue, where our base model would classify most images into class 3.  This gave our model a higher than expected training accuracy around 80%, however, our validation accuracy was around 60%.

### Pixel distribution of the data set:
Each image in the data set is represented by 600x800 pixels of the standard RBG variety. Below is a distribution of how activated each channel is for the pixels within the dataset. The green channel is the most activated for the images followed by red and then green. 

## 2. Augmentations
We have made improvements to our data preparation pipeline by shifting over from using tf records to just using standard data frames. There was no good way of getting tf records to work well with the ablumentation library but because we really like what the library offers we decided to switch our model instead. Currently we are using pandas dataframes as well as tf.data datasets for our training data. With this in place the rest of the pipeline becomes pretty much plug-n-play. 
We define a modest transformation pipeline by passing the images through a random crop and resize function, transposition (switching the width and height), and horizontal and vertical flip function. Each of these have a 50% of being applied to the image. This sort of transformation pipeline helps a lot in augmenting our dataset since we were having problems with overfitting in the past. Below is an example of how the train dataset looks like after the first transformation. 

The next step of the transformation includes some convolutional techniques, such as slight color shifting, random brightness and contrast and small little cutouts in the image. This features as also shown in the image above. 
We found that by applying convolutional augmentations the model started to overfit less because it was better at looking at the image as whole when trying to classify it rather than focusing on smaller parts. 
Along the way we discovered even better ways to make our model better at generalizing through a technique called CutMix. Essentially, this takes parts of other images and layers them on top of each other interpolating them. The labels also get weighed and calculated. The results of the CutMix implementation are listed below.
 
## 3. Denoising
Since the images were crowd-sourced, they were prone to labeling or photographic errors. Some of the photos were not very clear on what label they were and some did not even contain an image of a leaf.

We performed 5-fold cross validation to retrieve the out-of-fold accuracy for each fold as the baseline for gauging how much we can improve if we were to remove certain labels that were deemed as ‘mis-labeled’.
For each fold, we save the out-of-fold accuracy, the corresponding validation set and the model’s weights.
Then, for each fold, we find the corresponding model’s weights, perform some augmentation (called TTA or Test Time Augmentation) to the corresponding validation set to gain better generalization, and fit the model on that validation set.
During TTA, we will duplicate the original image and perform augmentation. Then, we get the model to aggregate predictions across those images, leading to better generalization (refer to figure below).

Our TTA and aggregation techniques produce the predicted label value to be >1 when we implement TTA twice. This pushes the max label value (100% confidence) to 2. If you implement 3x TTA, it will be 3 and so on. Also, this is a percentage estimated as a float. 
For each fold, after we make the predictions from the test-time augmented validation set to retrieve the following dataframe.

We then find the mis-predicted images (label != pred) with high confidence level (can be extracted from the value column from the above dataframe) that are above a certain threshold value. We remove the images. 
The intuition behind the above steps is if your model is already predicting wrong labels with very high confidence for those images. Then, it is unlikely to predict it correctly even if you continue to feed it the image for training (as it is unable to get it right anyway). By removing these noisy labels, it can then focus on the correct labels and strengthen its predictions on the clean data.
The formula for calculating the confidence level is:  confidence_level = (value / # of TTA) * 100
We set the confidence threshold to be 80% and that removed about 2.24% of the images.
The average out-of-fold accuracy improved by 2% from 86% to 88% after the removal of those 2.24%, which demonstrates that the denoising process does contribute in improving the accuracy of our efficientnet model. 
Before Denoising

Removing some ‘noisy’ images

We removed about 2.2% of the images.

The above chart shows we removed labels 2 and 4 the most.
After Denoising


## 4. Data Summary

That data set was crowd sourced from farmers and families that rely on the Cassava as a main source of carbohydrates.  These images were then labeled by professionals. This helped create a large and diverse data set very quickly, however it also created a very noisy dataset, as there was no standardization of images, and most of the images contained multiple leaves, different parts of the plants and sometimes pictures of the farms themselves.

This makes it difficult for the model to perform well, and requires us to introduce generalization techniques such as image augmentation and even denoising techniques.
