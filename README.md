# Neural_Nets_And_Random_Forests
Comparison of Artificial Neural Networks and Random Forests applied to the prediction of the occurence of diabetes, stroke and hypertension on people.

_____________________________________________________________________

## About the datasets

A dataset was obtained on Kaggle regarding historical data of patients and the occurence, or not, of the medical conditions diabetes, stroke and hypertension, based on multiple features, such as:

### Diabetes' Features:
Age	Sex	HighChol	CholCheck	BMI	Smoker	HeartDiseaseorAttack	PhysActivity	Fruits	Veggies	HvyAlcoholConsump	GenHlth	MentHlth	PhysHlth	DiffWalk	Stroke	HighBP

### Hypertension's' Features:
age	sex	cp	trestbps	chol	fbs	restecg	thalach	exang	oldpeak	slope	ca	thal

### Stroke's Features:
sex	age	hypertension	heart_disease	ever_married	work_type	Residence_type	avg_glucose_level	bmi	smoking_status

(the features' descriptions can be found at https://www.kaggle.com/datasets/prosperchuks/health-dataset)

_____________________________________________________________________

## Machine and Deep Learning: the objective of this project

The main goal of this project is to compare the results of predicting the ocurrence or not os the health conditions diabetes, stroke and hypertension using **Artificial Neural Networks** and **Random Forests**.

The Neural Networks used were Multi-layer feedforward networks with one output node: the result of 1 (the event happens) or 0 (the event doesn't happen). Now, about the number of input nodes and hidden nodes: the number of input nodes is equal to the number of features on that dataset, while for the hidden nodes, the suggested rule by Masters, 1993 (Practical Neural Network Recipies in C++, 1993, by Timothy Masters), that suggests that the format of the hidden layers should follow the format of a geometric pyramid, with the number of neurons decreasing from the input to the output. Following this rule, the neural networks will have the following structures:

***Diabetes NN***:

![image](https://user-images.githubusercontent.com/100734219/215916166-0ddeab16-54d1-4267-a65d-0cd2cc62520b.png)


***Hypertension NN***:

![image](https://user-images.githubusercontent.com/100734219/215916204-d8631b42-20c7-4e2c-88c4-61644d4aca65.png)


***Stroke NN***:

![image](https://user-images.githubusercontent.com/100734219/215916252-65e8e678-7593-4e33-93e7-10f2ffdbbdad.png)


The experiments with the Neural Networks were developed using, in each medical condition dataframe, three cases: without data regularization and with data regularization using L2 technique with λ = 0,01 and λ = 0,1 (technique used to prevent occasional overfittinng of the model.

Now, the Random Forest structures were first tested without setting previously any parameters of the forest and by setting the optimized parameters obtained when using RandomSearchCV.

_____________________________________________________________________

## Details of the Development

Before starting, a few hyperparameters were manually set for the entirety of the development process, in order to make comparisons possible afterwards, such as: 

- Data training/testing sets split with the proportion 70% training  /  30% testing;
- (NN) ReLU activation function for the hidden layers;
- (NN) Sigmoid activation function for the output layer (since we have a classification problem (0 or 1);
- (NN) Binary_crossentropy loss function;
- (NN) adam optimizer;
- (NN) Accuracy score as a metric;
- (NN) Number of epochs = 150 and batches = 32 (values appropriate for the size os the datasets and that have a reasonable time of training);
- (NN) validation split of 0,15, without shuffling;
- Random state set to 42 during the tests. 

With all this being said, let's go to the steps taken during the development: Before starting the training of the neural networks, I had to explore the datasets to see if any missing value or absurdities were there. With this, it was discovered that the column "sex" in the hypertension dataset had some missing values, as well as the column "sex" in the stroke dataset. These missing values had to be removed because their presence could cause exploding gradient issues, causing NaN loss function values during training. Also, in the stroke dataset there were values on the column "age" < 0, which did not make sense and were therefore removed. 

Z-score normalization was used on the training and test datasets seperately (necessary for when training the neural network, so the model converges faster. However, he normalized datasets weren't applied on the Random Forest models, since tree-based models don't compare data across features.

Below, some examples of the learning curves obtained during the neural networks' training:

![image](https://user-images.githubusercontent.com/100734219/216203389-65ba590d-6b7c-44ab-a4c2-bc8534388772.png)

_Learning curve obtained for the training and validation using the diabetes dataset without applying any regularization. As we can see, there was some overfitting happening after something close to the epoch 50._

![image](https://user-images.githubusercontent.com/100734219/216203733-6716f4fd-ebd9-4ce6-84ec-db9f26c278d4.png)

_Learning curve obtained for the training and validation using the diabetes dataset when applying L2 regularization with λ = 0,01. As we can see, we could now prevent some of the overfitting, since the training and validation curves converged._


In the end, the following results for the accuracy were obtained:

![image](https://user-images.githubusercontent.com/100734219/216204734-60109f96-122c-4ce0-ac5a-dc07d55eecfa.png)

As we can see, for the diabetes prediction, the best model was using an Artificial Neural Network with L2 regularization with λ = 0,01. for the hypertension prediction we had interesting results, with extremely high accuracy values, which could be due to the size and representability of the dataset, and for the stroke prediction, curiously, Random Forest mdels had way better accuracy scores than ANN, being the model with Random Forest with Optimized Parameters the best model for the prediction of this medical condition.

