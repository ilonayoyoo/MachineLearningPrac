## Goals
In this lab you will:
- Learn to implement the model $f_{w,b}$ for linear regression with one variable

Notation
Here is a summary of some of the notation you will encounter.

General
Notation	Description	Python (if applicable)
𝑎
 	scalar, non bold	
𝐚
 	vector, bold	
Regression		
𝐱
 	Training Example feature values (in this lab - Size (1000 sqft))	x_train
𝐲
 	Training Example targets (in this lab Price (1000s of dollars))	y_train
𝑥(𝑖)
 ,  𝑦(𝑖)
 	 𝑖𝑡ℎ
 Training Example	x_i, y_i
m	Number of training examples	m
𝑤
 	parameter: weight	w
𝑏
 	parameter: bias	b
𝑓𝑤,𝑏(𝑥(𝑖))
 	The result of the model evaluation at  𝑥(𝑖)
  parameterized by  𝑤,𝑏
 :  𝑓𝑤,𝑏(𝑥(𝑖))=𝑤𝑥(𝑖)+𝑏
 	f_wb

