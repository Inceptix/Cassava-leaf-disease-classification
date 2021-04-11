## Performance Report

## 1. Model Evolution Summary

### Phase 1

* Key Features: 
    * ResNet-50 pre trained layer.
    
    * Effective learning rate scheduler.

* Drawbacks/Issues: 
    * Over fitting
    
    * No augmentation techniques to address imbalance in data set.

* Average Validation Accuracy: 60%


### Phase 2

* Key Features: 
    * Switched from sparse categorical cross entropy, to accuracy for our model’s evaluation metric
    * Removed ResNet-50, introduced EfficientNetB6 pretrained layer
    * Use NoisyStudent data set for pretraining
    * We trained the models on raw images rather than using TFRecords.
    * Introduced image augmentation through the use of Albumentations
    * Cross Validation
    * CutMix image augmentation techniques

* Drawbacks/Issues:
    * Slow
    * Learning rate scheduler not as effective as it could be 
    * Overfitting
    * Issues with confusion matrix


* Average Validation Accuracy: 85%

### Phase 3

* Key Features:
    * Final Model
    * Cross Validation
    * Label denoising techniques
    * Attention Mechanisms for visualization
    * EfficientNetB4 pre trained layer
    * Image augmentation, but no more CutMix
    * Reintroduction of confusion matrix

* Drawbacks/Issues:
    * Slowest model yet (remedied by Temple HPC)

* Average Validation Accuracy: 88%


## 2. Metrics
The competition calls for accuracy as the main metric for evaluating the model.

* a) Phase 1
    * i) Sparse Categorical Cross Entropy
        * This metric produces a single value (the certainty of the models prediction) for the category it believed the image was.
        
        * It works similarly enough to accuracy and allows us to produce a confusion matrix to evaluate the model.
        
        * This evaluation method is also good for when the categories are mutually exclusive, which is true in our case.
* b) Phase 2
    * i) Accuracy
        * Changing the model led me to change the evaluation metric to be the same as the required metric for the test.
        
        * Simple metric, gives the accuracy by just comparing the total number of correct predictions to the total number of examples.
* c) Phase 3
    * i) Same as Phase 2

## 3. Performance Summary 

a) Phase 1

![alt text](</Docs/Project/Images/Performance_Report/Performance_Report_Phase_1.png>)
        

In phase one we had issues with the model overfitting.  Due to an imbalance in the dataset, the model tended to classify most images at class 3, which has the label Cassava Mosaic Disease.

b) Phase 2

![alt text](</Docs/Project/Images/Performance_Report/Performance_Report_Phase_2.png>)

In phase 2 we continued to combat overfitting, but this was quickly addressed with the switch to EfficientNet and noisy-student as pre-trained weights. Our model no longer classifies most images as class 3.

The overfitting seen present in the graph was due to a lack of image augmentation techniques that we later introduced on our dataset to help keep our model general.

The only issue with the switch required adjusting the learning rate scheduler.

c) Phase 3
    
![alt text](</Docs/Project/Images/Performance_Report/Performance_Report_Phase_3.png>)

Our final model produces graphs as such.  Our learning rate scheduler is still not perfect.

With the introduction of denoising techniques, our model achieves an average accuracy of 88% for out-of-fold accuracy.
