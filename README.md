
The main objective of air pollution data is to predict annual average air pollution concentrations of various cities in the U.S. using predictors such as data about population density, urbanization, road density, as well as satellite pollution data and chemical modeling data. In the dataset, there are 48 attributes/features with values for each of the 876 monitors (observations). 

The value column indicates the PM2.5 concentration level average of fine particles/volume of air for 876 gravimetric monitors for 2008. 

To predict annual average air pollution concentrations, you are required to cover the following stages:

Stage 1 – Exploring data

1.	Explore data, provide a descriptive analysis of the variables, and decide if you need to transform the variables to the right formats. 
2.	How many states are there in the dataset?
3.	How many stations are there per city?
4.	Conduct a correlation test and provide the results focusing on highly correlated pairs.


Stage 2 – Pre-processing the dataset with a view to develop models:

Split the dataset into training and testing using the rsample package of R. The requirement for splitting the data is to use the ratio of 2:3. 
5.	Report on the size of both datasets. Check the proportion of cities for both datasets. 
6.	Report if there is an issue with the datasets. 
7.	Propose a meaningful way to bin the types of cities.

Build a recipe or pipeline using the recipes package using the following steps on the training set:

8.	Give ‘value’ variable the outcome role
9.	Give ‘id’ variable a role of ‘id variable’
10.	Give ‘fips’ variable a new role of id variable that is ‘county id’ as it is also an id variable only
11.	Next create a dummy variable with one hot encoding using the function step_dummy() in the recipe. Pass variables state, county, city, zcta to be converted into dummy variables using one hot encoding.
12.	Add step_normalize() for all predictors to normalize the data.
13.	Now as in starting we saw lot of variables have high correlation. This issue can be solved using recipe. Use step_corr() to remove variables with high correlation. Note exclude ‘CMAQ’ and ‘aod’ variable from correlation checking as we need these variables for prediction.
14.	Next remove variables with nonzero variance. These are the variables which have very similar values. This can be done by adding step_nzv() in recipe. In this also exclude ‘CMAQ’ and ‘aod’ variable.
15.	Next use prep() and bake() to apply this recipe to training and testing dataset and extract the transformed training and testing dataset. Note while using prep() for training dataset keep retain= TRUE in order to extract the training dataset with bake().

Following the above steps, you should obtain a new dataset with 38 numerical variables. 

Apply the same steps to the test set.
Stage 3 - Building models for prediction and classification

In this stage, there are 3 models that need to be built. Linear Regression technique is used for Model 1. LDA is used for Model 2. Random Forest is used for Model 3.
16.	Use linear regression to build a model (called model 1) and perform the prediction on the test dataset and calculate RMSE and MAE.

17.	Use LDA to classify. To build an LDA model, you need to create a dummy variable to convert air pollution to ‘AQI Category’. The threshold for AQI Category is shown in (attached)

Perform LDA on the training set. Comment on the results of LDA.
Produce a confusion matrix and accuracy rate.
Check the performance of LDA on the test set and make comments.


18.	Use Random Forest to classify AQI category.
Apply random forest on the training and testing sets. 
Report RMSE and MAE and compare those results with Model 1. 


Stage 4 – Conclusions and Recommendations
19.	Make conclusions related to pros and cons of predictive techniques and classifications.
20.	Make conclusions on the rsample and recipes packages to answer the reason as to why these 2 packages are used.
21.	Make recommendations for other experts in the data analytics field as to what lessons have been learnt to attain a high prediction rate.



