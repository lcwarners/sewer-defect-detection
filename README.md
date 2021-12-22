# Sewer Defect Automated Detection Using Machine Learning
### CS-433 Machine Learning project 2

Within the framework of the EPFL Machine Learning course, we collaborated
with the city of Lausanne to automate the recognition of defects in
sewer pipes. To this goal we trained the neural networks _RESNet50_,
_EfficientNetB1_ and _EfficientNetB7_ on CCTV videos from the pipes. Our
purpose was to detect two main defects, namely roots and cracks.
Data augmentation, comparison of these three models, and active 
learning were implemented.

___Please note that we were unable to provide the data on which this mode
was trained and evaluated due to its confidential nature.___

To use the model, you need to download the weights obtained by 
training, and place them in the directory [weights](weights).
Delete the file [ẗo_be_deleted](weights/to_be_deleted.md)  and
replace it by the files found in 
https://drive.google.com/drive/folders/1sT-3jq-_CUohp4oVf3I1E3U3O1r5cnEF?usp=sharing

## Libraries used

Before running any code, make sure you have all the libraries needed.
If not, open a terminal and run
`pip3 install $name_of_the_package`

* The neural networks are implemented via _tensorflow_.
* For plots we will need _matplotlib_, _sklearn_ and _itertools_.
* To deal with arrays, _numpy_ is needed.
* To handle videos files, _os_ and _moviepy_ are used.

## Architecture

### Data Augmentation

% to do

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
(either crack or root). To apply this code to one of your video
you need to change the content of the variable
`video_file` by the path of your video.

### Active Learning

% to do

## License

[MIT](LICENSE)
