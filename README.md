# SFSU - EXCO - Intro-to-Data-Science
##### By: Mark Kim and Xuantong (Queenie) Qian

## Diabetic Retinopathy Detection using VGG16
### Code HEAVILY based from kernal of Dana Elisa Nicolas on Kaggle

This is the final project for EXCO - Intro to Data Science.

Diabetic Retinopathy is a disease that causes retinal damage due to diabetes.  It is a leading cause of diabetes in developed countries (http://www.diabetes.co.uk/diabetes-complications/diabetic-retinopathy.html).

#### The Data
For this project we found a dataset containing images that have already been categorized into 5 categories of diabetic retinopathy: None, Mild, Moderate, Proliferate, and Severe.  The objective of our project was to create a machine learning model that would accurately predict the severity of diabetic retinopathy from an image presented to it.  Because of the accuracy and ease of use, we decided to implement the VGG16 Convolutional Neural Network for classification and detection.

#### The VGG16 Convolutional Neural Network
The VGG16 model is an extremely accurate neural network which achieves a 92.7% accuracy of ImageNet, a dataset of over 15 million images belonging to over 22,000 categories.  Although this network can achieve extremely high accuracy, it has one major drawback.  Chief of its weaknesses is probably the speed with which it can be trained.  It takes an enormous amount of time to train this model.  We only trained this model for up to 25 epochs (which we will explain in more detail), so we did not achieve phenomenal results, but each epoch of training was painfully slow.  The reason for this is because as a fully connected model that ends up having a very large set of parameters to calculate.

