# Baseline Model Report

_Baseline model is the the model a data scientist would train and evaluate quickly after he/she has the first (preliminary) feature set ready for the machine learning modeling. Through building the baseline model, the data scientist can have a quick assessment of the feasibility of the machine learning task._

When applicable, the Automated Modeling and Reporting utility developed by TDSP team of Microsoft is employed to build the baseline models quickly. The baseline model report is generated from this utility easily. 

> If using the Automated Modeling and Reporting tool, most of the sections below will be generated automatically from this tool. 

## Analytic Approach
* What is target definition?
	* 1 healthy as Label 4
	* 4 different diseases:
		* Cassava Bacterial Blight as Label 0
		* Cassava Brown Streak Disease as Label 1
		* Cassava Green Mottle as Label 2
		* Cassava Mosaic Disease as Label 3

* What are inputs (description)?
	+ TFRecords of 20,000 images with labels of 0,1,2,3,4.
* What kind of model was built?
	+ A CNN with a pre-trained model called RESNET-50 was built on top of it.

## Model Description

* Models and Parameters
	+ RESENET-50 as our pre-trained baseline model before we add a few layer to it.


	* Description or images of data flow graph
		* All TFrecord files -> load_dataset -> read_tfrecord -> decode_image -> get the actual image and its label -> Feed it into the base model.
	* What learner(s) were used?
	* Learner hyper-parameters
		* We use SparseCategoricalCrossentropy as a loss metric when compiling the function because there are two or more label classes and the labels are provided as integers.
		* We use the standard Adam optimizer for Keras learning scheduler with some default parameters for the learning rate. 


## Results (Model Performance)
* Confusion Matrix
	* Our main way of evaluating our model is by conufsion matrix.  This allows us to understand the missclassifications, and attemtpt to resolve them 

* Distribution Matrix
	* Used as a tool to show the actual number of each type of classification within the training data

## Model Understanding

* Insight Derived from the Model
	* Importantly from the model we can see the need to address "noise." The images are not at all standardized, and our belief is that our model is having a hard time seeing past this noise.  Finding a way to help the model give attention to only leaves/the subject of the image, and not the background, should help us increase accuracy.


## Conclusion and Discussions for Next Steps

* Conclusion on Feasibility Assessment of the Machine Learning Task
	* Our problem seems to have been attacked with relative ease by others in the field, but our model stills needs a lot fo work.  As it stands right now, the next steps will prove to answer the feasibilty of this problem.  Right now, without some form of attention mechanism, or anotehr form of data augmentation, I do not see the model performing much better. 

* What other Relevant Data Sources Are Available to Help the Modeling
	* Sources we are using include a lot of otehr Kaggle posts, as many users have successful models using techniques we have yet to implement.
