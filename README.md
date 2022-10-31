# PCCAAR

PCCAAR is an implementation of an attribute artifact removal method for attributes compressed Point Clouds.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install the necessary packages specified in both notebooks, or you can run them directly using Google Colab.

## Training
First, you have to train 3 models for each component of the YUV format.
Due to limited resources, the training will be divided onto multiple iterations, during each of them, you load 100 patches from each point cloud for a total of 600 graphs, this batch will be fed to the model for the training, and after that, you have to pause the training by saving the model's weights, prepare the next batch of data, and then resume the training of the previous model so that it get's initialized by the previous weights.
This procedure should be repeated until there is no more data to train on for the 3 channels of the YUV format.
## Testing
The testing pipeline is very straightforward, all you have to do is import the decoded point cloud as well as the original one ( for comparison reasons) and also the 3 trained models for each YUV channel, the script will automatically divide the test data into a set of patches and feed them into the 3 models to generate the output for each channel, the outputs will then be concatenated to form the cleaned Point Cloud which will be compared to the original one.

