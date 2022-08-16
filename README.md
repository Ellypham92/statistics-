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
:heavy_check_mark: See the results:
<img width="682" alt="Screen Shot 2022-08-16 at 11 23 13 AM" src="https://user-images.githubusercontent.com/64395120/184930042-202572bd-a01f-49b7-b33c-2e077584d94c.png">

:heavy_check_mark: Visualization:
<img width="700" alt="Screen Shot 2022-08-16 at 11 24 57 AM" src="https://user-images.githubusercontent.com/64395120/184930425-4bf6217e-38dc-4a6b-b985-744ae83fc448.png">


 As we can see from the display of regression output, the model can explain the 45.34% of fliiper length on bill length.
- Compute 98\% confidence intervals for the intercept and slope coefficients


