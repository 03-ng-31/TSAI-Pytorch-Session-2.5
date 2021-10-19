# TSAI-Pytorch-Session-2.
## The Problem Statment 

Creating a Neural Network which does the following Operation :
  1. Takes in two inputs:
      A. An Image from the MNIST dataset
      B. A Random number between 0 and 9
  2. Buid a Neural Network which takes in the two inputs and provides us with two outputs 
      A.  The Number that was represented by the MNIST image
      B. The Sum of the random number and the number represented by the input  image to the network
 
 ![image](https://user-images.githubusercontent.com/71637993/137838038-cd0d1c2e-68aa-436a-a2b4-06c9aaed4282.png)
 
 Further Insights into the Input Layers 
 
 1. We consider an Images which are a representation of the digit from [0-9]
 
 ![image](https://user-images.githubusercontent.com/71637993/137838911-742d0deb-3fc2-456b-9e8d-06c28ee46c64.png)

 
 2. A One hot Encoded form of a random number between [0-9]
 
 ![image](https://user-images.githubusercontent.com/71637993/137839302-ce3dbef7-71ab-423a-827d-68bae11a0059.png)
 

 
 
 #### Data Creation Strategy 
 
 1. The Dataset we are considering for the image is MNIST which is a greyscale image and is of dimension 28 X 28 
    we make use of CNN , to extract features from the the images using three convolution blocks , first two blocks [Convolutional Operation + Max Pooling ] , third layer[ Convolutional Operation ]
    
    The dataset already is labelled i,e. Each images are labelled with their corresponding numbers between 0-9 . This would serve as the Y_1 Target 
    
    Once The Features are Obtained , we flatten the output of the final convolutional layers 
 2. Creation of the second input to the neural Network, involves creation of synthetic data .  
    --> We are to generate the numbers[0-9] randomly without bias towards any particular nunber. This would serve as the Second input to the network . 
    --> Create a target_variable Y_2 which is a mutiplication of the  label and the randomly generated number which serves as the output Y_2
    --> The random numbers generated are converted into binaries[0/1] using one hot encoding.
    
#### Data Combination 

We concatenate the Flattened tensors from the final convolutional layer with the one hot encoded form of the corresponding randomly generated number

#### Evaluating the Results
 
 We calculate two losses:
 1. For Correclty idenitfying the MNIST Image which is fed as input = Loss_1
 2. For Correctly Identifying the the Multpilication of the randomly generated number and input MNIST Image = Loss_2
 
 Calulcate the Total loss , i.e Total Loss = Loss_1 + Loss_2  and perform Backward Propagation to minimize the loss by updating wieghts. We are trying to mimize the overall losses 

We are looking at exactly what percentages data was correctly classified into its category 

we see that for Y_1 which is a Classification of Images : 55793   of 60000 are correctly classified . Giving us  92.98 % accuracy 

we see that for Y_3 which is a Classification for the Muliples : 54968   of 60000 are correctly classified . Giving us 91.61%   accuracy  
 
 

#### Training Logs

![image](https://user-images.githubusercontent.com/71637993/137843934-e0c070f1-6b3b-4763-b8db-d1098512350f.png)



 




