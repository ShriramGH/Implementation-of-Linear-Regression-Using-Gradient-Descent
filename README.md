# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Import the required library and read the dataframe.
2. Write a function computeCost to generate the cost function.
3. Perform iterations og gradient steps with learning rate.
4. Plot the Cost function using Gradient Descent and generate the required graph.
   
## Program:
```
Program to implement the linear regression using gradient descent.
Developed by: SHRIRAM S
RegisterNumber:  212222240098
```
### Import Necessary Libraries
```py
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```
### Display the Data
```py
data=pd.read_csv("ex1.txt",header =None)
```
### Prediction Graph on Profit
```py
plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")
```
### Define the Compute cost Function
```py
def computeCost(X,y,theta):
  m=len(y)
  h=X.dot(theta)
  square_err=(h-y)**2
  j=1/(2*m)* np.sum(square_err)
  return j
```
### Display the values of Function
```py
data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))

computeCost(X,y,theta)
```
### Define the gradient descent Function
```py
def gradientDescent(X,y,theta,alpha,num_iters):
  m=len(y)
  J_history=[]

  for i in range (num_iters):
    predictions=X.dot(theta)
    error = np.dot(X.transpose(),(predictions-y))
    descent=alpha*1/m * error
    theta-=descent
    J_history.append(computeCost(X,y,theta))

  return theta,J_history  
```
### h(x)
```py
theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1" )
```
### Plot the cost function and Profit Prediction Graph
```py
plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Grading Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")
```
### Prediction function
```py
def predict (x,theta):
  predictions=np.dot(theta.transpose(),x)
  return predictions[0]
```
### Prediction 1
```py
predict1=predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000,we predict a profit a profit of $"+str(round(predict1,0)))
```
### Prediction 2
```py
predict2=predict(np.array([1,7]),theta)*10000
print("For population =70,000,we predict a profit a profit of $"+str(round(predict2,0)))
```

## Output:
![image](https://github.com/NathinR/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118679646/59383340-39b5-4f26-b0d2-fe0c3fc774bb)
![image](https://github.com/NathinR/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118679646/27187757-82d6-4604-bfee-46d54746eda8)
![image](https://github.com/NathinR/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118679646/f470f068-8bfb-466a-a768-f55060470a9c)
![image](https://github.com/NathinR/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118679646/08808630-5138-45c6-bb94-2c89775848be)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
