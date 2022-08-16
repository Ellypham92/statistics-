## :bird: Gentoo Penguins

<img width="380" alt="Screen Shot 2022-08-16 at 11 11 44 AM" src="https://user-images.githubusercontent.com/64395120/184928087-200f4127-b6b5-40c4-a873-2c4c4a906854.png">

### :snowflake: Problem Statement:
The file* penguins.csv contains body measurements for over 100 Gentoo penguins observed in the Palmer Archipelago of Antarctica from 2007-2009. The images show what the measurements mean. Here we will work with bill length and flipper length to create predictive model.

### :ocean: Data:
- Using dim() to check the dimension and head() for a slice of the data
- Data dimension: 117 rows and   8 columns
<img width="700" alt="Screen Shot 2022-08-16 at 11 18 01 AM" src="https://user-images.githubusercontent.com/64395120/184929152-cd6ae74c-ef25-472f-a061-015114bb9660.png">

### :telescope: Modeling and Diagnotic:
- R libraries: **dplyr** for data manipulation, **magrittr** for pipe operator
- Fit a Simple Linear Rregresion model where bill length is the predictor and flipper_length is the response using lm() function <br>
:heavy_check_mark: See the results: <br>
<img width="400" alt="Screen Shot 2022-08-16 at 11 23 13 AM" src="https://user-images.githubusercontent.com/64395120/184930042-202572bd-a01f-49b7-b33c-2e077584d94c.png">

:heavy_check_mark: Visualization using plot() function:

<img width="700" alt="Screen Shot 2022-08-16 at 11 24 57 AM" src="https://user-images.githubusercontent.com/64395120/184930425-4bf6217e-38dc-4a6b-b985-744ae83fc448.png">

As we can see from the display of regression output, the model can explain the 45.34% of fliiper length on bill length. The estimate sigma (standard deviation of the errors) is 4.75245

- Use the model to answer these questions:  Which points have high leverage?  Which points are outliers?  Which points are influential based on Cook's distance?  
:heavy_check_mark: Diagnotic plots: <br>
<img width="700" alt="Screen Shot 2022-08-16 at 12 05 13 PM" src="https://user-images.githubusercontent.com/64395120/184937561-2e53da67-9e8e-402d-8d4c-111186896042.png">

:heavy_check_mark: Create a table for Leverage and Standardized Residuals  <br>
table <- data.frame(Case = 1:nrow(penguins), <br>
                    Diam = penguins$bill_length_mm,<br>
                    Distance = penguins$flipper_length_mm, <br>
                    Residuals = penguins.mod$residuals, <br>
                    leverage = lm.influence(penguins.mod)$hat, <br>
                    StdResiduals = rstandard(penguins.mod)) <br>

Output: <br>
<img width="500" alt="Screen Shot 2022-08-16 at 12 07 43 PM" src="https://user-images.githubusercontent.com/64395120/184938025-570dc0ca-5f16-475c-850b-ace8053dc6f3.png">

:heavy_check_mark:  Detect leverage_points <br>

subset(table, leverage > (4/nrow(penguins))) <br> 

:heavy_check_mark: Detect influential points using Cooks Distance <br>
subset(cooks.distance(penguins.mod), cooks.distance(penguins.mod) > 4/(nrow(penguins)- 2)) <br> 

Observations numbered as 11, 17, 62, 98, 102, 103, 111 are considered as high leverage. No outlier is found. Based on Cook's distance, we indentified observations numbered as  11, 66, 103  are influential points <br>

- Add curves for the fitted regression line, the boundaries of a 98% confidence interval for the regression line, and the boundaries of a 98% prediction interval for bill_length_mm <br>
<img width="700" alt="Screen Shot 2022-08-16 at 11 55 05 AM" src="https://user-images.githubusercontent.com/64395120/184935769-6d1f129d-1ed6-4563-8a0d-054517988670.png">

 As we can see in the plot, the blue lines color represents for the boundaries of a 98% confidence interval and the deeppink lines color represents for a 98% prediction interval; it is WIDER than the confidence interval boundaries. 
 
- Split the penguin data into two subsets, one for female penguins and one for males <br>
penguins.male <- penguins.exam %>% filter(sex == "male") ### males penguins  <br>
penguins.female <- penguins.exam %>% filter(sex == "female") ### female penguins 

- Make a plot with the data points and the fitted regression line for the two subsets <br>

:heavy_check_mark: Males penguins: <br>
<img width="600" alt="Screen Shot 2022-08-16 at 11 35 58 AM" src="https://user-images.githubusercontent.com/64395120/184932370-51d7d767-ed9d-4f73-9a20-ac7ad5327c34.png">

:heavy_check_mark: Females penguins: <br>

<img width="600" alt="Screen Shot 2022-08-16 at 11 37 05 AM" src="https://user-images.githubusercontent.com/64395120/184932565-78494111-d639-4cab-b335-611d17aff5f6.png">

We use summary() function to display the output, we learned thar the models for both males and females can explain the 24.69 %. The estimate sigma is 4.912 <br>

### :telescope: Prediction and Evaluation:
- Use the model to predict `flipper_length_mm` when `bill_length_mm` = 20.5 mm. We use predict() function <br>

predict.lm(penguins.mod, data.frame(bill_length_mm = 20.5))

By using the model, we can make the prediction that when value of bill_length_mm is 20.5 mm, the value for flipper_length_mm  is 177.5111  

-  Find the total sum of squares, the residual sum of squares, and the regression sum of squares based on `penguins.mod`. We use anova() for calculation

penguins.aov = anova(penguins.mod) <br>

SSR <- penguins.aov$`Sum Sq`[1] ## Regression sum of squares <br>
SSE <- penguins.aov$`Sum Sq`[2] ## Residual sum of squares <br>
SST <- SSR + SSE ## Total sum of squares <br>

The total sum of squares is 4751.812, the residual sum of squares is 2154.447, and the regression sum of squares is 2154.447 
