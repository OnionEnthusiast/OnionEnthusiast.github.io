# Bitcoin Price Action Predictor - [Back](/index.md)
## Motivation
After reading about the power of neural networks in image classification I began to ponder what other classification topics it could be useful for and naturally, as I had recently been looking into the viablity of crypto mining, decided to look into the viability of a classification neural network in predicting price action for BTC. If there was an edge to be gained from this it could potentially be extreamly profitable.

[Top](#bitcoin-price-action-predictor)

## Technologies
* Language: As I am the most familiar with python and it being a reasonably well equiped language for this type of problem that is what I decided to use as my language.
* Libraries: Considering data is extremely readily avalible on [Kaggle](https://www.kaggle.com/) in a csv format and the ubiquity of the library, I will be using [pandas](https://pandas.pydata.org/) for the actual handling of data. For the model itself I will be using [scikitlearn](https://scikit-learn.org/stable/index.html) as it has a reasonably easy api to use for constructing ML models. For data visualisation I will be using [MatplotLib](https://matplotlib.org/) in order to gain a greater insight into weather or not the data actually beats simply just using a stochastic model. The specific source for the data used can be found [here](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data).

[Top](#bitcoin-price-action-predictor)

## Methodology:
  1. [Data Preformating & Labeling](#data-preformating-&-labeling)
  2. [Model Training](#model-training)
  3. [Model Validation](#model-validation)
  4. [Comparison With Stochastic Methods](#comparison-with-stochastic-methods)
  5. [Conclusion](#conclusion)

[Top](#bitcoin-price-action-predictor)

## Data Preformating & Labeling
The raw data provided by our source prevents several problems that must be addressed before the model can be labled. Placing them in order of ease of solving we have:
1. Data shows price at a time stamp rather than the change in that price over that time period.
2. Data is non-normalized.
3. Missing lines in data.

### Data doesnt represent change in price.
Firstly, the data represents the current price. Sure we could look at multiple parts of the data point to understand how the price changes for that segment but what if we need a single number to represent the change for that time interval? The best solution I could come to is to divide the close by the open to give some sense of percentage change. This now represents the change in price over that interval.

### Data is non-normalized
The previous step has thankfully most of the work for normalizing the data for us. The data is already reasonably close to zero (as an artifact of the fact that btc doesn't have massive minute to minute swings). All we have to do now is center the data on zero. If we observe the fact that the data is currently centered around one, increases are result in a value >1 after the previous step and decreases result in values <1 but >0. Additionally it is worth noting that the values are extreamly small and may be vulnrable to floating point errors. Thus the logical nex step is to pass them into a logorithm as a final normalisation step.

### Missing Lines in data
In order to solve this problem the data will need to be chunked into sections of consecutave non missing lines, then the labling process will be applied to each of these chunks to provide us with a large dataframe of data that is ready to be used for training.

### Labeling
For our purposes we will be selecting an arbitrary number of data points to use as the input data for both training and prediction, in this instance it appears that 8 input datta points for each output point is about as much as my laptop can hold in memory. The way we will be selecting input datapoints will be to take the 8 preceeding data points. The catagories for the labels will be whether the data point is increasing (1) or decreasing (0).

[Top](#bitcoin-price-action-predictor)

## Model Training

[Top](#bitcoin-price-action-predictor)

## Comparison With Stochastic Methods

[Top](#bitcoin-price-action-predictor)

## Conclusion

[Top](#bitcoin-price-action-predictor)
