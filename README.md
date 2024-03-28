# Stock-Forecasting-Using-LSTM
Here's a breakdown of the key components and steps of the project:

## Data Preparation

1)Preparing the DataFrame: The function prepare_dataframe_for_lstm transforms the input DataFrame by creating lag features from the 'Close' price column, essentially creating historical price data points (e.g., Close(t-1), Close(t-2), etc.) as new features. This process is crucial for time series forecasting, where past values are used to predict future ones.
2)Scaling the Data: The data is scaled to a range of -1 to 1 using MinMaxScaler. This normalization step helps improve the convergence of the training process by ensuring that all features contribute equally.
3)Splitting the Data: The dataset is split into training and test sets, maintaining the temporal order of the data. This allows the model to be trained on past data and evaluated on unseen future data.
4)Reshaping the Data: The input data is reshaped to fit the LSTM model's expected input shape, which is [samples, time steps, features]. In this case, each sample is a sequence of lagged 'Close' prices.

## LSTM Model

1)Defining the Model: The LSTM class defines the neural network architecture, including an LSTM layer for processing sequences of data and a fully connected layer to output the predicted stock price.
2)Training the Model: The training process involves running the model through the training dataset multiple times (epochs), adjusting the model weights to minimize a loss function (Mean Squared Error Loss) using the Adam optimizer. The data is fed in batches to optimize the training process.
3)Evaluation and Prediction: The model's performance is evaluated using the test set. Predictions made by the model on the training and test sets are compared against the actual stock prices to assess its forecasting accuracy.
4)Visualizing Results: The project includes visualizations of the actual vs. predicted stock prices, providing a clear way to assess the model's performance visually.

## Additional Steps

1)Data Loader: A PyTorch DataLoader is used for batching the data, which improves the efficiency of model training by allowing for parallel processing and reducing memory usage.
2)Training and Validation Loop: Detailed training and validation loops are implemented to train the model and monitor its performance on both the training and test data across epochs.
3)Inverse Transformation: Predictions made by the model are scaled back to their original range using the inverse transformation of MinMaxScaler to compare them with the actual stock prices accurately.
4)Final Evaluation: The project concludes with a comparison of scaled-back actual and predicted prices for both training and testing phases, providing a comprehensive evaluation of the LSTM model's forecasting ability.


Overall, this project showcases the application of LSTM neural networks for stock price forecasting, emphasizing data preprocessing, model training, and evaluation techniques.
