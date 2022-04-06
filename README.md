# Linear Regression Model For AH Absolute Humidity
## To Predict Humidity based on substances in the air

### Project Details
The Project aims to train a predictive model to obtain a model for AH Absolute Humidity.

## Response and Predictor Variables’ Details and Derivations
(Before Training of Model)

**Response Variable:** AH Absolute Humidity

**Predictor Variables:** NO2(GT), PT08.S4(NO2), T, RH 

**Dropped Variables:** NMHC(GT), CO(GT), PT08.S1(CO), C6H6(GT), PT08.S2(NMHC), NOx(GT), PT08.S3(NOx), PT08.S5(O3)

The data set contained missing values that were tagged with -200 value.  The columns expressions node had to be used to change the -200 value to real missing values of “?” which were then treated using the missing value node. NMHC(GT) was a variable in the data set that had to be dropped because it had too many missing values. For the rest of the missing values for the other variables(columns), I chose to use linear interpolation since there were many values in the columns which could be used to derive the missing values. An assumption of Linear Regression analysis is that there should be no multicollinearity between variables. As The variables CO(GT), PT08.S1(CO), C6H6(GT), PT08.S2(NMHC), NOx(GT), PT08.S3(NOx), PT08.S5(O3) were found to display high multicollinearity, they were also dropped.

(After Training of Model)

**Predictor Variables (Interaction Terms Created):** NO2(GT) Squared, PT08.S4(NO2) Squared, T Squared, RH Squared

After running a Knime Linear Regression model and plotting a residual scatter plot, it showed a curved residual pattern. This suggested there might be a need to fit a polynomial of some order to explain this curved pattern of residuals. As such, interaction terms of the squared value of the different variables were created, and this had the effect of increasing the R^2 value which simply meaned that there was an increase in the strength of the linear relationship between the variables. The math column (multi column) node was used to square the existing columns of data. 

## Predictive Models Used and Performance Evaluation Statistics
**Knime Multiple Regression Model**
<br /> R^2 = 0.94
<br />Adjusted R^2 = 0.94

**H20 Ridge Regression Model**
<br /> R^2 = 0.948

**H20 Lasso Regression Model**
<br /> R^2 = 0.948

**K Fold Cross Validation Regression Model**
<br /> R^2 = 0.943

Using a Knime multiple regression model, a high value of R^2 of 0.94 is obtained which suggests that the predictor variables have a strong linear relationship with the response variables.

Using the Ridge and Lasso regularisation models, the R^2 is further improved to 0.948. 

Using a 10 Fold Cross Validation Regression Model, the R^2 is also improved albeit by a smaller amount to 0.943.

Based on the comparison of the R^2 values, it appears that the Ridge and Lasso regularisation models are the best at predicting the response variable as it has the highest R^2 values.

## Most Important Features in Determining The Response Variable
The p values of the predictor variables are the most important aspect to look at in determining the response variable. Predictor variables which have P values lesser than 0.05 or are close to 0 are significant predictors of the response variables. Predictor variables which have P values of greater than 0.05 are taken to be insignificant as there is no evidence that the variable has an effect on the response.

![image](https://user-images.githubusercontent.com/102946848/161669207-a8a07b7b-5c2d-4a7e-9f39-fdbccd721fa9.png)

Predictor Values: NO2(GT), PT08.S4(NO2), T, RH, NO2(GT) Squared, PT08.S4(NO2) Squared, T Squared, RH Squared

Therefore, all the predictor variables used which are also the features, are all equally important in determining the response variable as they all have P values close to 0.

*Analysis powered by KNIME Analytics Platform*
<br /> *KNIME Workflow: [https://github.com/genephua/KNIME-LinearRegression/blob/main/Linear%20Regression%20Model%20-%20Air%20Quality.knwf](https://github.com/genephua/KNIME-LinearRegression/blob/main/Linear%20Regression%20Model%20-%20Air%20Quality.knwf)*
<br /> *Data Source: [AirQualityUCI.xlsx](https://github.com/genephua/KNIME-LinearRegression/blob/main/AirQualityUCI.xlsx)*









