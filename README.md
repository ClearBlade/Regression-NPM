# regression-js

## Contents

### [Overview](#overview-1)
### [System Installation](#system-installation)
### [Usage](#usage-1)
### [Assets](#assets-1)
### [Advanced](#advanced-1)

## Overview

Regression algorithms can be implemented using the Regression-JS library to run on the ClearBlade Platform for prediction purposes.

This is an ipm package, which contains one or more reusable assets within the ipm Community. The 'package.json' in this repo is a ipm spec's package.json, [here](https://docs.clearblade.com/v/3/6-ipm/spec), which is a superset of npm's package.json spec, [here](https://docs.npmjs.com/files/package.json).

[Browse ipm Packages](https://ipm.clearblade.com)

## System Installation

1. Open the ClearBlade Platform and enter your login credentials
```
https://platform.clearblade.com/
```
2. Click on **Add System** -> **Advanced** and copy the link of this repository in the box.
```
https://github.com/ClearBlade/brain-js
```
3. Click **Create**
4. You can now access this system in the platform.

## Usage

- This IPM package consists of a Regression Library that can be imported in the ClearBlade Platform in order to train and test machine learning models on the platform.

- This library supports both linear and polynomial regression.

- First we define the training data which we will be using for predicting using linear regression. The data below is recorded by a temperature sensor over a period of 20 days. 

``` javascript
  var inputs = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20];
  var outputs = [73.4, 76.2, 62.3, 80.2, 100, 94, 88.3, 70, 78, 83, 83, 91, 74, 68, 84, 81, 90, 94, 103, 99];
```

- The following code snippet loads the Regression library and allows your code to access functionality of the library APIs via the **model** variable.

``` javascript
  const model = MLRegression().SLR;
```

- Once we define the **model** variable, we define a new regression model with the given input training data and the expected outputs. We get a trained model (in this case **linear**) and this model is stored in the regression variable.

``` javascript
   var regression = new model(inputs, outputs);
```

- Once the model is trained, predict the value for the 24th day.

``` javascript
  var test = [24];
  var prediction = regression.predict(test[0]);
```

- In a similar way, polynomial regression can also be performed

``` javascript
  const degree = 2;

  const new_model = MLRegression().PolynomialRegression
  
  var regression = new new_model(inputs, outputs, degree);    // degree of the polynomial equation is provided

  var test = 24;
  var prediction = regression.predict(test));
```
 
- Additional information can also be logged using the **regression** variable
  - regression.coefficients -  Prints the coefficients in increasing order of power (from 0 to degree).
  - regression.toString(3) - Prints a human-readable version of the function.

- The implementation of this library is done in the [smoke test](https://github.com/ClearBlade/regression-js/blob/master/code/services/RegressionExample/RegressionExample.js) and you can refer to the [**Official Documentation**](https://github.com/mljs/regression) of that library to explore more options that you can use.  

## Assets

### Libraries 

| Library                   | Description                                             | Official Documentation             |
| ------------------------- | ------------------------------------------------------- | ---------------------------------- |
| ``` RegressionLibrary ``` | A Library Implementing Linear and Polynomial Regression | https://github.com/mljs/regression |

### Code Services

``` RegressionExample ``` : A code service to show working of Regression Library.

## Advanced 

### Transpilation to ES5

Follow these [steps](https://github.com/ClearBlade/Machine-Learning-Node-Libraries/blob/master/README.md#steps-for-transpilation-to-es5-1) for transpilation of any NPM package to ES5 so that the NPM package can be imported as a library in the clearblade code engine.
