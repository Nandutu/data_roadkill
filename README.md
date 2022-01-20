# data_roadkill
The daily total roadkill data on South African Highways showing Species name, date of road mortality, number of roadkill incidence, Class, Order, and Family

# Where we got the daily roadkill data.
We converted the monthly data to Daily roadkill data.
We collected from previous research published as roadkill cases from 2011 to 2014 in South Africa.

https://doi.org/10.3957/056.045.0301

https://www.frontiersin.org/article/10.3389/fevo.2018.00015

https://doi.org/10.1111/aje.12628

# Notebooks

## arima_only.ipynb

1. The actual data is input in the notebook, visualized, non-stationary data made stationary.
2. The stationary (transformed) data is input in the ARIMA(5,0,2) and AR(5,0,0) model orders to generate ARIMA-only and AR-only predictions
3. Predictions from linear models are interpolated to allow the actual data to fix the predicted data
4. The residuals from the linear models are computed, and output is input to gridsearch_lstm_only.ipynb file 


## gridsearch_lstm_only.ipynb

Parameters are fine-tuned, and the file captures residuals from 
1. ARIMA-only residuals to capture the nonlinear patterns in the data, which are later corrected
2. AR-only residuals to capture the nonlinear patterns in the data, which are later corrected
3. Actual data to LSTM-only to capture the nonlinear patterns


## error_correction_and_plots.ipynb

This file visualizes plots and corrects the error by combining the ARIMA-only predictions in arima_only.ipynb file plus the residual error predictions from gridsearch_lstm_only.ipynb file.

The result of the computations is an ARIMA-LSTM correction ie prediction. This study has run experiments on only hybrid (s) ARIMA-LSTM and AR-LSTM hybrid models.
