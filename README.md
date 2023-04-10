# Homework 1 EE 399

Author: Samuel Luong

## Abstract

This assignment is an introduction to machine learning. The code will be able to find the best fitting model for the assigned y values based on a nonlinear function.
In this case, the nonlinear function has 4 parameters (A, B, C, D). Using opitmization and least squared error, we will be able to find the parameters. Then, we can run 
some testing code such as training the model with three different types of linear functions with certain amounts of data and testing the rest of the data with our new models. Also, we will be able to run a 2D error landscape by sweeping 2 different parameters and fixing 2 parameters and finding the 2D loss landscapes. 

## Section 1 - Introduction / Overview

Based on the data points for y, we must design a way to model the data points. In this case, we use an equation, f(x) = AcosBx + Cx + D, as the model of the data. Afterwards we must find the parameters: A, B, C, and D. The method used will be explained in the other sections but the next step would be to fixed two of the parameters and sweeping the other two parameters. We will do all combinations meaning that there are 6 2D loss landscape graphs. Afterwards, we will be using different models such as a line, parabola, and a 19th degree polynomial and using different sections of the y data to find the best fit polynomial. The assignment states that the first method is training the first 20 data points of the y data and then testing the last 10 data with the new model. Afterwards, we will be assigning the first 10 and the last 10 data points of the y data for training then testing the middle 10 data points with the new model.

## Section 2 - Theoritcal Background

To find the model, we must find the parameters of the equation. For linear equations, the process is just finding the summation of the errors and deriving based on each parameter. The process can be condensed down into a line of code for python by using the numpy.polyfit function. However, the model that was given to us is a nonlinear equation. Therefore, the process of finding the parameters is by finding the least squared error of the equation and providing a intial guess of the parameters. Afterwards, we can used the minimize function from python to find the actually parameters which can be adjusted based on the eye sight. Finding nonlinear parameters, we can assume that there can be many solutions or no solutions because the process requires us to eyeball the curve to best fit based on our decision. 

## Section 3 - Algorithm Implementation and Development

There are three different parts of the code to finish the assignment. The first code is the curve fitting for a nonlinear model. First,I added the datas into an x and y set. Afterwards, I designed the function that returns the least squared error. Inside this function, the function requires 3 variables: p is the parameter array, x is the x data, and y is the y data. Then, I made a parameter array that includes the four parameters that we must use for the least square error. The four parameters are a best guess which can be editted to best fit the data. Then, I used the scipy.optimize library to use the opt.minimize code. The minimize code can be used to find the best fitting parameters and requires the best fitting function, the initial guess parameters, the x and y data, and setting the method to Nelder-Mead. Afterwards, we extract the results and seperate each of the four parameters. Part i ask us to find the parameters A, B, C, and D so I printed the results. Finally, I graphed the y data points and the curve from the generated parameters and nonlinear function.

For part ii, we need to find a 2D loss landscape graph of each combination of the 2 sweeping parameters and 2 fixed parameters. In total, we should have 6 graphs of each different combination. First, I coded the loss_fun by returning the least squared error value. The function requires 6 different parameters: the A, B, C, D parameters and the x and y data points. Then, we set two different parameters on the given parameters from part i. Afterwards, I used numpy linspace to sweep the other two parameters. The linspace code needs a starting point and an ending point. Also, we can set the number of values inbetween the starting and ending point. In this case, I set it to 100 data points between the starting and ending point. Then, we create a 2D array based on the lenth of the inbetween number of values. This empty area is filled with least square error values and is placed based on the position of the first and second sweep parameter. For example, if we want to insert a least square error at position [i,j] then the sweeping parameters used is the first parameter[i] and the second parameter[j]. We repeat this process for every combination of sweeping parameters. Afterwards, we used pcolors by inserting the 2D error array and subplots to seperate the graphs into a 2 by 3.

Lastly, the last two parts of the assignment requires us training the model with few data points at different locations. For example, part iii requires us to use three different models like the line, parabola, and 19th polynomial functions to fit the data. However, I had to use only the first 20 data points as "training data" and use the model for the last 10 data points. Therefore, I coded three different functions for each model. Then, the return value is the least squared error of each model. Each functions' parameters is the array of parameters and the first 20 x and first 20 y data points. To find the unknown parameters and converting it into an array, we use the numpy's polyfit function where we insert the training data's x and y and typing the number of degrees of the polynomial. For example, a line is 1 degree, the parabola is 2 degrees and the 19th polynomial is the 19 degrees. Then, we find the least square error for each model's training data and print it out. Then, we use the same model and insert the last 10 data points for each x and y and call for the least square error value and print it out. Now, we repeat the same process but for the first 10 data points and the last 10 data points as training data. To make sure its in one array, we use numpy's concatenate. Also, for the testing data, we use the middle 10 data points instead. All the least squared error values are printed out.

## Section 4 - Computational Results 

The results for part i shows a curve that is closely similar to the data points. According to the Figure 1, we can see that the red curve mostly matches with the data points. The parameters that fits the equation, f(x) = AcosBx + Cx + D, is **A = 2.17, B = 0.909, C = 0.732, and D = 31.45**.  

![Alt text](https://github.com/Griffinhunter/Homework-1---EE-399/blob/main/Curve%20Fit.jpg)

Figure 1: The best fit curve with a nonlinear equation

The results for part ii requires the parameters from the previous part. Therefore, the fixed parameters are equal to the parameters from the first part of the assignment. Figure 2 shows the resulting 2D loss landscape graphs for each combination. The number of minima is shown by the darker blue areas because this number presents the error that is closer to the 0 value. 
Therefore, we can see that by sweeping D and C, we can see that there are several points in the graph that are near 0. Due to the visibility of the coloring, we can barely see that there are about 4 areas that are dark purple. This means that there are **4 minimas**. 
Next, the graph for sweeping A and D, we can see that at a some range of A, any number for D can the value. In this case, we sweep D between 20 to 40 with 10 equal segments. The fixed value of D was 31.45 and the range between shows that the number of minimas is large. In this case, we can see about **4 to 5 minimas** with our given range.
The A and B sweeping landscape also shows a similar response where the locations of minimas is concentrated in a certain location but can be any value in that area. In this case, we can see about **3 to 4 minimas** for this graph.
The B and C sweeping landscape shows a more senssitive sweeping. In this case, we can clearly see **2 minimas* in the middle of the landscape. The surronding areas are clearly lighter colors compared to the two points in the graph. 
The B and D sweeping landscape shows a similar pattern with B and C, however, the colors are a lot more darker compared to B and C. In this case, we can see roughly **2 to 3 minimas**
Finally, for the A and C sweeping landscape, we can see that the dark purple patterns are similar to A and D. In this case, the minimas are concentrated in a line where any of these values can be use to produce a low least square error. Therefore, the number of minimas roughly shown in this landscape is **4 to 6 minimas**.

![Alt text](https://github.com/Griffinhunter/Homework-1---EE-399/blob/main/2D%20Landscape.jpg)

Figrue 2: The 2D loss landscape of 6 combinations of 2 sweep parameters

The results for part iii shows that the linear model is the best for the training data as least square error is the smallest number which is shown in the figure. The reason is that the line passes through the testing data points so the least square error is small. The parabola does not account for the testing data as the model starts to dip downward before the testing data. Therefore, the least square error is larger than the linear model. The 19th degree polynomial has a small least square error value for the training model but when we used the tested data, the least square error value is the largest out of the other models. The reason is that the fitting method for the training data has all the points connected together. However, the tested data is not included in the model so the error is large. Overall, the pattern is that the larger the degree is for the polynomial then the smaller the least square error because some models cannot predict the testing data. **All least square error values is in figure 3.**

![Alt text](https://github.com/Griffinhunter/Homework-1---EE-399/blob/main/First%2020%20Training.jpg.png)

Figure 3: Training with the first 20 data points and testing with the last 10

The results for part iv shows that the linear model is also the best model to use for least square error. The reason that the least square error is smaller than part 
iii because we can predict the location from the first 10 data points and the last 10 data points and whatever is in the moddle can have a smaller least square error compared to predicting where the last 10 is from the previous part. The parabola model has a smaller least square error for the testing data then the training data is because the model passes through the middle parts of the data but doesn't pass through the last 10 data points of the training data.
The 19th degree polynomial's least square error is better than the previous part because the model passes through the middle portion with a linear line and the least square error is small for the testing data. Overall, the linear, parabola, and 19th degree polynomial has a better least square error for the testing data than the previous part because the data in the middle can be easily be fit with a model becasue the data is in a linear pattern. **All least square error values is in figure 4**.

![Alt text](https://github.com/Griffinhunter/Homework-1---EE-399/blob/main/10%20by%2010.jpg)

Figure 4: Training with the first 10 and last 10 data points and testing with the middle 10
