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

