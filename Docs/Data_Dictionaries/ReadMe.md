### Data Dictionaries
The data represents cassava leave images. Each leaf is either healthy or infected with one of several diseases that cause material harm to the food supply of many African countries.

## Files

**[train/test]\_images** - the image files. In .jpg format.

Below is an example image. 

![alt text](</Docs/Project/Images/Class_0.png>)

**train.csv**

  image_id - the image file name.

  label - the ID code for the disease.

**sample_submission.csv** - A properly formatted sample submission, given the disclosed test set content.

  image_id - the image file name.

  label - the predicted ID code for the disease.

**[train/test]\_tfrecords** - the image files in tfrecord format.

**label_num_to_disease_map.json** - The mapping between each disease code and the real disease name.

## The different classes and their images
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