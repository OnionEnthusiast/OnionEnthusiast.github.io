# Bitcoin Price Action Predictor - [Back](/index.md)
## Motivation
After reading about the power of neural networks in image classification I began to ponder what other classification topics it could be useful for and naturally, as I had recently been looking into the viability of crypto mining, decided to look into the viability of a classification neural network in predicting price action for BTC. If there was an edge to be gained from this it could potentially be extremely profitable.

## Technologies
* Language: As I am the most familiar with python and it being a reasonably well equipped language for this type of problem that is what I decided to use as my language.
* Libraries: Considering data is extremely readily available on Kaggle in a csv format and the ubiquity of the library, I will be using pandas for the actual handling of data. For the model itself I will be using scikitlearn as it has a reasonably easy api to use for constructing ML models. For data visualization I will be using MatplotLib in order to gain a greater insight into weather or not the data actually beats simply just using a stochastic model.

*   The specific source for the data used can be found [here](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data).

[Top](#motivation)

## Methodology:
  1. [Data Pre-Formating & Labeling](#data-preformating-and-labeling)
  2. [Model Architecture & Training](#model-architecture-and-training)
  3. [Model Validation](#model-validation)
  4. [Comparison With Stochastic Methods](#comparison-with-stochastic-methods)
  5. [Conclusion](#conclusion)

[Top](#motivation)

## Data Pre-Formating and Labeling
The raw data provided by our source prevents several problems that must be addressed before the model can be labeled. Placing them in order of ease of solving we have:
1. Data shows price at a time stamp rather than the change in that price over that time period.
2. Data is non-normalized.
3. Missing lines in data.

### Data doesn't represent change in price.
Firstly, the data represents the current price. Sure we could look at multiple parts of the data point to understand how the price changes for that segment but what if we need a single number to represent the change for that time interval? The immediate obvious solution would be to take the difference of the opening and closing values (close – open) to get the delta in the price. However, due to the values still being rather large (on the order of dozens of dollars) this is sub optimal. This is because ML models are better able to learn from normalized data sets. A more optimal way to capture the change in value while conforming to the necessity for “well behaved” and normalized data can be derived from the fact that price action is often measured in percentage change. This can lead us to understand that one way to measure the change in price (while again maintaining the special properties) is by dividing the closing price by the opening price. This scales the data to a more manageable size and centers it at one.

### Data is non-normalized.
The previous step has thankfully done most of the work for normalizing the data. The data is already reasonably close to zero (as an artifact of the fact that btc doesn't have massive, ie: greater than 1000%,  minute to minute swings). All we have to do now is center the data on zero. If we observe the fact that the data is currently centered around one, as increases are result in a value >1,  decreases result in values between 1 and 0, and a stagnation or lack of change would result in a value of exactly 1, the most obvious solution would be to simply subtract one from each data point. Additionally it is worth noting that the values are extremely small and may be vulnerable to floating point errors due to the low volatility of btc as compared to other crypto-curriencies.

### Missing lines in data.
As with any data set in the real world there is bound to be internal inconsistencies and errors in the data collection process. In this case there are several lines where there was no data recorded. The solution I will be taking to this issue is to chunk the data into several pieces using the NaN rows as delimiters. This will ensure I have only contiguous data and will prevent the feeding of a NaN row into the model during training or validation.

### Labeling.
In order to label our data points we need to first understand the goal of the model, to predict the next time interval’s price action. In order to do this we will be using the price action of as many preceding data points as we can reasonably fit into memory. Thus we will be constructing an N length vector of previous price actions labeled with what was done, 0 for no change, +1 for increases, and -1 for decreases. For our use case I will be using N=8 due to the fact that my laptop does not have a lot of ram.


[Top](#motivation)

## Model Architecture and Training
For this project we will be using the MLPClassifier function from scikit-learn with two hidden layers, one of 64 neurons and one of 32 neurons. This should hopefully enable us to capture the majority of any existing complex relationships in the data. Additionally we will be using the ADAM solver, logistic activation function and one thousand itterations.
[image blocked:Image of the model creation code](/btc-nn/model_creation_code.png)

### Final Data Preperation
We will need 


[Top](#motivation)

## Model Validation

[Top](#motivation)

## Comparison With Stochastic Methods


[Top](#motivation)

## Conclusion

[Top](#bitcoin-price-action-predictor)
