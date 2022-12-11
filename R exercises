 A.M.Madhu Attanayake

 #https://methodenlehre.github.io/SGSCLM-R-course/index.html Exercises answers
 
 
#Rounding Numbers
x <- rnorm(10, mean = 1, sd = 0.5)
x
round(x, digits=0)#roundoff to 0 decimal places
round(x, digits=3)#roundoff to 3 decimal places

this_number <- 3.45263
round(this_number, digits=0)

#Compute Mean
library(dplyr)
df <- data_frame(sex = sample(c("male", "female"),
                              size = 24,
                              replace = TRUE),
                 age = runif(24, min = 19, max = 45))
df
print (mean(df$age))#calculate the mean age
summary(df)#summary statistics using summary() finction

#Character Vectors
#Generate a new variable from the variables ID, initials and age using the paste() function. The new variable should look like this:

#"1-RS-44" "2-MM-78" "3-PD-22" "4-PG-34" "5-DK-67" "1-RS-59"

ID <- c(1, 2, 3, 4, 5)
intials <- c("RS", "MM", "PD", "PG", "DK")
age <- c(44, 78, 22, 34, 67, 59)
paste(ID[1:5], intials[1:5],age[1:5], sep = "-")

#Data Frames

#Change the order of the factor levels in the following data set. We want placebo to be the new reference category.

dff <- data_frame(no_alcohol = c(64, 58, 64),
                  placebo = c(74, 79, 72),
                  anti_placebo = c(71, 69, 67),
                  alcohol = c(69, 73, 74))

dff <- dff %>%
  gather(key = condition, value = aggression) %>%
  mutate(condition = factor(condition))
dff
levels(dff$condition)
dff$condition <- factor(dff$condition, levels = c("placebo", "anti_placebo","no_alcohol","alcohol"))
levels(dff$condition)                                                            
dff$condition <- relevel(dff$condition, ref = "placebo")
levels(dff$condition)

#Advanced Exercises

#Select all even numbers from a numeric vector:
x <- seq(1, 20, by = 1)
x
x %% 2
index <- x %% 2 == 0
index
even_numbers <- x[index]
even_numbers#even numbers

#Select all odd numbers from a numeric vector:
x %% 2
index <- x %% 2 == 1
index
odd_numbers <- x[index]
odd_numbers#odd numbers





#Exercise 3.5

dset <- read_csv("data.csv")
cols(
  Vpn = col_character(),
  messzeitpunkt = col_character(),
  rating = col_double()
)
dset$Vpn <- as.factor(dset$Vpn)
dset$messzeitpunkt <- as.factor(dset$messzeitpunkt)
dset



#Exercises 4.5

#Convert grouping variables to factors.using a data set
library(readr)
library(tidyr)
library(dplyr)
results <- read_csv("gpa.csv")
cols(
  Student_Id = col_integer(),
  Semester1_gpa = col_double(),
  Semester2_gpa = col_double(),
  Semester3_gpa = col_double()
)
results

#CONVERT TO LONG
result_long <- results %>%
  gather(key = condition, value = gpa,
         Semester1_gpa, Semester2_gpa, Semester3_gpa, -Student_Id) %>%
  mutate(Student_Id = factor(Student_Id),
         condition = factor(condition))
result_long

#sUMMARY
summary_result <- result_long %>%
  group_by(Student_Id, condition) %>%
  summarise(mean_gpa = mean(gpa))

summary_result

result_long <- result_long %>%
  mutate(log_result = log(result))

result_long

#Plotting

library(ggplot2)

ggplot(data = result_long)
ggplot(data = result_long, aes(x = gpa, y =Student_Id  , col = condition))
ggplot(data = result_long, 
       aes(x = gpa, y = Student_Id, col = condition)) + geom_point()

#Exercise 5.9

#plot2

ggplot(data = result_long, 
       aes(x = gpa, y = Student_Id, col = factor(Student_Id), 
           shape = factor(condition))) + geom_point()

#plo3

p <- ggplot(data = result_long, 
            aes(x = gpa, y = Student_Id, 
                shape = factor(condition))) + geom_point()

p + facet_grid(condition ~ .)


