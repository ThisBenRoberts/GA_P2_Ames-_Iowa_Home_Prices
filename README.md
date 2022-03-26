# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2 - Ames Housing Data and Kaggle Challenge

### Overview

Any item (a car, a book, a piece of fruit, or even a home) is truly only "worth" what someone else is willing to pay for it.   For one buyer, proximity to a school maybe a good thing. So they are willing to pay more for a home.  For another, a school nearby may be an unwanted nuisance, so they are willing to pay less.  For one buyer, a finished basement may be the chance to give their new home a personal touch, for another buyer it may mean a project they are unwilling to deal with. 

Additionally, home features, neighborhoods, building styles, and lot conditions can change from region to region, state to state, and city to city. In some locations in home heat maybe an unnecessary expense, while in others air conditioning may not be the norm. One neighborhood may have newer homes than another just across the street. Hilly terrains and homes with basements maybe the norm in east Tennessee, while in west Tennessee the land is flat and basements are unusual.

This creates the opportunity for a lot of unpredictable fluctuations in a home's final sale price. Trained, professional real estate brokers, agents, lenders, and investors get this wrong all the time.

The most common method for estimating a home's sale price is referred to as "running comps".  The process involves finding homes that have recently sold, or are currently on the market, with a similar age, size, location, and condition to our target property, and estimating the value of our target property based on these 'comparable' sales.  This can be done manually, as explained by [Nerdwallet](https://www.nerdwallet.com/article/mortgages/find-your-homes-value-do-your-own-comps-in-4-steps)  or outsourced a number of different ways. (Read more [here](https://www.nerdwallet.com/article/mortgages/how-to-determine-home-value))

Knowing that nuances exist in the market, and wanting a method that be truly called 'local' and 'proprietary', we've been asked to determine if it's possible to accurately predict home prices using sort of computer modeling, can we describe which home features have the greatest impact on that model, and can we do this using hyper-local sales data in Ames, Iowa.

---
### Problem Statement

We hypothesize that home prices can be accurately predicted using a computer model that leverages feature details specific to Ames, Iowa. Furthermore, we believe that we can describe what those features are as well as their expected impact to the home's final saleprice.


---
### Datasets

#### Provided Data

We were provided with 1 set of data that were used in this analysis. These datasets were 

* [`train.csv`](./datasets/train.csv): Training Data ([source](https://www.kaggle.com/c/dsir-0124-project-2-regression-challenge/data))


#### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|1st flr sf|int64|test.csv|First Floor square feet|
|2nd flr sf|int64|test.csv|Second floor square feet|
|3ssn porch|int64|test.csv|Three season porch area in square feet|
|alley|object|test.csv|Type of alley access to property|
|bedroom abvgr|int64|test.csv|Bedrooms above grade (does NOT include basement bedrooms)|
|bldg type|object|test.csv|Type of dwelling|
|bsmt cond|object|test.csv|Evaluates the general condition of the basement|
|bsmt exposure|object|test.csv|Refers to walkout or garden level walls|
|bsmt full bath|float64|test.csv|Basement full bathrooms|
|bsmt half bath|float64|test.csv|Basement half bathrooms|
|bsmt qual|object|test.csv|Evaluates the height of the basement|
|bsmt unf sf|float64|test.csv|Unfinished square feet of basement area|
|bsmtfin sf 1|float64|test.csv|Type 1 finished square feet|
|bsmtfin sf 2|float64|test.csv|Type 2 finished square feet|
|bsmtfin type 1|object|test.csv|Rating of basement finished area|
|bsmtfin type 2|object|test.csv|Rating of basement finished area (if multiple types)|
|central air|object|test.csv|Central air conditioning|
|condition 1|object|test.csv|Proximity to various conditions|
|condition 2|object|test.csv|Proximity to various conditions (if more than one is present)|
|electrical|object|test.csv|Electrical system|
|enclosed porch|int64|test.csv|Enclosed porch area in square feet|
|exter cond|object|test.csv|Evaluates the present condition of the material on the exterior|
|exter qual|object|test.csv|Evaluates the quality of the material on the exterior|
|exterior 1st|object|test.csv|Exterior covering on house|
|exterior 2nd|object|test.csv|Exterior covering on house (if more than one material)|
|fence|object|test.csv|Fence quality|
|fireplace qu|object|test.csv|Fireplace quality|
|fireplaces|int64|test.csv|Number of fireplaces|
|foundation|object|test.csv|Type of foundation|
|full bath|int64|test.csv|Full bathrooms above grade|
|functional|object|test.csv|Home functionality (Assume typical unless deductions are warranted)|
|garage area|float64|test.csv|Size of garage in square feet|
|garage cars|float64|test.csv|Size of garage in car capacity|
|garage cond|object|test.csv|Garage condition|
|garage finish|object|test.csv|Interior finish of the garage|
|garage qual|object|test.csv|Garage quality|
|garage type|object|test.csv|Garage location|
|garage yr blt|float64|test.csv|Year garage was built|
|gr liv area|int64|test.csv|Above grade (ground) living area square feet|
|half bath|int64|test.csv|Half baths above grade|
|heating|object|test.csv|Type of heating|
|heating qc|object|test.csv|Heating quality and condition|
|house style|object|test.csv|Style of dwelling|
|kitchen abvgr|int64|test.csv|Kitchens above grade|
|kitchen qual|object|test.csv|Kitchen quality|
|land contour|object|test.csv|Flatness of the property|
|land slope|object|test.csv|Slope of property|
|lot area|int64|test.csv|Lot size in square feet|
|lot config|object|test.csv|Lot configuration|
|lot frontage|float64|test.csv|Linear feet of street connected to property|
|lot shape|object|test.csv|General shape of property|
|low qual fin sf|int64|test.csv|Low quality finished square feet (all floors)|
|mas vnr area|float64|test.csv|Masonry veneer area in square feet|
|mas vnr type|object|test.csv|Masonry veneer type|
|misc feature|object|test.csv|Miscellaneous feature not covered in other categories|
|misc val|int64|test.csv|$Value of miscellaneous feature|
|mo sold|int64|test.csv|Month Sold (MM)|
|ms subclass|int64|test.csv|Identifies the type of dwelling involved in the sale.|
|ms zoning|object|test.csv|Identifies the general zoning classification of the sale.|
|neighborhood|object|test.csv|Physical locations within Ames city limits (map available)|
|open porch sf|int64|test.csv|Open porch area in square feet|
|overall cond|int64|test.csv|Rates the overall condition of the house|
|overall qual|int64|test.csv|Rates the overall material and finish of the house|
|paved drive|object|test.csv|Paved driveway|
|pid|int64|test.csv|Parcel identification number - can be used with city web site for parcel review.|
|pool area|int64|test.csv|Pool area in square feet|
|pool qc|object|test.csv|Pool quality|
|roof matl|object|test.csv|Roof material|
|roof style|object|test.csv|Type of roof|
|sale type|object|test.csv|Type of sale|
|saleprice|int64|test.csv|Sale price $$|
|screen porch|int64|test.csv|Screen porch area in square feet|
|street|object|test.csv|Type of road access to property|
|total bsmt sf|float64|test.csv|Total square feet of basement area|
|totrms abvgrd|int64|test.csv|Total rooms above grade (does not include bathroom|
|utilities|object|test.csv|Type of utilities available|
|wood deck sf|int64|test.csv|Wood deck area in square feet|
|year built|int64|test.csv|Original construction date|
|year remod/add|int64|test.csv|Remodel date (same as construction date if no remodeling or additions)|
|yr sold|int64|test.csv|Year Sold (YYYY)|

---

### Analysis Summary

For this analysis, previous sales data as recorded and reported from home sales in Ames, Iowa were examined.  The data included quantifiable metrics such as the number of bathrooms, bedrooms, living area square footage.  The data also included more subject qualitative data such as overall quality and garage conditions, as well as objective descriptive data points such as the presence of air conditioning, and type of building. After some initial cleaning, we looked at our sample data and the correlations of each data point to the salesprice in order to determine if a relationship existed and to what degree.  We considered both positive and negative as goal is an accurate prediction of the final price of a home, meaning the net impact of all features needed to be included. A positive correlation is one in which the presence of a feature or additional units of a feature tended to indicate an increase in the final saleprice.  A negative correlation is one in the which the presence of a feature or additional units of a feature tended to indicate a lower final saleprice. A model was built and tested based on those correlations.  

---

### Conclusions & Recommendations

There is indeed a correlation between every data point we were provided and the final saleprices weobserved.  While the trend appears to be stronger for some features than others, in total it is possible to build a computer model based on those correlations to accurately predict final saleprices.  Furthermore, we can identify and estimate the impact of those features on the final saleprice.  

Additionally, our model did prove to be accurate a little over 90\% of the time. In its current form, we believe that it could be used as a reliable jumping off point to predict the final saleprice of a home. However, the model was built on data generated from one geographic location so it should NOT be used in an attempt to predict home prices outside of Ames,Iowa. Further, we do believe that the 90\% accuracy score could be improved upon given more time.

Given our time constraints, a lot of missing data were filled in with 0's. We suspect that the model and resulting predictions may be better improved by considering a combination of features to estimate that missing data.  For example, where the lot frontage was missing, we looked at the shape of the lot, then the average lot frontage for lot of a similar shape and estimated our missing numbers. As a result, we would recommend spending more time understanding the missing data and attempting to make informed estimates before relying solely on the predictions made by our model.  


