# Project Charter

## Problem Description

* The cassava is a large starchy root that is commonly grown in tropical and subtropical climates. This large, cylindrical root grows beneath the ground and gathers nutrition from sunlight, captured by its large shrub like leaves that protrude.  Both the roots and leaves are not to be consumed raw, however once cooked, both parts of the plant become edible, and nutritious. The leaves provide protein to humans, and the stalks can even be dried into hay to be fed to livestock.

Largely grown in Africa, this crop is estimated to be grown in 80% of households farms and gardens in the Sub-Saharan area(Markerere University AI Lab Cassava Leaf Disease Classification).  Outside of Africa, cassava is also grown in a number of countries in Asia and Latin America such as, the Philippines, Cambodia, Indonesia, the Domican Republic, Venezuela, Guatemala, and many more.  With so much of the world growing the crop, it has risen to become one of the world's largest sources of carbohydrates, with over half of a billion people relying on it (Cassava (manioc) plantvillage.psu).

Cassava is a resilient plant, and can withstand drought and poor soil conditions.  However, it is not invulnerable.  This plant is susceptible to damage caused by insects and disease, and for the purposes of this project we will be looking into damage caused by four different diseases, namely; Cassava Bacterial Blight(CBB), Cassava Brown Streak Disease(CBSD) Cassava Green Mottle(CGM), and Cassava Mosaic Disease(CMD).

All of these diseases lead to a loss in crop yield, causing food shortages and malnutrition in many small villages.  To address this issue the government has offered help, however the help relies on government officials doing in person inspections, which is both time consuming and expensive.

To remedy this issue, Markerere University AI Lab has presented the challenge of using data science tactics to help identify the diseases in a cheaper and more time effective manner.  To aid in the solution they have given a library of over 21,000 images of Cassava leaves, both infected and healthy. These images are labeled with the corresponding affliction, or healthy if no affliction is present.

Thus the question we will be responding to is this, can we use computer vision techniques to effectively identify the diseases present in the Cassava plant?


## Scope
* In this project we intend to ask the question, can we use computer vision to aid in early detection and classification of diseases in the Cassava leaves?
To answer this question, we must first understand the data set, and the nature of the problem.  As the data set contains a large amount of classified images, we will be working in a supervised learning situation.  This is good as it will allow us to create better metrics for measuring the effectiveness of our model.

The data set also contains 5 categories, 4 different diseases and a healthy version. This means our question is in the form of a classification problem.  This gives us a few options to consider when trying to build an effective model.  Our base model will be based on flattening the data into vectors, and running it through a basic neural network.

Once we have explored our data set, and created an effective baseline we can begin exploring techniques used by other contestants to find and apply techniques that may be helpful to increasing our accuracy.  Another opportunity to increase accuracy could come from adjusting the parameters of our model.  We may even explore Convolutional Neural Networks(CNN) to see if they could produce better results in this scenario. One area I am particularly interested in exploring is that of pre-trained neural networks.

By the end of our project we hope to have a model that can produce accurate classification of each of the four diseases present in the data set. Having an accurate model can help farmers quickly identify a diseased plant. Being able to identify the diseased plant and the disease specifically they can take the correct steps to save the crops or harvest early and get rid of the diseased plants.


## Personnel
* Project Lead
	* Dr. Abha Belorkar
	* Sam Black
* Data Scientists
	* Dodge Hill
	* Jonathan Oberst
	* Marinos Rrapaj
	* Thuc Duong
	
## Metrics
* What are the qualitative objectives? (e.g. reduce user churn)
* What is a quantifiable metric  (e.g. reduce the fraction of users with 4-week inactivity)
* Quantify what improvement in the values of the metrics are useful for the customer scenario (e.g. reduce the  fraction of users with 4-week inactivity by 20%) 
* What is the baseline (current) value of the metric? (e.g. current fraction of users with 4-week inactivity = 60%)
* How will we measure the metric? (e.g. A/B test on a specified subset for a specified period; or comparison of performance after implementation to baseline)

## Plan
* Phases (milestones), timeline, short description of what we'll do in each phase.

## Architecture
* Data
  * What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)
* Data movement from on-prem to Azure using ADF or other data movement tools (Azcopy, EventHub etc.) to move either
  * all the data, 
  * after some pre-aggregation on-prem,
  * Sampled data enough for modeling 

* What tools and data storage/analytics resources will be used in the solution e.g.,
  * ASA for stream aggregation
  * HDI/Hive/R/Python for feature construction, aggregation and sampling
  * AzureML for modeling and web service operationalization
* How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.
  * How will the customer use the model results to make decisions
  * Data movement pipeline in production
  * Make a 1 slide diagram showing the end to end data flow and decision architecture
    * If there is a substantial change in the customer's business workflow, make a before/after diagram showing the data flow.

## Communication
* How will we keep in touch? Weekly meetings?
	* Currently running a Discord server which enables us to talk to each other very quickly and set up meetings as needed.
	* Discord chat functionality also allows us to chat about anything going on with the project at any time.
	* Github commit messages are an easy way of checking what work was done to prevent overlapping.
	* Jira task completions
* Who are the contact persons on both sides?
	* Project development contacts: Thuc Duong(tug98850@temple.edu), Dodge Hill(tuh33009@temple.edu), Jonathan Oberst(tug93898@temple.edu), Marinos Rrapaj(tuf61948@temple.edu)
	* Shareholder contacts: Abha Belorkar, Sam Black
