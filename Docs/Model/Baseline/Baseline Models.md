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

* Distribution Matrix

## Model Understanding

* Variable Importance (significance)

* Insight Derived from the Model



## Conclusion and Discussions for Next Steps

* Conclusion on Feasibility Assessment of the Machine Learning Task

* Discussion on Overfitting (If Applicable)

* What other Features Can Be Generated from the Current Data

* What other Relevant Data Sources Are Available to Help the Modeling