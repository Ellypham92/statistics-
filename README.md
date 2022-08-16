## :bird: Gentoo Penguins

<img width="380" alt="Screen Shot 2022-08-16 at 11 11 44 AM" src="https://user-images.githubusercontent.com/64395120/184928087-200f4127-b6b5-40c4-a873-2c4c4a906854.png">

### :tea: Problem Statement:
The file* penguins.csv contains body measurements for over 100 Gentoo penguins observed in the Palmer Archipelago of Antarctica from 2007-2009. The images show what the measurements mean. Here we will work with bill length and flipper length.

### :basketball: Data:
 The file **coffee.txt** contains 53 days of test data collected by Starbucks in a city where some larger stores are already open.

### :telescope: Modelling:
- R libraries: dplyr for data manipulation, magrittr for pipe operator
- Fit the linear regression model in R using lm() function
coffee <- read.delim("coffee.txt")
coffee.mod <- lm(Customers~Baristas, data=coffee)
plot(Customers~Baristas, data=coffee, col = 'deeppink', pch = 19)
abline(coffee.mod)



predict.lm(coffee.mod, newdata = data.frame(Baristas = c(2)), interval = 'pred', level = 0.95)
predict.lm(coffee.mod, newdata = data.frame(Baristas = c(8)), interval = 'pred', level = 0.95)
- Compute 95% prediction intervals for $Y = Customers$ when $x=Baristas= 2$ and when $x=Baristas=8$
