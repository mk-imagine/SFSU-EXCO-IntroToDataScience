# SFSU - EXCO - Intro-to-Data-Science

## Diabetic Retinopathy Detection using VGG16
##### By: Mark Kim and Xuantong (Queenie) Qian
##### Code HEAVILY based off of kernal of Dana Elisa Nicolas on Kaggle

This is the final project for EXCO - Intro to Data Science.

Diabetic Retinopathy is a disease that causes retinal damage due to diabetes.  It is a leading cause of diabetes in developed countries (http://www.diabetes.co.uk/diabetes-complications/diabetic-retinopathy.html).

#### The Data
For this project we found a dataset containing images that have already been categorized into 5 categories of diabetic retinopathy: None, Mild, Moderate, Proliferate, and Severe.  The objective of our project was to create a machine learning model that would accurately predict the severity of diabetic retinopathy from an image presented to it.  Because of the accuracy and ease of use, we decided to implement the VGG16 Convolutional Neural Network for classification and detection.

#### The VGG16 Convolutional Neural Network
The VGG16 model is an extremely accurate neural network which achieves a 92.7% accuracy of ImageNet, a dataset of over 15 million images belonging to over 22,000 categories.  Although this network can achieve extremely high accuracy, it has one major drawback: the speed with which it can be trained.  It takes an enormous amount of time to train this model.  We only trained this model for up to 25 epochs (which we will explain in more detail), so we did not achieve phenomenal results, but each epoch of training was painfully slow.  The reason for this is because as a fully connected model that ends up having a very large set of parameters to calculate.  VGG16 has a number of other weaknesses like its size, scalability, and memory constraints.  But because of its ease of use, it makes an excellent learning tool.

#### Implementation
The data provided was split into the 5 categories explained earlier.  Since it was not seperated between a training set and validation set, we had to split it into the two sets.  Using a tool called "split_folders," we were able to seperate the training data into a 80/20 split of training and validation data, respectively.  To get an idea of what the data looked like, we used pytorch to create a grid of sample images from the dataset.  We did some research on how to do this within keras, but since we had code available from the class that did this with pytorch, we abandoned our efforts with keras and used the class code.

Following this, we wanted to add image transformations to increase the amount of data we had, but were never able to actually implement it.  Instead, the ImageDataGenerator was just used to create the datasets from the image directories.  Perhaps there is a more elegant solution to this, but we are not aware of one at the moment.  The actual implementation of the VGG16 model was relatively simple and using the ImageNet weights allowed us to use the "experience" of the pre-trained model as well.

We experimented a bit with freezing and unfreezing a number of the final layers of the model so that it would be specialized towards the dataset we provided it.  After this experimentation, we settled on unfreezing the final 8 layers.  Even with only 8 layers unfrozen, the trainable parameters still numbered beyond 100 million.  This is the major reason why the VGG16 CNN is so slow to train.

An interesting trick that we found in the code from Ms. Nicolas's code was the introduction of checkpoints in the training model.  These checkpoints allow the fitting to check if the accuracy of the model is increasing after each training epoch.  If the model's validation accuracy does not increase, it keeps the weights of the highest accuracy epoch.  In addition, if the validation accuracy does not improve after a set number of epochs, it stops further epochs from being attempted.  Yet another tactic we found in many kernals, and indeed this kernal as well, was to weight the data.  In this particular case, the distribution of data between the severity cases was uneven, so each severity class was weighted so that they were all evenly represented.

#### Conclusion
After finally fitting the data, we were able to see a modest increase in training accuracy over time.  As can be seen with the loss and accuracy graphs, the accuracy increased significantly for the training data, but the accuracy against the validation data was less than spectacular.  It is obvious that classification accuracy with data like ours is very difficult to achieve and more experimentation will be necessary to yield better results.  Overall, this was a very educational project and a great springboard to learn about machine learning and data science in greater depth.
