### Data Dictionaries
The data represents cassava leave images. Each leaf is either healthy or infected with one of several diseases that cause material harm to the food supply of many African countries.

## Files

[train/test]\_images - the image files. The full set of test images will only be available to your notebook when it is submitted for scoring. Expect to see roughly 15,000 images in the test set.

![Cassava Images](https://www.kaggleusercontent.com/kf/48038133/eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0..q2Htz1rRGtBSHppj4EZN-Q.TJNNookByHOKLkyhX3HgYdF8tCNkisBeOuvUOwsEm9tXpOv85bovYy4s3o2f0cqvKymtdtCrnn7f7IDqogL9UKGTn6Zkl1zIupJqvijyH6zjVghTU6YDq-4OBFt3CXdHn3rccOJoQD59eEQd3Yxo_FGZJlnqXwtFqcWgCUg7FC3-sMbiFjMMslV8qsy7FmUhksXzhWpaqsvCumwuB6Nwu2YepCclGcjYqMpAgHLM3TKh-33yUcpz3qLVaLHBfamNpp8S1gZN9CEiroiH_QUCG-LkdJqWhJrmVNnVu_YMiVBdyOQwpkMt1OTgWgh5yudy7EVpSYsTTrqFrL7CyH66rVi-GPhBtLKwBsM4IAOJa2h_mH1rmuWRo-BHPeztAmuDO2tTrkVP7Z-y_QxgPkvjJkscZ7yDofaNBmhjX-HgvR9sIxLba9GeldVzEiuvk0DO0RErSMuL2f6pTtaSbbJxB53FpFDFlkvWm5P6mP8v2BNjUa7U2s9-DXvqmp7XoSPziHqfD87pQ0tGGYBgvJUIaehB3BQ3EebnWM72zyeYRTxH0vVoY0IYhNVD0b6tCqGxQOy_nHBm4Lx9tbfo-cQK6OpmPCYAsBj9T9ncgI9uUSuykrg9i9BFZpzwtgZI_3JnyZdJFFdkF32E_uueJIhyDM2ANXcPGpteLKUefsCkgqCTKqrTqwxVhA-tdidxqs65.bnuWpf754YRFPEsolSedcw/__results___files/__results___18_0.png)

**train.csv**

image_id - the image file name.

label - the ID code for the disease.

**sample_submission.csv** - A properly formatted sample submission, given the disclosed test set content.

image_id - the image file name.

label - the predicted ID code for the disease.

[train/test]\_tfrecords - the image files in tfrecord format.

label_num_to_disease_map.json - The mapping between each disease code and the real disease name.
