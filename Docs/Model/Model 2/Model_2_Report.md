# Model Report

## 1. Original Base Model
Our original model was a CNN that utilized an image adjustment layer to normalize the images, before giving them to a pre-trained Resnet50 layer, and a very basic exponential decay learning rate scheduler.  On top of this, we added the following layers; GlobalAveragePooling, Dense(16 ,relu), Dense(8,relu), and finally Dense(5,relu) that gave us our prediction. In an attempt to prevent overfitting, we placed a dropout layer between the Dense(16) and Dense(8) layers.  For scoring, the model used spare categorical entropy.

This model was our teams first attempt at making predictions with the competitions dataset, and was fairly basic.  We continued to adjust the model and attempt to make improvements.  Adjusting the learning rate scheduler, and the dropout value, however the best we achieved was (on average) 60% validation accuracy.

![alt text](</Docs/Project/Images/Model_2_Report_Images/confusion_matrix_original_model.png>)

As seen in the confusion matrix above, our model had an overfitting issue. Most likely caused by 1) a bias in the training data to contain mostly class 3 (Cassava Mosaic Disease), and 2) over usage of Dense layers.

## 2. Switch to EfficientNet
The next step in tweaking the model was switching our pretrained layer from ResNet50, to EffecientNet (EffecientNetB6 specifically), using the “Noisy Student” data set for pretraining. This gave us the following results:


Interestingly this fixed an issue we had.  Our previous model clumped all of it’s predictions into the final two categories(3:Cassava Mosaic Disease, 4:Healthy). 
Next, we had to address the accuracy issue.  To do this, Dodge started by readjusting the model.  He adjusted the dropout layer, and edited the image adjustment layer to be better suited for EfficientNetB6. From here we obtained:


Our next step was to adjust the learning rate scheduler(LR).  This was just using a basic exponential decay scheduler, and Thuc recommended switching to a Cosine Decay LR.  This had profound effects, and our model was able to perform as follows:


From the above graphics you can see that our model was performing better, but was still over fitting.  We spoke in class with Dr. Belorkar and Sam Black, who gave us many suggestions for addressing this, one major suggestion was to decrease the image size.

## 3. Introduction of Augmentations

Next on the agenda was for the team to address the overfitting issues.  This meant introducing the other team members' work. We began working on integrating the base model with a notebook created by Marinos that includes albumentation(augmentation techniques). This meant dropping the TFRecords and TPU’s we were previously using and switching to Pandas DataFrames to interface with the images.  After sometime we were able to produce a model with the following features:
Cross validation
The introduction of cross validation would help us address the datasets imbalance.  Paired with the augmentation techniques this was able to greatly improve our models performance.
Basic Augmentation Techniques(Crop, Transpose, Horizontal and Vertical Flips, Hue/Brightness Adjustments, etc)
These basic techniques allowed us to adjust the images so that the cross validation did not simply feed the model repeat images between folds.  Augmentations also help the model become “more general” which serves to improve the model's validation accuracy.
CutMix
This is a more advanced augmentation technique that combines the methodology of cutout and mixup. Cutout simply removes part of the image and replaces them with black squares. 
This does help in increasing the generalization of the model but also effectively cuts down on the training sample per image since part of the image is not being analyzed. Mixup also introduces another set of problems. It produces images that are so mutated they do not look like the training set anymore. They are a mixture of two overlapping images which wouldn’t normally exist. 
Cutmix takes properties from both of these techniques but keeps only the beneficial parts. It removes part of the image and then adds another image to the part removed. At the same time it also changes the labels based on the amount of pixels present in the image per label. 
One final change to note was that the model now used accuracy as our metric.  This was to fit the competitions scoring model.

## 4. Refinement and Finished Model

At this point we had a model that was functioning very well, and was posting very good accuracy scores on the validation set (around 85%).  We began with exploring other possible techniques for increasing performance.
Dropped CutMix
Introduced to help keep our model more general and prevent overfitting, we removed it in an attempt to see its effects on the model's performance on the validation data.  However, after removing it, it appeared that had no effect on increasing the validation accuracy, so we decided to remove it entirely.
Denoising the Data Labels
Since the images were crowd-sourced, they were prone to labeling or photographic errors. Some of the photos were not very clear on what label they were and some did not even contain an image of a leaf.
We performed 5-fold cross validation to retrieve the out-of-fold accuracy for each fold as the baseline for gauging how much we can improve if we were to remove certain labels that were deemed as ‘mis-labeled’.
For each fold, we save the out-of-fold accuracy, the corresponding validation set and the model’s weights.
Then, for each fold, we find the corresponding model’s weights, perform some augmentation (called TTA or Test Time Augmentation) to the corresponding validation set to gain better generalization, and fit the model on that validation set.
During TTA, we will duplicate the original image and perform augmentation. Then, we get the model to aggregate predictions across those images, leading to better generalization (refer to figure below).

Our TTA and aggregation techniques produce the predicted label value to be >1 when we implement TTA twice. This pushes the max label value (100% confidence) to 2. If you implement 3x TTA, it will be 3 and so on. Also, this is a percentage estimated as a float. 
For each fold, after we make the predictions from the test-time augmented validation set to retrieve the following dataframe.

We then find the mis-predicted images (label != pred) with high confidence level (can be extracted from the value column from the above dataframe) that is above a certain threshold value. We remove the images. 
The intuition behind the above steps is if your model is already predicting wrong labels with very high confidence for those images. Then, it is unlikely to predict it correctly even if you continue to feed it the image for training (as it is unable to get it right anyway). By removing these noisy labels, it can then focus on the correct labels and strengthen its predictions on the clean data.
The formula for calculating the confidence level is:  confidence_level = (value / # of TTA) * 100
We set the threshold to be 80% and that removed about 2.24% of the images.
The average out-of-fold accuracy improved by 2% from 86% to 88% after the removal of those 2.24%, which demonstrates that the denoising process does contribute in improving the accuracy of our efficientnet model. 
Before Denoising

Removing some ‘noisy’ images

We removed about 2.2% of the images.

The above chart shows we removed labels 2 and 4 the most.
After Denoising

Attention Layer
We had desired, from the early stages of development, to have an understanding as to how our classifier was classifying with more nuance than just the predicted label that was returned from the “black-box.” The way we went about achieving this deeper level of understanding was by implementing an attention layer into our model alongside the efficientnet base. This was done with the hopes that we could visualize, in a human-understandable manner, how the computer was valuing different aspects of the image during the classification process.  The attention layer works in a recurrent manner, in which on top of the normal input -> model -> output manner that was already occurring, there was another branch in which an extra set of outputs was produced that was then re-fed the same image, in which case the attention layer would perform an action in which this extra outputs would be used to “glimpse” at specific parts of the image. This action of “glimpsing” was where the model was directing its attention, and was used to see exactly what the model was “looking” at.

