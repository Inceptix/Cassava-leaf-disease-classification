# Cassava Leaf Disease Classification Project Charter

## Problem Description

The cassava is a large starchy root that is commonly grown in tropical and subtropical climates. This large, cylindrical root grows beneath the ground and gathers nutrition from sunlight, captured by its large shrub like leaves that protrude.  Both the roots and leaves are not to be consumed raw, however once cooked, both parts of the plant become edible, and nutritious. The leaves provide protein to humans, and the stalks can even be dried into hay to be fed to livestock.

Largely grown in Africa, this crop is estimated to be grown in 80% of households farms and gardens in the Sub-Saharan area [2].  Outside of Africa, cassava is also grown in a number of countries in Asia and Latin America such as, the Philippines, Cambodia, Indonesia, the Domican Republic, Venezuela, Guatemala, and many more.  With so much of the world growing the crop, it has risen to become one of the world's largest sources of carbohydrates, with over half of a billion people relying on it [1].

Cassava is a resilient plant, and can withstand drought and poor soil conditions.  However, it is not invulnerable.  This plant is susceptible to damage caused by insects and disease, and for the purposes of this project we will be looking into damage caused by four different diseases, namely; Cassava Bacterial Blight(CBB), Cassava Brown Streak Disease(CBSD) Cassava Green Mottle(CGM), and Cassava Mosaic Disease(CMD).

All of these diseases lead to a loss in crop yield, causing food shortages and malnutrition in many small villages.  To address this issue the government has offered help, however the help relies on government officials doing in-person inspections, which is both time consuming and expensive.

To remedy this issue, Markerere University AI Lab has presented the challenge of using data science tactics to help identify the diseases in a cheaper and more time effective manner.  To aid the solution, they have given a library of over 21,000 images of Cassava leaves, both infected and healthy. These images are labeled with the corresponding affliction, or healthy if no affliction is present.
Thus, the question we will be responding to is this: Can we use computer vision techniques to effectively identify the diseases present in the Cassava plant?

## Scope
In this project, we intend to ask the question, can we use computer vision to aid in early detection and classification of diseases in the Cassava leaves?

To answer this question, we must first understand the data set, and the nature of the problem.  As the data set contains a large amount of classified images, we will be working in a supervised learning situation.  This is good as it will allow us to create better metrics for measuring the effectiveness of our model.

The data set also contains 5 categories, 4 different diseases and a healthy version. This means our question is in the form of a classification problem.  This gives us a few options to consider when trying to build an effective model.  Our base model will be based on flattening the data into vectors, and running it through a basic neural network.

Once we have explored our data set, and created an effective baseline we can begin exploring techniques used by other contestants to find and apply techniques that may be helpful to increasing our accuracy.  Another opportunity to increase accuracy could come from adjusting the parameters of our model.  We may even explore Convolutional Neural Networks(CNN) to see if they could produce better results in this scenario. We are particularly interested in exploring pre-trained neural networks.

By the end of our project, we hope to have a model that can produce accurate classification of each of the four diseases present in the data set. Having an accurate model can help farmers quickly identify a diseased plant. Being able to identify the diseased plant and the disease specifically, they can take the correct steps to save the crops or harvest early and get rid of the diseased plants.


## Personnel
* Project Lead
  * Dodge Hill
* Project Mentors
	* Dr. Abha Belorkar
	* Sam Black
* Data Scientists
	* Dodge Hill
	* Jonathan Oberst
	* Marinos Rrapaj
	* Thuc Duong
	
## Metrics
* What are the qualitative objectives?
  * Help farmers save crops by classifying images of cassava plants as healthy or diseased
* What is a quantifiable metric?
  * Check the accuracy of our model at predicting if a leaf is healthy or not
  * Check the accuracy of predicting the correct disease if the model predicts a leaf does have a disease
  * Check the accuracy of our model against other more baseline image sets such as ImageNet
* What is the baseline (current) value of the metric? 
  * The current top score aboard the leaderboard predicts correctly with a score of 0.911
* How will we measure the metric? 
  * Categorical accuracy
  * Precision recall
  * Confusion matrices

## Exploratory Data Analysis: 
In this competition, we have 5 classes: 4 diseases and 1 healthy.
  
**Class 0: Cassava Bacterial Blight (CBB)**
  * Small lesions on viens, spread to turn leaf brown, yellow ring around lesions
    * Treatment: prune infected parts if caught early, otherwise uproot and burn
  * ![alt text](<Images/Class_0.png>)

**Class 1: Cassava Brown Streak Disease (CBSD)**
  * Brown streaks on leaves
    * Treatment: detected early - harvest early, otherwise remove and destroy plant
  * ![alt text](<Images/Class_1.png>)

**Class 2: Cassava Green Mottle (CGM)**
  * Yellow dots on the leaves
    * Treatment: uproot and destroy
  * ![alt text](<Images/Class_2.png>)

**Class 3: Cassava Mosaic Disease (CMD)**
  * White/discoloration on leaves, smaller leaf size
    * Treatment: uproot them, don’t replant from the infected
  * ![alt text](<Images/Class_3.png>)

**Class 4: Healthy**
  * ![alt text](<Images/Class_4.png>)

**Label distribution of the data set:**
  * ![alt text](<Images/Label_Distribution.png>)

## Plan
### Timeline: 
![alt text](<Images/Timeline.png>)

### Phase 1:
* Big goals:
  * Exploring existing solutions to the problem 
  * Data cleaning and processing 
  * Evaluating performance of baseline model
	
* Project Charter due Feb 8th - this document
* Project Demo due Feb 18th
  * In this demo, we will demonstrate to the class our baseline model.
  * However, we plan on getting a baseline model earlier (by Feb 12th) because the competition ends Feb 18th.
  * The team should present the baseline version of their project that has been through at least one iteration of the complete data science project lifecycle (business understanding → data acquisition → modeling →  deployment → performance evaluation).
  * More EDA, basic understanding of baseline models, accuracy, plan on improving the model, what did we not try in the model.
  * Explore existing solutions to the problem (check out other notebooks on Kaggle)
  * Have a firm understanding of image classification basics by checking out Sam’s getting started resources (https://cassavavirus.atlassian.net/browse/CAS-12?atlOrigin=eyJpIjoiNTA0ZGFkZDllMzEyNDg4ZDg1Njg1NmFhOGFiZWE3M2MiLCJwIjoiaiJ9)
  * Data cleaning + processing (the imbalance of class needs to be resolved) -> Check out image augmentation. 
  * Get together and evaluate the performance of all of our baseline models.
  * Make a nice presentation with all of our findings + challenges + things to improve + plan for phase 2. 

### Phase 2:
* Big goals:
  * Experimenting with feature engineering 
  * Experimenting with alternative ML methods 
  * Evaluating performance of new models
* Bi-monthly Progress Report
* Project Demo
* Revise Project Charter

### Phase 3: 
* Big goals
  * Improving over the Phase 2 model 
  * Creating an interactive dashboard
* Data Report
* Model Report
* Performance Report
* Project Demo
* Interactive Dashboard



## Architecture
* Data
  * What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)
    * Raw images of cassava leaves with labels taken from Kaggle
    * Potentially pre-train the model on other image datasets such as ImageNet 



* Data movement from on-prem to Azure using ADF or other data movement tools (Azcopy, EventHub etc.) to move either
  * all the data, 
  * after some pre-aggregation on-prem,
  * Sampled data enough for modeling 

* What tools and data storage/analytics resources will be used in the solution e.g.,
  * Python for feature construction, aggregation and sampling
  * Keras, TensorFlow for modeling and web service operationalization

* How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.
  * How will the customer use the model results to make decisions
    * The “customer”, farmers of cassava, will use the model to quickly predict which plants may be sick in order to save more crops
  * Data movement pipeline in production
    * “Customer” can upload images of their leaves and our model will predict what if the leaf is healthy or diseased, and if diseased, what disease it has


## Communication
* How will we keep in touch? Weekly meetings?
	* Currently running a Discord server which enables us to talk to each other very quickly and set up meetings as needed.
	* Discord chat functionality also allows us to chat about anything going on with the project at any time.
	* Github commit messages are an easy way of checking what work was done to prevent overlapping.
	* Jira task completions
* Who are the contact persons on both sides?
	* Project development contacts: Thuc Duong(tug98850@temple.edu), Dodge Hill(tuh33009@temple.edu), Jonathan Oberst(tug93898@temple.edu), Marinos Rrapaj(tuf61948@temple.edu)
	* Shareholder contacts: Abha Belorkar, Sam Black

## Work Cited
[1] “Cassava (Manioc).” Cassava (Manioc) | Diseases and Pests, Description, Uses, Propagation, plantvillage.psu.edu/topics/cassava-manioc/infos. 

[2] “Cassava Leaf Disease Classification.” Kaggle, 2020, www.kaggle.com/c/cassava-leaf-disease-classification. 

[3] “EXECUTIVE SUMMARY.” Global Cassava Market Study, www.fao.org/3/y5287e/y5287e04.htm. 

[4] Ihelon. “Cassava Leaf Disease - Exploratory Data Analysis.” Kaggle, Kaggle, 28 Nov. 2020, www.kaggle.com/ihelon/cassava-leaf-disease-exploratory-data-analysis. 

