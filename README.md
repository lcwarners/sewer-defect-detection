# Sewer Defect Automated Detection Using Machine Learning
### CS-433 Machine Learning project 2

Within the framework of the EPFL Machine Learning course, we collaborated
with the city of Lausanne to automate the recognition of defects in
sewer pipes. To this goal we trained the neural networks _ResNet50_,
_EfficientNetB1_ and _EfficientNetB7_ on CCTV videos from the pipes. Our
purpose was to detect two main defects, namely roots and cracks.
Data augmentation, comparison of these three models, and active 
learning were implemented.

___Please note that we were unable to provide the data on which this mode
was trained and evaluated due to its confidential nature.___

To use the model, you need to download the weights obtained by 
training, and place them in the directory [weights](weights).
Delete the file [to_be_deleted](weights/to_be_deleted.md)  and
replace it by the three files found in 
[this repository](https://drive.google.com/drive/folders/1sT-3jq-_CUohp4oVf3I1E3U3O1r5cnEF?usp=sharing).

## Libraries used

Before running any code, make sure you have all the libraries needed.
If not, open a terminal and run

`pip3 install $name_of_the_package`

* The neural networks are implemented via _tensorflow_.
* For plots we will need _matplotlib_, _sklearn_ and _itertools_.
* To deal with arrays, _numpy_ is needed.
* To handle videos files, _os_ and _moviepy_ are used.
* To label data for active learning the library _superintendent_ was used.

## Architecture

### Data Augmentation

In order to train models on a sufficiently large dataset, we needed to 
use data augmentation. On the notebook
[DataAugmentation](DataAugmentation.ipynb) is implemented a code 
which take as input a set of labeled pictures, and which create several 
transformation of each image, keeping the same label, to increase the 
robustness and the accuracy of the model.

### Comparison and Optimization

The three notebooks in the directory
[comparison_optimization](comparison_optimization) were used
to compare model performance of _ResNet50_, _EfficientNetB1_,
and _EfficientNetB7_, immediately clear from the names of the notebooks.
All notebooks work the same way: the batches are generated, the model is
downloaded and dense layers appended, and the original model is frozen
in such a way that it works as feature extractor. The added dense layers
are trained using the train data and validated with the valid batches.

### Fine tuning

_EfficientNetB1_ was fine-tuned using the notebook
[EfficientNetB1_finetune.ipynb](EfficientNetB1_finetune.ipynb).
Transfer learning was applied first, subsequently the last
10 layers were unfrozen (excepting batch normalization).
The training is implemented using early stopping and
the weights are saved for later use.

### Prediction and Visualization

In the notebook
[prediction_visualization.ipynb](prediction_visualization.ipynb),
the weights are loaded and used to generate predictions
on a test batch of 600 images. The accuracy is calculated and the
wrongly classified images are inspected.

### Analyze Video 

The notebook [analyze_video.ipynb](analyze_video.ipynb) is the most
important for direct application. It takes a video as input and
outputs a list of timestamps in which the model detects a defect
(either crack or root). To apply this code to one of your videos
you need to change the content of the variable
`video_file` to the path of the intended video.

### Active Learning

In the notebook [Active_Learning](Active_Learning.ipynb) is our implementation of active learning, using the
_Jupyter_ interface. The active learning interface requires _Python 3.7.11_
and _TensorFlow 2.7.0_.

## License

[MIT](LICENSE)
