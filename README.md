# Classification-EMDS-
Report on Classification of EM dataset by using ML,DL and CV techniques
Summary:
Out of total 840 images divided in 21 classes ,40 images of each classes I uses 32 images as training and 8 images as testing of every class so ,672 images for training and 168 images for testing.
Best accuracy for classification I got is 57.7%  by using  vgg16 as feature extractor and using XGBOOST Classifier on that vgg16 extracted features for classification.

Details of Approches:

1:Using ANN:

In ANN ,I simply divided the data set into training and testing (672 and 168) and choosen RELU activation function in hidden layer and softmax activation function in Output layer.There is 3 hidden layer in this model. By doing Classification by ANN the accuracy I got is only 4%.


2:Using Transfer Lerning and fine Tunning:

MobileNet V2:

In this first I done Data Augmentation of training Images to increase the number  of training images.Downloaded the Pretrained MobileNet V2 model by removing the top layer the model.
Then adding the Data Augmented layer and dropout layer(for regularization) in Pretrained model and then doing  the training (freezing the layer of base model).And after 25 epochs I got 19% accuracy.

After that I unfreezed the 54 layer out of 154 layer for fine tunning the model ,and then doing the training . After fine tunning I got testing accuracy 25%  .


3:vgg16 as base model and  Random Forest,XGBOOSTand SVM as Classifier: 

In this 1stly I extracted the features of training images and  the vgg16 gives 1000 features . Same things done on the testing images . Features extracted by the vgg16 is uses the Random Forest ,Xgboost and SVM Classifier for classification.
After doing Hyperparameter tunning by GridSearch CV (of RF and SVM model) and Optuna (for XGBOOST model) I got the accuracy of 48.8(by RF),57.7(by XGBOOST) and 24.4(by SVM).


4:ResNet V2 as base model and  Random Forest,XGBOOSTand SVM as Classifier: 

In this 1stly I extracted the features of training images using the ResNet  . Same things done on the testing images . Features extracted by the ResNet V2 is uses the Random Forest ,Xgboost and SVM Classifier for classification.
After doing Hyperparameter tunning by GridSearch CV (of RF and SVM model) and Optuna (for XGBOOST model) I got the accuracy of 45.8(by RF),53.5(by XGBOOST) and 21.3(by SVM).


5:Image_Denoising_Thresholding_InceptionResNetV2:

In this on train and test images I uses the Median blur filter to to reduce the noise .Then on denoised image I applied the Adaptive thresholding so that only foreground object will left in the image  .And then applying the InceptionResNetV2  for feature extraction on filtered image to get the features. After getting the features I applied the Random Forest Classifier for classification and I got the Classification accuracy of 41.07%.
