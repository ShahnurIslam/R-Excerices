## Getting my head round popular packages such as ggplot2, dplyr etc. 

###Since my main job involves manaipulating data I thought I'd start with dplyr. The questions I've used can be found here http://r-exercises.com/2017/01/12/lets-get-started-with-dplyr/

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

Initially I tried the below but I realised it wasn't point of the question

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
**Exercise 4**
I haven't used the filter command before so I quickly used R help(?filter) to give me a basic idea of the function. I've found that R documentation can be a good source of help if you're not sure how to use a command.

```
filter(df,Dose>5)
```
**Exercise 5**

```
filter(df,Dose>5 & Time > mean(Time))
```
**Exercise 6**
```
1)arrange(df,desc(Wt))
2)arrange(df,Wt)
3)arrange(df, Wt, desc(Time))
```
**Exercise 7**

There aren't any NA's in the data so unsure why they've asked us to use na.rm = True with the average.
```
mutate(df,trend = Time-mean(Time)
```
**Exercise 8**
Saw a few comments on how to do this. This was the solution they suggested

```
mutate(df,weight_cat = ifelse(Wt<66.8,"Welterweight",ifelse(Wt<69.85,"Light-middleweight",ifelse(Wt<72.57,"Middleweight","Super-middleweight"))))
```
You could also write a function to categorise weight and apply that. It was a challenge so thought why not
Here's the function
```
> categorise_weight<- function(x){
+ if(x<66.68){
+ print("Welterweight")
+ } else if (x<69.85) {
+ print("Light-middleweight")
+ } else if (x<72.57){
+ print("Middleweight")
+ } else
+ print("Super-middleweight")
+ }
```
Then using lapply we can store add the new column and store this back in df
```
df<-mutate(df,weight_cat=lapply(df$Wt,categorise_weight))
```

**Exercise 9**
Didin't understand this at first but realise it's meant to 
```
weight_group <- weight_groupgroup_by(df,weight_cat)
```

**Exercise 10**
```
summarize(weight_group, Avg_time = mean(Time), Total_Dose = sum(Dose))
```
