# MonReader

This project aims to design an image model for image sequence classification. Two image models are built for the MonReader to identify whether there is any flipping action in a sequence of image. The first model is an a simple CNN based Image classifier using Keras. The model contains 3 Convoluational layers with 0.3 dropout rate.
The other model uses ResNet model backbone and we fine tuned the model using our image dataset. Both ResNet18 and ResNet50 are tested for the comparision.   

#Preprocessing

Images are chopped and resize to 224x224. Those images are then transformed into standard form with normalized RGB for computation efficiency 

#Kares CNN

For the model setup, we use dropout rate of 0.3 to avoid overfitting. A fully connected layer is used to link up the flatten layer and only output will be produced by the model.We also chose sigmoid as our activation function in the last layer since we want to have a single output with a range from 0 to 1.
The output lower than 0.5 would be predicted as 'Not Flipped' and the one with higher than 0.5 would be predicted as 'Flipped'

Model Architecture:
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d (Conv2D)             (None, 224, 224, 16)      448       
                                                                 
 max_pooling2d (MaxPooling2D  (None, 112, 112, 16)     0         
 )                                                               
                                                                 
 conv2d_1 (Conv2D)           (None, 112, 112, 16)      2320      
                                                                 
 max_pooling2d_1 (MaxPooling  (None, 56, 56, 16)       0         
 2D)                                                             
                                                                 
 conv2d_2 (Conv2D)           (None, 56, 56, 32)        4640      
                                                                 
 max_pooling2d_2 (MaxPooling  (None, 28, 28, 32)       0         
 2D)                                                             
                                                                 
 dropout (Dropout)           (None, 28, 28, 32)        0         
                                                                 
 flatten (Flatten)           (None, 25088)             0         
                                                                 
 dense (Dense)               (None, 128)               3211392   
                                                                 
 dense_1 (Dense)             (None, 1)                 129       
                                                                 
=================================================================
Total params: 3,218,929
Trainable params: 3,218,929
Non-trainable params: 0
_________________________________________________________________

              precision    recall  f1-score   support

Not Flip (0)       0.99      1.00      1.00       307
    Flip (1)       1.00      0.99      0.99       290

    accuracy                           0.99       597
   macro avg       1.00      0.99      0.99       597
weighted avg       1.00      0.99      0.99       597

#ResNet



Accuracy: 0.9547738693467337 ,F1 Score: 0.9543147208121826
Prediction of first 10 images: [1 1 0 1 1 1 1 1 0 0]
Label of first 10 images: [1 1 1 1 1 1 1 1 0 0]
              precision    recall  f1-score   support

Not Flip (0)       0.97      0.94      0.96       307
    Flip (1)       0.94      0.97      0.95       290

    accuracy                           0.95       597
   macro avg       0.95      0.96      0.95       597
weighted avg       0.96      0.95      0.95       597


Accuracy: 0.9698492462311558 ,F1 Score: 0.96875
Prediction of first 10 images: [1 0 0 0 0 1 0 0 1 0]
Label of first 10 images: [1 0 0 0 0 1 0 0 1 0]
              precision    recall  f1-score   support

Not Flip (0)       0.96      0.98      0.97       307
    Flip (1)       0.98      0.96      0.97       290

    accuracy                           0.97       597
   macro avg       0.97      0.97      0.97       597
weighted avg       0.97      0.97      0.97       597


aOxCdP66ufhd0EbD
