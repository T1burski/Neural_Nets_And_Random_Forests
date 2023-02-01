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

(the feature's descriptions can be found at https://www.kaggle.com/datasets/prosperchuks/health-dataset)

_____________________________________________________________________

## Machine abd Deep Learning: the objective of this project

The main goal of this project is to compare the results of predicting the ocurrence or not os the health conditions diabetes, stroke and hypertension using **Artificial Neural Networks** and **Random Forests**.

The Neural Networks used were Multi-layer feedforward networks with one output node: the result of 1 (the event happens) or 0 (the event doesn't happen). Now, about the number of input nodes and hidden nodes: the number of input nodes is equal to the number of features on that dataset, while for the hidden nodes, the suggested rule by Masters, 1993 (Practical Neural Network Recipies in C++, 1993, by Timothy Masters), that suggests that the format of the hidden layers should follow the format of a geometric pyramid, with the number of neurons decreasing from the input to the output. Following this rule, the neural networks will have the following structures:

***Diabetes NN***:

![image](https://user-images.githubusercontent.com/100734219/215916166-0ddeab16-54d1-4267-a65d-0cd2cc62520b.png)


***Hypertension NN***:

![image](https://user-images.githubusercontent.com/100734219/215916204-d8631b42-20c7-4e2c-88c4-61644d4aca65.png)


***Stroke NN***:

![image](https://user-images.githubusercontent.com/100734219/215916252-65e8e678-7593-4e33-93e7-10f2ffdbbdad.png)


The experiments with the Neural Networks were developed using, in each medical condition dataframe, three cases: without data regularization and with data regularization using L1 technique with λ = 0,01 and λ = 0,1 (technique used to prevent occasional overfittinng of the model.

Now, the Random Forest structures were first tested without setting previously any parameters of the forest and by setting the optimized parameters obtained when using RandomSearchCV.




























