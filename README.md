# Homework 1 EE 399

Author: Samuel Luong

## Abstract

This assignment is an introduction to machine learning. The code will be able to find the best fitting model for the assigned y values based on a nonlinear function.
In this case, the nonlinear function has 4 parameters (A, B, C, D). Using opitmization and least squared error, we will be able to find the parameters. Then, we can run 
some testing code such as training the model with three different types of linear functions with certain amounts of data and testing the rest of the data with our new models. Also, we will be able to run a 2D error landscape by sweeping 2 different parameters and fixing 2 parameters and finding the 2D loss landscapes. 

## Section 1 - Introduction / Overview

Based on the data points for y, we must design a way to model the data points. In this case, we use an equation, f(x) = AcosBx + Cx + D, as the model of the data. Afterwards we must find the parameters: A, B, C, and D. The method used will be explained in the other sections but the next step would be to fixed two of the parameters and sweeping the other two parameters. We will do all combinations meaning that there are 6 2D loss landscape graphs. Afterwards, we will be using different models such as a line, parabola, and a 19th degree polynomial and using different sections of the y data to find the best fit polynomial. The assignment states that the first method is training the first 20 data points of the y data and then testing the last 10 data with the new model. Afterwards, we will be assigning the first 10 and the last 10 data points of the y data for training then testing the middle 10 data points with the new model.

## Section 2 - Theoritcal Background

