# sewer defect detection
CS-433 Machine Learning project 2

Before running any code, make sure you have all the dependencies needed installed.
If not, open a terminal and run
> pip3 install $name_of_the_package
The neural networks are implemented via tensorflow.
For plots we will need matplotlib, sklearn.metrics and itertools.
To deal with arrays, numpy is needed.
To handle videos files, os and moviepy are used.

#### Please note that we were unable to provide the data on which this model was evaluated due to its confidential nature.

# directories
## comparison and optimisation
The three notebooks in these directories were used to compare model performance of ResNet50, EfficientNetB1, and EfficientNetB7, immediately clear from the names of the notebooks. The working of the notebooks is identical: the batches are generated, the model is downloaded and dense layers appended, and the original model is frozen such that it functions as feature extractor. The added dense layers are trained using the train data and validated with the valid batches.

## fine tuning
EfficientNetB1 was finetuned using this notebook. Transfer learning was applied first, subsequently the last 10 layers were unfrozen (excepting batch normalisation). The training is implemented using early stopping and the weights are saved for later use.

## prediction and visualisation
In this notebook, the weights are loaded and used to generate predictions on a test batch of 600 images. The accuracy is calculated and the wrongly classified images are inspected.

## analyze video 
This notebook is most important for direct application. It takes a video as input and outputs a list of timestamps in which the model detects a defect (either fissure or racine). 

## active learning
