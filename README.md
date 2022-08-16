## :bird: Gentoo Penguins

<img width="380" alt="Screen Shot 2022-08-16 at 11 11 44 AM" src="https://user-images.githubusercontent.com/64395120/184928087-200f4127-b6b5-40c4-a873-2c4c4a906854.png">

### :tea: Problem Statement:
The file* penguins.csv contains body measurements for over 100 Gentoo penguins observed in the Palmer Archipelago of Antarctica from 2007-2009. The images show what the measurements mean. Here we will work with bill length and flipper length.

### :basketball: Data:
- Using dim() to check the dimension and head() for a slice of the data
- Data dimension: 117 rows and   8 columns
<img width="997" alt="Screen Shot 2022-08-16 at 11 18 01 AM" src="https://user-images.githubusercontent.com/64395120/184929152-cd6ae74c-ef25-472f-a061-015114bb9660.png">

### :telescope: Modelling:
- R libraries: dplyr for data manipulation, magrittr for pipe operator
- Fit a SLR model where bill length is the predictor and flipper_length is the response <br>
:heavy_check_mark: See the results: <br>
<img width="400" alt="Screen Shot 2022-08-16 at 11 23 13 AM" src="https://user-images.githubusercontent.com/64395120/184930042-202572bd-a01f-49b7-b33c-2e077584d94c.png">

:heavy_check_mark: Visualization:

<img width="700" alt="Screen Shot 2022-08-16 at 11 24 57 AM" src="https://user-images.githubusercontent.com/64395120/184930425-4bf6217e-38dc-4a6b-b985-744ae83fc448.png">

As we can see from the display of regression output, the model can explain the 45.34% of fliiper length on bill length. The estimate sigma (standard deviation of the errors) is 4.75245

- Split the penguin data into two subsets, one for female penguins and one for males
penguins.male <- penguins.exam %>% filter(sex == "male") ### males penguins 
penguins.female <- penguins.exam %>% filter(sex == "female") ### female penguins 

- Make a plot with the data points and the fitted regression line for the two subsets <br>

:heavy_check_mark: Males penguins: <br>
<img width="600" alt="Screen Shot 2022-08-16 at 11 35 58 AM" src="https://user-images.githubusercontent.com/64395120/184932370-51d7d767-ed9d-4f73-9a20-ac7ad5327c34.png">

:heavy_check_mark: Females penguins:
<img width="600" alt="Screen Shot 2022-08-16 at 11 37 05 AM" src="https://user-images.githubusercontent.com/64395120/184932565-78494111-d639-4cab-b335-611d17aff5f6.png">

We use summary() function to display the output, we learned tgar the models for both males and females can explain the 24.69 %. The estimate sigma is 4.912 <br>


