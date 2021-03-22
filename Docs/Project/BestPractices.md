# Best Practices In Data Science

Team: Thuc Duong, Dodge Hill, Marinos Rrapaj, Jonathan Oberst

## Technical

***Distribution***

* Our classified data does not have an even split between all of the categories. 
* Since our data are images, we don’t need to have summary metrics like mean or median but we can plot the distribution of the classes and the red, green, blue channels to extract insights of how our models might distinguish between the different classifications.
* We can use the distribution to see what classes are in greater amounts and use data augmentation techniques to create more training examples of those classes that are not as available.
*  Some of the images were observed to be misclassified from our EDA so we implemented a system that removes images that the system believes to have high probability of being mis-labeled in the first place. By removing these mis-labeled images, we hope to achieve better training data for our model. 

***Slicing***
* “Slicing means separating your data into subgroups and looking at metric values for each subgroup separately.”
* Slicing the pixel data into subsections. 
* This is dependent on the architecture of our models since some models might slice up the images in different ways or even take the whole image for training.
* Slicing as in looking at how the model performs against classifying each class like what’s the accuracy of classifying a leaf with disease X compared to disease Y. 
* This can also be helpful when thinking about choosing augmentation techniques as we can try out different subgroups of augmentation techniques and see how that improves the model’s accuracy. 
* We have also been using canny-edge detection to observe how the models are looking at the images and where they are focusing their attention on.

***Look at examples***
* “It’s nearly impossible to produce working code of any complexity without performing this step. Your analysis is abstracting away many details from the underlying data to produce useful summaries.”
* Since these are images, it’s great to look at it to identify the physical attributes.
* This will increase the confidence that we have in our analysis.
* Kaggle Notebooks have been an excellent source of information and inspiration for our project.  As we work to implement new features we are often able to find notebooks from others who have implemented similar features.

***Consistency Over Time***
* “Just because a particular day or set of days is an outlier does not mean you should discard the corresponding data. Use the data as a hook to determine a causal reason why that day or days is different before you discard it.”
* There are many images in the data set that are not consistent with the rest.  Many of them contain more than just the leaves we are concerned with.  Rather than just discarding these images, we are working on a way to make sure they are labeled correctly.  We are also working on using attention mechanisms to make sure the model is focusing on the right part of the image.
* We have been utilizing data augmentation techniques to increase the size and diversity of our training sets. 

## Process

***Separate validation, description and evaluation***

* The data that we have was gathered by those in the farming community. We do believe the data to be self-consistent and that it was collected correctly although some images might appear higher quality than others. 
* However, some of these images are prone to be mis-labeled and we worked on removing these images with high probability of being mis-labeled. 
* The data consists of images of healthy and diseased plants. Each of the diseases have been already identified and categorized as such to help us solve the classification issue when looking at new plants which carry disease
* The data itself doesn’t give any evaluation but its use comes in being able to identify other plants which are diseases and acting early. Usually, the earlier a sick plant can be identified, losses can be cut much faster and new plants can replace those ones.

***Standard first, custom second***
* “When looking at new features and new data, it's particularly tempting to jump right into the metrics that are new or special for this new feature. However, you should always look at standard metrics first, even if you expect them to change. For example, when adding a new universal block to the page, make sure you understand the impact on standard metrics like “clicks on web results” before diving into the custom metrics about this new result.”
* There are ways we can augment the data using other images which are not included in the original dataset. However, the best practice is to first go through the process of creating a model that works on the standard data and metrics; being able to identify the disease given a specific plant.
* Our base model was trained on the original data set we were given, and we maximize the performance of our model.  Now we are attempting to introduce augmentation techniques to increase the performance.

***Check for reproducibility***
* Usually classification data comes with testing data to check against. So sometimes this can lead to a model overfitting because of small dataset or other reasons. 
* We use 5-fold stratified cross validation technique to improve the accuracy and predictive confidence of the model by retrieving out-of-fold accuracy. With out-of-fold accuracies, we are able to estimate the ability of different models on unseen data, they help us to remove the noisy labels and also improve the accuracy of the models. 

***New metrics should be applied to old data/features first***
* When coming across new data it is important to develop some new metrics, however, it is important to first check those metrics against the old data and features to make sure that the model still makes sense because new metrics are meant to enhance and not completely change.

## Mindset 

***Data analysis starts with questions, not data or a technique***

* The data gathered by the Kaggle competition is already well formatted for us to use. What we must do first is see what it is the data is trying to tell us, coming from a place where we have limited knowledge about Cassava leaves and image detection. We have to figure out what it is we don’t know, and we figure that out by asking questions, which will eventually get us closer to the truth. As well, it is important to look around at what others have already discovered from the dataset. Using other people’s insights will lead to us being able to draw our own conclusions quicker and with greater accuracy.

* Our analysis was accomplished by first asking ourselves what the data represented. We went about learning about cassava and how these diseases present themselves. Once we understood a little as to what the data represented, we went about trying to ask questions that got at how the actual data manifested the representations 

***Correlation != Causation***

* As we work on our model, we have to be careful of confusing results we are getting with the underlying truths that they represent. For example, many of the diseases presented in our problem have similar visible symptoms. We have to be careful that if our classifier is getting more accurate at predicting right from wrong in the early stages of developing our model that it is because the classifier understands those tiny differences and not because our classifier is making incorrect assumptions that will hurt us in the long run

* We have taken steps to try and stay in front of this, such as using confusion matrices to see how our model is classifying images at each iteration of our project as well as denoising the data to limit the amount of noise that could create false patterns within our model.

***Share with peers first, external consumers second***

* As a team of four, we will need to make sure our communication and teamwork is strong if we are to achieve our maximum potential on this project. Prior to any of us making any long term changes or committing a lot of time to specific ideas, we should first hash it out with the group as a whole to make sure the ideas at play are as fleshed out as they can be before we set off to tackle problems. Once things are agreed upon by the team, then we can look elsewhere for even more optimizations. 
We have had meetings on every day during the work week in order to keep each other posted and updated. This has led to good collaboration and help throughout the project. Whenever we can’t figure something out amongst ourselves, we then turn to outside resources for guidance.
	
***Expect and accept ignorance and mistakes***
* Heading into this project, individually we each lack major experience in both the realm of image classification as well as general botany. As we go about our project, we will inevitably make misguided assumptions and we have to be careful to allow ourselves to take a step back and admit when we are incorrect. As well, we have to be understanding when someone else within our group makes a mistake. 
* We have to understand that the best way to deal with a mistake is to understand that they happen, and that as a team we need to pool our minds to deal with it, learn from it, and move on.
* We have all been accepting of each other throughout the project. Everyone understands that sometimes errors are made and sometimes life gets in the way, but we fostered a healthy environment in which we can be okay with problems and work together to solve them.  
