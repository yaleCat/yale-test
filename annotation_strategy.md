
# Annotation strategy

## Multi-Class Classification

As for classification task, the annotation strageties are really depends on what kind of issue you want solve. We list down some most common ways for building annotation task:

### Annotation for baseline dataset
* Easiest way to create annotation task. After we get a baseline dataset with detection box, we just need to create 'Cleaning task' for each concept.
<img src="https://github.com/visenze/sense/blob/feature/notes/notes/images/data/detect_box.png" width=800>
* Create tagging task for those data annotated as 'FALSE' and the choices are all the tags under its concept group

### Cleaning task for confused images based on entropy
* Visualize the prediction result with TSNE plot
* Check whether traiing dataset are with corrupted labels by viewing if the training dataset neighbors are showing the similar pattern with the bad cases
* Predict the entire training dataset with the model and get the entropy value for each prediction
* Filter out the data with highest 10% entropy value (the percentage can vary according to the dataset)
* Create cleaning task for the filtered data and the cleaning class is the predicted tag
* Create tagging task for those data annotated as 'FALSE' and the choices are all the tags under its concept group

### Cleaning task for adding data based on keywords search
* 
* Review the annotation result and iterate the model with the new dataset

### Group cleaing task for badcase driven data coverage expansion based on visual search 
(Be careful of overfitting issue)
* Error analysis for the prediction result on product development dataset (How to do error analysis)
* Filter out thoses bad cases with data coverage issue
* Get search result from the existing search model online with relevant feature sets and enough reference size
* Create group cleaning task, in which each query url is the bad case url and the cleaning class is the groundtruth for the bad case image
* Create guideline to notice vendor that do not select the exact match and duplicate images during the annotation task to prevent overfiting to the product development dataset
* Review the annotation result and iterate the model with the new dataset

---
## Multi-Label Classification

### To be added




