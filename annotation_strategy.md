
# Annotation strategy

## Multi-Class Classification

As for classification task, the annotation strageties are really depends on what kind of issue you want solve. We list down some most common ways for building annotation task:

### Cleaning task for adding data based on keywords search (for building baseline dataset)

* Easiest way to create annotation task. First we should prepare a keywords-concept dictionary.
* Use the dictionary to crawl data from sources such as  Google and Pinterest by iGragger
* Import the crawled dataset into Hydra Vision 
* Create Cleaning annotation task for each concept.

### Cleaning task for confused images based on entropy (for cleaning corrupted labels)
* Visualize the prediction result with TSNE plot
* Check whether traiing dataset are with corrupted labels by viewing if the training dataset neighbors are showing the similar pattern with the bad cases
-- tsne_example.jpg
* Predict the entire training dataset with the model and get the entropy value for each prediction
* Filter out the data with highest 10% entropy value (the percentage can be different based on the analysis)
-- entropy_formula.jpg
* Create cleaning task with its predicted tag of the selected data
* Create tagging task for those data annotated as 'FALSE' and the tag choices should be under its concept group
-- annotation_tagging_example.jpg



### Group cleaing task for badcase driven data coverage expansion based on visual search (for solving bad cases)
(Be careful of overfitting issue)
* Error analysis for the prediction result on product development dataset (How to do error analysis)
* Filter out thoses bad cases with data coverage issue
-- badcase_search_error_analysis.jpg
* Get search result from the existing search model online with relevant feature sets and enough reference size
-- badcase_search_dashboard_result.jpg
* Create group cleaning task, in which each query url is the bad case url and the cleaning class is the groundtruth for the bad case image
-- badcase_search_annotation.jpg
* Create guideline to notice vendor that do not select the exact match and duplicate images during the annotation task to prevent overfiting to the product development dataset
-- badcase_search_guidline.jpg
* Review the annotation result and iterate the model with the new dataset
-- badcase_search_happy.jpg





