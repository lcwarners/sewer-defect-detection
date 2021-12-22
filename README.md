# Sewer Defect Automated Detection Using Machine Learning
### CS-433 Machine Learning project 2

Within the framework of the EPFL Machine Learning course, we collaborated
with the city of lausanne to automate the recognition of defects in
sewer pipes. To this goal we trained the neural networks RESNet50,
EfficientNetB1 and EfficientNetB7 on CCTV videos from the pipes. Our
purpose was to detect two main defects, namely roots and cracks.
Data augmentation, comparison of these three models, and active 
learning were implemented.

___Please note that we were unable to provide the data on which this mode
was trained and evaluated due to its confidential nature.___

## Librairies used

Before running any code, make sure you have all the librairies needed.
If not, open a terminal and run
`pip3 install $name_of_the_package`

* The neural networks are implemented via _tensorflow_.
* For plots we will need _matplotlib_, _sklearn_ and _itertools_.
* To deal with arrays, _numpy_ is needed.
* To handle videos files, _os_ and _moviepy_ are used.

## Architecture

### Comparison and optimisation

The three notebooks in this directory were used to compare model
performance of ResNet50, EfficientNetB1, and EfficientNetB7,
immediately clear from the names of the notebooks. All notebooks work the
same way: the batches are generated, the model is downloaded
and dense layers appended, and the original model is frozen such that it
functions as feature extractor. The added dense layers are trained using
the train data and validated with the valid batches.

### Fine tuning

EfficientNetB1 was finetuned using this notebook. Transfer learning was
applied first, subsequently the last 10 layers were unfrozen (excepting
batch normalisation). The training is implemented using early stopping and
the weights are saved for later use.

### prediction and visualisation

In this notebook, the weights are loaded and used to generate predictions
on a test batch of 600 images. The accuracy is calculated and the wrongly
classified images are inspected.

### analyze video 

This notebook is most important for direct application. It takes a video as
input and outputs a list of timestamps in which the model detects a defect
(either fissure or racine). 

### active learning
