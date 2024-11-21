# <p align="center" style="font-size: 60px;"><strong>Technical Assignment</strong> </p> 

<p align="center">
  <a href="##introduction">Introduction</a> |  
  <a href="#models">Models </a> | 
  <a href="#hyperparameter-tuning-andlearning-optimisation">Hyperparameter Tuning and Learning Optimization </a> |
  <a href="#performance-evaluation">Performance Evaluation</a> | 
</p>


## Introduction

This repository contains an analysis tool for forecasting the monthly industrial production of Electric and Gas Utilities in the United States. This sector is a significant contributor to fluctuations in national output over the course of the business cycle. By examining the industrial production (IP) index, which measures the real output of establishments located in the U.S. (excluding territories), we gain insights into structural developments within the economy. This forecasting project aims to leverage historical production data to predict future trends.

For more information, refer to the [explanatory notes issued by the Board of Governors](https://fred.stlouisfed.org/series/IPG2211A2N).

## Code Architecture

The project is organized into the following Jupyter notebooks, chosen for their ability to visualize and interpret results efficiently:

- **data_preparation.ipynb**: This notebook contains analysis and methods for preprocessing data, preparing it for model training.
- **model_selection.ipynb**: This notebook covers the model selection process, where models are trained, compared, and evaluated.

For the forecasting task, we opted to use **LSTM (Stacked LSTM)** and **CNN-LSTM** models, both of which are well-suited for time series prediction tasks.

## Hyperparameter Tuning and Learning Optimization

We opted to use Optuna with TimeSeriesSplit in order to find the best parameters for the Stacked LSTM model. Both models were trained using cross-validation, which showed good performance for both of them.


## Results

Below are some of the results produced by the models:

### Stacked LSTM - Metrics Curves and Predictions

<div align="center">
  <table>
    <tr>
      <td><img src="./media/lstm_optimal_curve.png" width="300" /></td>
      <td><img src="./media/lstm_optimal_prediction.png" width="300" /></td>
    </tr>
  </table>
</div>

### CNN-LSTM Results - Metrics Curves and Predictions

<div align="center">
  <table>
    <tr>
      <td><img src="./media/cnn_lstm_curve.png" width="300" /></td>
      <td><img src="./media/cnn_lstm_prediction.png" width="300" /></td>
    </tr>
  </table>
</div>

### Model Performance Metrics

| Metric   | Stacked LSTM | CNN-LSTM |
|----------|--------------|----------|
  | MAE      | 4.36     |  3.95 |
| RMSE     | 5.24     | 4.91  |

The evaluation table showcases the performance of each model, with the Stacked LSTM model demonstrating a strong balance between training and generalization capabilities, making it our chosen model for real-time forecasting
While both models demonstrate promising results, the CNN-LSTM exhibits smoother performance and lower error metrics compared to the stacked LSTM, making it the preferred choice for deployment.
