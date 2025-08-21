# Identifying lopsidedness in galaxies using Deep Convolutional Neural Network
The project aims to create a machine-learning model using the publicly-available AlexNet, a popular Deep Convolutional Neural Network (DCNN) architecture for the classification of spiral galaxies from SDSS into lopsided and symmetric.

# Repository Structure
This repository includes the following:
main:
1. The script for augmentation, training and further, generating the model performance metrics on the test data set is presented as a compressed file:
To run the model from scratch, run the ./cnn_run.sh, which includes splitting of data into training and testing, followed by augmentation, then training the model on the augmented dataset and finally, testing the performance of the model.

Some more necessary details regarding various subdirectories:

a)input_images: contains the labelled images(placed in separate subdirectories).
b)package_cnn/image_classify/images/training: contains images used for training, after augmentation has been performed using
c)package_cnn/image_classify/images/training: contains images used for training, after augmentation has been performed using
d)package_cnn/image_classify/images/training: contains images used for training, after augmentation has been performed using
e)outputs: jjk

Flow of execution of ./cnn_run.sh:



# Data
