# Deep Semantic Role Labeling (SRL)

SRL deep learning model is based on DB-LSTM which is described in this paper : 
[End-to-end learning of semantic role labeling using recurrent neural networks](http://www.aclweb.org/anthology/P15-1109)


The system  consists of code related to two models for following tasks : 
## Predicate identification 
 Model trained using RNN network with CRF as final output layer

## SRL model
SRL Trained on db-lstm network with CRF as final output layer. 


## Evaluation
We use evaluation/conlleval.pl for model evaluation for both the models . This script is taken from Conll2000 shared task. (http://www.cnts.ua.ac.be/conll2000/ )
Rest of the code files  for data manipulation and feeding the data for neural networks. 



## Code Layout : 

### Data folder : 

#### embeddings : 
The word embeddings have been trained using fasttext by facebook . The word embedding are represented by two files : 
Vocab.txt : the vocabulary words in w2v
wordVectors.txt : the vector for words mentioned in vocab.txt. Please note that it is row-row mapping from word to vector.
The w2v model is trained with skipgram , 32 dimensions on QQ+SRL data
 Predicate_identifier
Data for predicate identifier model in conll05 format. Please note that this format is generated by SemanticRoleLabeler
Srl

#### Models folder :
Final	
The final models for predicate identification and srl model
Parameters
This folder is for saving model parameters while training
PI 
Folder to save predicate identifier model while training
Srl
Folder to save srl model parameters while training



## Paddle Docker 

THe deep learning code is built using Paddle framework by Baidu (https://github.com/PaddlePaddle/Paddle)


Paddle docker is required to run the code in Docker environment. 

Working in the docker environment: 
Go to semantic-role-labeling-neural/
    - Run following command 
        + docker run -it  -v $(pwd):/paddle paddlepaddle/paddle:0.10.0   /bin/bash

if the docker image is not already present on the system, it will be downloaded. Also please check for newer version of the docker image


## Model related code :

Predicate Identifier Model 
Training the model :
pi_train.py
Running the inference code from trained model : 
Pi_infer.py
SRL model 
Training the model 
Srl_train.py
Running the inference code from trained model :
Srl_inference.py