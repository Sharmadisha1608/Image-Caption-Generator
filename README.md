# Image-Caption-Generator

#### Image Captioning - A Deep Learning Approach
###### In this I have proposed a hybrid system employing the use of multilayer Convolutional Neural Network(CNN) to generate vocabulary describing the images and a Long Short Term Memory (LSTM) to accurately structure meaningful sentences using the generated keywords. The convolutional neural network compares the target image to a large dataset of training images, then generates an accurate description using the trained captions. We showcase the efficiency of our proposed model using the Flickr8K dataset.
![image](https://user-images.githubusercontent.com/56456928/133123967-9a2133c0-c7a6-46e5-bd3f-b5fc834b8a68.png)

##### Pipeline
###### Store Image ->ResNet -> Image Encode-> Model-> Caption

###### The model consists of 3 phases:
###### A. Image Feature Extraction
###### The features of the images from the Flickr 8K dataset is extracted using the Resnet model due to the performance of the model in object identification. The dropout layers are present to reduce overfitting the training dataset, as this model configuration learns very fast. These are processed by a Dense layer to produce a 4096 vector element representation of the photo and passed on to the LSTM layer.

###### B. Sequence processor
###### The function of a sequence processor is for handling the text input by acting as a word embedding layer. The embedded layer consists of rules to extract the required features of the text and consists of a mask to ignore padded values. The network is then connected to a LSTM for the final phase of the image captioning.

###### C. Decoder
###### The final phase of the model combines the input from the Image extractor phase and the sequence processor phase using an additional operation then fed to a 256 neuron layer and then to a final output Dense layer that produces a softmax prediction of the next word in the caption over the entire vocabulary which was formed from the text data that was processed in the sequence processor phase.
![image](https://user-images.githubusercontent.com/56456928/133124021-0de2651b-6dc8-4a97-9624-a0175824a532.png)

##### Training Phase
###### During training phase we provide pair of input image and its appropriate captions to the image captioning model. The Resnet model is trained to identify all possible objects in an image. While LSTM part of model is trained to predict every word in the sentence after it has seen image as well as all previous words. For each caption we add two additional symbols to denote the starting and ending of the sequence. Whenever stop word is encountered it stops generating sentence and it marks end of string. Loss function for model is calculated as, where I represents input image and S represents the generated caption. N is length of generated sentence. pt and St represent probability and predicted word at the time t respectively. During the process of training we have tried to minimize this loss function.

##### Input-Output Screenshot
![image](https://user-images.githubusercontent.com/56456928/133818494-412c5e56-4258-4665-bae8-01f35e723c75.png)
![image](https://user-images.githubusercontent.com/56456928/133818543-0a5f7e4d-9b21-4443-be62-3743b3982df9.png)
