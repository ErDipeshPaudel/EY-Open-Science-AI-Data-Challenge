# EY-Open-Science-AI-Data-Challenge

Summary on major steps on this challenge:
We read description of challenge
We downloaded data provided on challenge and looked at the data
Combined multiple datasets to enhance model performance
Created meaningful features like Heat Index and Building Density
Used GeoPandas and Shapely for location-based insights
Used Random Forest for its robustness and accuracy
Then we achieved high accuracy with careful data preparation and feature selection

This is the Complete Guide to Solving the EY Open Science AI & Data Challenge: Cooling Urban Heat Islands, you just need basic understanding of python programming and you are ready to jump into the project, you will learn all the materials along the way 
while doing the project. 

Hope this might help you:

The goal of this challenge is to predict the Urban Heat Island (UHI) Index for specific locations in New York City by using meteorological data, building footprint data, and satellite observations which they already provided us. Now we aimed to build an accurate machine learning model and generate a submission file that meets the competition’s requirements.

#We will use Jupyter Notebook For interactive coding and visualization,

#Tech Stack we will be using for this project are,
Programming Language: Python
Libraries for Data Handling: Pandas, NumPy
Libraries for Data Visualization: Matplotlib, Seaborn
Geospatial Analysis: GeoPandas, Shapely
Satellite Data Handling: Rasterio, Xarray, Rioxarray
Machine Learning: Scikit-learn (RandomForestRegressor)
Model Evaluation: Scikit-learn (R² Score, RMSE)


#Major Steps to Complete the Project

1. First we go through all the data that are provided in the challenge and try to understand the problem, you can download the data from data descripiton section of the challenge in official EY company challenge. (https://challenge.ey.com/challenges/the-2025-ey-open-science-ai-and-data-challenge-cooling-urban-heat-islands-external-participants/data-description)

2. Project Setup: Installed necessary Python libraries using !pip install pandas numpy matplotlib seaborn rasterio geopandas scikit-learn xarray rioxarray odc-stac pystac-client planetary-computer keras

Verified the availability of all datasets provided for the challenge

2. Data Loading and Exploration
Loaded the UHI training dataset (Training_data_uhi_index_2025-02-18.csv) using Pandas
Note: Make sure you downloaded this updated training dataset because previous data had the error init and EY Challenge officials later updated new dataset.
Then, Load the weather data from NY_Mesonet_Weather.xlsx, including temperature, humidity, wind speed, wind direction, and solar flux.
Inspected the datasets for missing values and data types

3️. Data Preprocessing
Converted datetime columns into proper datetime format
Merged the UHI training data with weather data based on the nearest timestamps
Handled missing values in the merged dataset

4️. Feature Engineering
Created new features like,
Heat Index: A calculated feature combining air temperature and relative humidity
Time-Based Features: Extracted hour, day of the week, and month from the datetime column
Building Density: Counted the number of buildings within a 100m buffer around each UHI data point using GeoPandas and Shapely

5️.Data Visualization
Visualized the distribution of UHI Index values using Seaborn
Created heatmaps and scatter plots to understand feature relationships
Plotted the UHI Index on a map to identify hotspot areas

6️. Model Training and Evaluation
Split the data into training and validation sets (80% train, 20% validation)
Trained a Random Forest Regressor from Scikit-learn on the engineered features

Then we evaluated model performance using:
R² Score: Measures how well the model explains the variance in UHI Index
RMSE (Root Mean Squared Error): Measures the average prediction error

Achieved high accuracy with an R² score of 0.9679 and RMSE of 0.0029

7️. Handling Missing Data in Submission Dataset
Loaded the submission template (Submission_template.csv)
Merged it with the weather and building data
Handled missing features using Nearest Neighbors Interpolation from Scikit-learn

8️. Prediction and Submission File Generation
Predicted UHI Index values for the submission locations using the trained model
Formatted the results to match the competition’s submission requirements
Saved the final predictions as final_submission.csv

#Note: about Random Forest Regressor Model

This is how Random Forest Regressor works which I copied from LLM Copilot AI:
A "random forest regressor model" is a supervised machine learning algorithm that uses an ensemble of multiple decision trees to make predictions on continuous target variables (regression), where each tree is built on a random subset of the data, and the final prediction is the average of all the individual tree predictions, effectively reducing variance and improving model accuracy compared to a single decision tree; it is considered a powerful tool for handling complex non-linear relationships in data. 
Key points about random forest regressor:
Ensemble learning:
It combines multiple decision trees to create a more robust model. 
Bagging technique:
Each decision tree is built on a random sample (bootstrap sample) of the data, introducing randomness and preventing overfitting. 
Feature selection randomness:
At each split in a decision tree, only a random subset of features is considered, further diversifying the trees. 
Averaging predictions:
The final prediction is the average of the predictions made by all the individual decision trees. 
How it works:
Data splitting: The training data is randomly divided into multiple subsets. 
Tree building: For each subset, a decision tree is built using a random selection of features at each split. 
Prediction aggregation: Once all trees are built, each tree makes a prediction for a new data point, and the final prediction is the average of all these individual predictions. 
