Project Description
Analysis of House Sales in a King's County


Project Overview
Primetime Realtors situated in the heart of a North Western County acts as the conduit for transforming home ownership aspirations into tangible realities. Committed to unwavering excellence and employing data-driven methodologies, the agency aspires to lead the way in achieving optimal pricing and facilitating successful real estate endeavors. Its overarching objective is to surpass traditional limitations by leveraging technology and analytical insights to revolutionize the real estate landscape as we perceive it.


Business Problem

In our role at a real estate agency, we are examining data from the Kings County House Sales dataset to advise our agency on strategies to boost home values in Kings County through renovations. Our goal is to identify the most impactful renovation factors that can enhance a home's value. By pinpointing these factors, our agency can effectively guide homeowners in maximizing their profits when selling their homes.


The Data

This project uses the King County House Sales dataset, which can be found in kc_house_data.csv in the data folder in this assignment's GitHub repository. The description of the column names can be found in column_names.md in the same folder. As with most real world data sets, the column names are not perfectly described, so you'll have to do some research or use your best judgment if you have questions about what the data means.

Data Cleaning
Next, we chose to clean our data by dropping unnecessary columns that would not help us achieve the result we were aiming for. These columns included:

id
date
waterfront
view
grade
sqft_above
sqft_basement
yr_renovated
zipcode
lat
long
sqft_living15
sqft_lot15
After dropping these columns, the remaining columns we we experimenting were:

price
bedrooms
bathrooms
sqft_living
sqft_lot
floors
condition
Waterfronts

 
After examining the data types of each column, we identified the only non-numeric column as "condition." To handle this, we transformed the "condition" column using one-hot encoding, which split it into subcategories: cond_avg, cond_fair, cond_good, cond_poor, and cond_verygood, all of which were converted to float data types.

Next, we categorized the remaining columns into separate arrays based on whether they were continuous or categorical variables. we then proceeded to analyze each array individually: for categorical variables, we generated histograms, while for continuous variables, we created a scatter matrix to explore their relationships further.


Data Preparation


To ensure the integrity of our target variable, "price," we employed the train-test split method to normalize it, separating it from the original dataframe and assigning it to "y," while designating the remaining variables as "X".

Following the normalization of the target variable, we constructed a heatmap to visualize the correlations between all columns and the target variable, "price." This heatmap revealed that "sqft_living" exhibited the highest correlation. To validate this correlation further, we  utilized cross-validation, which demonstrated a minimal discrepancy of about 0.01 between the training and validation scores, indicating a robust model.

Lastly, in the preparation phase, we crafted two models: one showcasing the variables ranked by their correlation strength with the target variable and another displaying a scatter matrix of all variables. This approach aimed to highlight any non-normal distributions, thereby guiding the normalization process for the modeling stage.


Modeling


Based on our models baseline model, utilizing a simple linear regression, established the initial understanding of the relationship between the square footage of living space and house prices. From the simple linear model, it was observed the model wasn't the best for this analysis. The model's R2 value was extreemly low, indicating that there are other numerous factors in housing that affect the house prices. These results showed that another iteration was needed. In the second model OneHot Encoding was introduced to convert the categorical variables to binary representation which is suitable for machine learning algorithms. The second model certainly improved from the baseline model, meaning that at least one of the independent variables has a significant effect on the dependent variable. To further improve the model, a third iteration was needed, In this model, Log Transformation was introduced to reduce skewness. The results from this iteration reduced skewness while simultaniously increasing the R2 making the model highly significant. The final model, a multiple linear regression, incorporated additional features to improve the predictive power. Evaluation metrics such as R-squared and F-statistic were used to assess the model's performance and significance. In this model, insignificant variables were dropped to achieve the highest prediction power of the models. The results gotten from this model's summary displayed the highest R2 value, and the best fit of residuals to a normal distribution.


Conclusion

 The multiple linear regression model is better than the simple linear regression model because The multiple linear regression model has a slightly higher R-squared value (0.498) compared to the simple linear regression model (0.498 vs. 0.473). A higher R-squared value indicates that the multiple linear regression model explains a larger proportion of the variance in the target variable (house prices) compared to the simple linear regression model.

 Furthermore, the analysis revealed that the most influential predictor of home prices was indeed "sqft_living", aligning with our initial expectations. 

 Moving forward, I believe it would be beneficial to incorporate additional predictive factors beyond "sqft_living" and "sqft_lot." By expanding the scope of factors considered, we can gain deeper insights into other home renovation aspects that contribute to enhancing home values.














