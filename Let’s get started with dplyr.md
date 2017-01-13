## Getting my head round popular packages such as ggplot2, dplyr etc. 

###The questions I've used can found here http://r-exercises.com/2017/01/12/lets-get-started-with-dplyr/

**Exercise 1**

```
library(dplyr)
df<- data.frame(Theoph)
```
**Exercise 2**

```
names(df)
```
**Exercise 3 (a)**

Initially I tried this but I then on second thought, I realise it wasn't point of the question

```
select(df,Subject, Wt,Dose)
```
This is a shorter way of doing the same thing
```
select(df,1:3)
```
**Exercise 3 (b)**
```
select(df,Wt,Dose)
```
