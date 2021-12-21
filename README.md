# sewer-defect-detection
CS-433 Machine Learning project 2

Before running any code, make sure you have all the dependencies needed installed.
If not, open a terminal and run
> pip3 install $name_of_the_package
The neural networks are implemented via tensorflow.
For plots we will need matplotlib, sklearn.metrics and itertools.
To deal with arrays, numpy is needed.
To handle videos files, os and moviepy are used.

## Directories
# comparison and optimisation
The three notebooks in these directories were used to compare model performance of ResNet50, EfficientNetB1, and EfficientNetB7, immediately clear from the names of the notebooks. The working of the notebooks is identical: the batches are generated, the model is downloaded and dense layers appended, and the original model is frozen such that it functions as feature extractor. The added dense layers are trained using the train data and validated with the valid batches.

