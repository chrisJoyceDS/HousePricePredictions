README!

### Overview

This README Covers:
- Background
- Problem Statement
- Data Dictionary
- Brief Summary of Analysis
- Conclusions and Recommendations
- File Structure
- Sources
- Powerpoint Presentation

## Problem Statement:
You've been hired by a new brokerage in Ames, Iowa called Aimless Real Estate LLC. Aimless has hired you as a datascientist to analyze data on property sales over the years to help them identify key properties to target for their services. This is not a very technical audience, as such your challenge is to identify any patterns between a house's value and its costs in relation to a predicted sales price, and be able to describe this information in a way your client will understand.

<h1>Data Dictionary</h1>

All Features Included in both hypothesis models and the initial model:
|Feature|Type|Dataset|Description|
|:---|:---:|:---:|---:|
|**id**|*int*|train|Index of the observation|
|**overall_qual**|*int*|train|Rates the overall material and finish of the house|
|**overall_cond**|*int*|train|Rates the overall condition of the house|
|**mas_vnr_area**|*int*|train|Masonry veneer area in square feet|
|**bsmtfin_sf_1**|*int*|train|Type 1 Basement total finished square feet|
|**bsmtfin_sf_2**|*int*|train|Multiple Types Basement total finished square feet|
|**bsmt_unf_sf**|*int*|train|Total unfinished basement square feet|
|**total_bsmt_sf**|*int*|train|Total square feet of basement area|
|**lot_area**|*int*|train|Lot size in square feet|
|**lot_frontage**|*int*|train|Linear feet of street connected to property|
|**1st_flr_sf**|*int*|train|Total first floor square feet|
|**2nd_flr_sf**|*int*|train|Total second floor square feet|
|**low_qual_fin_sf**|*int*|train|Low quality finished square feet (all floors)|
|**gr_liv_area**|*int*|train|Above grade (ground) living area square feet|
|**garage_area**|*int*|train|Size of garage in square feet|
|**wood_deck_sf**|*int*|train|Wood deck area in square feet|
|**open_porch_sf**|*int*|train|Open porch area in square feet|
|**pool_area**|*int*|train|Total Pool Squarefeet|
|**saleprice**|*int*|train|Sale price in USD|
|**exter_qual**|*object*|train|Exterior covering on house|
|**exter_cond**|*object*|train|Evaluates the present condition of the material on the exterior|
|**bsmt_qual**|*object*|train|Evaluates the height of the basement|
|**bsmt_cond**|*Object*|train|Evaluates the general condition of the basement|
|**heating_qc**|*object*|train|Heating quality and condition|
|**kitchen_qual**|*object*|train|Kitchen quality|
|**fireplace_qu**|*object*|train|Fireplace quality|
|**garage_qual**|*object*|train|Garage quality|
|**garage_cond**|*object*|train|Garage condition|

---

## Brief Summary of Analysis

#### From the data provided, we were able to find several positive correlations between square feet (captured in squarefeet) as well as even distributions of categorical features, mainly quality and conditions of different aspects of a property for sale. 
 
#### After visualizing the data through scatter plots, bar charts, and histograms the relationships started to lose their weight making early trouble for our hypothesis. We bet that features more closely related to depreciating aspects of property ownership would be better predictors of sale prices. One of the areas that Quality and Condition features started to lose their ground was when visualized as a histogram; more often than not individual Qual/Cond features were not normally distributed with the majority of their respective count in one or two majorities.

#### Squarefeet Features seemed promising as good predictors for sale price with their moderate/strong positive correlations to price. However once we calculated the Variance Inflation Factor on all numerical features, we saw that most of the features that leaned closer to strong positive correlations, also suffered from multicollinearity, sometimes reporting a VIF of infinity. After we succesfully modeled using MultiLinearRegression, Ridge CV and ElasticNetCV, we saw that our hypothesis was significant enough to disprove the null hypothesis.

---

## Conclusions & Recommendations

### Hypothesis Conclusion Statement:<br>
#### Because none of the differences taken by mean RMSE scores were larger than our level of significance = 0.05, there is insufficient evidence to reject our null hypothesis. We do not have enough evidence to conclude that Quality and Condition Features are better predictors of sale price than Squarefeet based features.


## Conclusions:
- ### From the current iteration of the model and data, there is not ample enough evidence to suggest that Quality/Condition nor SquareFt Feature based fields are the best predictors of price.
- ### Quality and Condition Features range further than just Features that reference quality or condition in their name.
- ### Squarefeet based features are also not entirely reliable on predicting potential sale price points either. As seen in EDA and further the performance of the models, Squarefeet Features have a very high multicollinearity with other Squarefeet Features which ultimately creates more noise than it does highlight the signal.
- ### Despite postive Linear relationships between individual Quality,Condition,Squarefeet features and Sale Price, more features need to be included in order to accurately predict sale prices that better tie the entire picture together, potentially such as numbers of category rooms (baths, bedrooms, etc.) as well as adding features that detail home/bldg style.

## Recommendations:
- ### Fund another round of analysis on the data to take lessons learned and reapply to better understand the data and create a model that is less restrictive of features it includes.
- ### When creating future models that predict price, ensure that the parameters set in cross validation models don't test models in a similar fashion.
- ### Continue to focus on features that represent non-depcreciative value such as Squarefeet as they tend to have strong positive correlations with price.
- ### When considering Quality/Condition Features, focus on instances of Heating quality and basement height as they are more evenly distributed than their peer features such as Garage Quality, Kitchen Quality, and Fireplace quality.

---

File Structure:
1. Code:
    a: 01_file_clean.ipynb - Project 2 Data Cleaning
    b: 02_eda_viz.ipynb - Project 2 Exploratory Data Analysis and Visualization
    c: 03_modeling_conclusion - Project 2 Preprocessing, Feature Engineering, Modeling and Conclusion
2. datasets:
    a: cleaned_datasets - Output folder for cleaned data sets from 01_file_clean.ipynb
        i: cleaned_test.csv - Copy of Cleaned Test Data Set from 01_file_clean.ipynb
        ii: cleaned_train.csv - Copy of Cleaned Trained Data Set from 01_file_clean.ipynb
    b: test.csv - Test Data Set
    c: train.csv - Train Data Set
3. kaggle_submissions
4. README.md

---

## Sources
1. https://www.investopedia.com/terms/z/zscore.aspf - Used for understanding and quoting z-score

---
Google Slides Presentation: https://docs.google.com/presentation/d/1KnR-ljWhMa2oQ5p9I0meKfI51DhHL3RTE7bS79gfDV4/edit?usp=sharing
---
