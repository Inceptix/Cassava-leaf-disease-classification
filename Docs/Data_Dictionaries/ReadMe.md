# Data Dictionaries
The data represents cassava leave images. Each leaf is either healthy or infected with one of several diseases that cause material harm to the food supply of many African countries.

## <Files\>

[train/test]\_images the image files. The full set of test images will only be available to your notebook when it is submitted for scoring. Expect to see roughly 15,000 images in the test set.

**train.csv

image_id the image file name.

label the ID code for the disease.

**sample_submission.csv** A properly formatted sample submission, given the disclosed test set content.

image_id the image file name.

label the predicted ID code for the disease.

[train/test]\_tfrecords the image files in tfrecord format.

label_num_to_disease_map.json The mapping between each disease code and the real disease name.
