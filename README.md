# MonReader

This project aims to design an image model for image sequence classification. Two image models are built for the MonReader to identify whether there is any flipping action in a sequence of image. The first model is an a simple CNN based Image classifier using Keras. The model contains 3 Convoluational layers with 0.3 dropout rate.
The other model uses ResNet model backbone and we fine tuned the model using our image dataset. Both ResNet18 and ResNet50 are tested for the comparision.   

#Preprocessing

Images are chopped and resize to 224x224. Those images are then transformed into standard form with normalized RGB for computation efficiency 

# Kares CNN

For the model setup, we use dropout rate of 0.3 to avoid overfitting. A fully connected layer is used to link up the flatten layer and only output will be produced by the model.We also chose sigmoid as our activation function in the last layer since we want to have a single output with a range from 0 to 1.
The output lower than 0.5 would be predicted as 'Not Flipped' and the one with higher than 0.5 would be predicted as 'Flipped'

Model Architecture:
![image](https://user-images.githubusercontent.com/62399559/187402437-429829c6-2105-4c55-855a-5602008d4249.png)

With a simple CNN architecture, the model achieve over 99% accuracy on the image recognition.

![image](https://user-images.githubusercontent.com/62399559/187402510-144fdf9a-77e8-4e48-bea1-a67f54de3ca8.png)


The image includes NotFlip(0)/Flip(1): 1
![image](https://user-images.githubusercontent.com/62399559/187403069-966a3042-6300-449b-b7bf-fcdd9fc84107.png)


# ResNet


ResNet18:

![image](https://user-images.githubusercontent.com/62399559/187402583-e916315f-599b-4e63-b9d0-ea9445fb058b.png)

ResNet50:

![image](https://user-images.githubusercontent.com/62399559/187402630-c9f6c8aa-f8f7-4ee7-b725-dbd4325d0dfc.png)


Both ResNet18 and ResNet50 have more complicated setup on layers and usually produce result better than vanilla CNN model in image classification. However, in the simple task like binary classifcation. The ResNet model may overshoot the problem from the over-complicated structure. In this case, we can see that both finetuned ResNet models have lower performace than a simple CNN model, almost 4% less in accuracy.      

aOxCdP66ufhd0EbD
