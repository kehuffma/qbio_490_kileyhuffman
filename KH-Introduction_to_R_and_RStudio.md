Introduction to R and RStudio COMPLETED
================
Nicole Black, Kayla Xu
07/13/22

### Secure copy (scp) this file to your qbio_490_name repository. DO NOT EDIT IN sp24_course_materials!

Welcome to RStudio! This document will take you through the basics of R
before we jump right into our analyses.

###### (1) R Notebooks vs R Scripts

This file is an R Notebook. R Notebooks allow for plain-text and code
blocks to be interspersed among each other. Here’s an example of a code
block:

``` r
print("This is a code block!")
```

    ## [1] "This is a code block!"

To run a code block in an R Notebook, simply hit the green arrow button
in the top right of the block. Your code will run, and any outputs will
be shown below the code block as well as in your console (down below).
You can collapse any unnecessary outputs by clicking the double up arrow
button in the top right of the output block.

To run a single line of R code, you can put your cursor on/highlight the
line and use the shortcut Cmd+Enter or Ctrl+Enter.

R Script is just a normal coding file. There are no code blocks or
plain-text sections, just a file with code and comments as needed. This
is what you’ll be coding in once we get a little further into the
semester.

###### (2) Setting Up Your Environment

When you first open a document, you want to make sure that your working
directory is properly set. This allows you to both access files on your
local machine, and to write files onto that machine.

To figure out where you are, use getwd(). This is equivalent to pwd in
Unix.

``` r
getwd()
```

    ## [1] "/home1/kehuffma/490_cluster"

To set your directory, type setwd(“/PATH/TO/DIRECTORY”). This is similar
to cd in Unix, except you need to use quotes around the directory.

``` r
## don't run this
# setwd() # (ex: "/Users/nicoleblack/Desktop/qbio_490_nicole/week3_R")

## for R Notebooks, don't actually do this! Keep reading...
```

Specifically for R Notebooks, setting a working directory is a bit
funky. Make sure you understand setwd() since this is the command you
will use when working in R scripts, but for all notebooks from now on,
just add your path into the R Setup chunk as seen below. Don’t worry
about remembering the syntax of this chunk, we’ll add it for you.

``` r
    # replace path with the path to your qbio_490_name directory
   # knitr::opts_knit$set(root.dir = normalizePath("/Users/kileyhuffman/Desktop/qbio_490_kileyhuffman"))
```

Now that your environment is set up, let’s get into coding!

###### (3) Variables

A variable is an container that stores data within your program. In R,
you do not have to specify your data type. To declare a variable, simply
state the name, use ‘\<-’, then specify the data you want to store.

``` r
var_string <- "hello world!"
var_num <- 23
var_vector <- c(3, 2, 1)

## Create a new variable my_var to store anything you choose:

my_var <- "my variable"

print(my_var)
```

    ## [1] "my variable"

Even though we don’t need to specify data types in R, they still exist
in the language.

For each empty variable, provide a value appropriate for the data type
and variable name.

``` r
# Undefined Values
## create an undefined value in two different ways
null <- NULL
na <- NA

# Boolean Value is either true or false
## booleans can be defined in a variety of ways in R!
true_var <- TRUE
false_var <- FALSE

## numeric is a catch all for any number value in R
negative <- -4
decimal <- 0.2

## a string is any text value
## strings can be enclosed in single or double quote
string_var <- "String"
char_var <- "@"

## vectors contain data elements of the same data type
## they are declared by enclosing elements in c()
vector <- c(2, 3) 

## a factor is a categorical variable
## a factor has data elements (defined like a vector) and categories (known also as levels), that are inferred from the data 
factor <- factor(vector) 
factor
```

    ## [1] 2 3
    ## Levels: 2 3

A note on variable naming:

``` r
numeric_vector = c(8,9)
## great names:
sum_of_ages <- sum(numeric_vector) # snake case
sumOfAges <- sum(numeric_vector) # camel case

## fine names:
AgeSum <- sum(numeric_vector)
sum.of.ages <- sum(numeric_vector)

## bad names:
sum <- sum(numeric_vector)
s <- sum(numeric_vector)
sumofages <- sum(numeric_vector)
SUMOFAGES <- sum(numeric_vector)
```

Now that you’re an expert on variables in R, let’s try it out!

Create four variables named ‘name’, ‘age’, ‘birthday’ (in a MM/DD/YYYY
format), and ‘three_fav_colors’. Print by writing out the name of each
variable. What data types are these (use typeof() to validate)?

``` r
## add code here!

# create variables
name <- "Kiley Huffman" # character variable
age <- 21 # double variable
birthday <- "09/26/2002" # character variable
three_fav_colors <- "red, blue, purple" # character variable

# print variables
print(name)
```

    ## [1] "Kiley Huffman"

``` r
print(age)
```

    ## [1] 21

``` r
print(birthday)
```

    ## [1] "09/26/2002"

``` r
print(three_fav_colors)
```

    ## [1] "red, blue, purple"

``` r
# check data type
typeof(name)
```

    ## [1] "character"

``` r
typeof(age)
```

    ## [1] "double"

``` r
typeof(birthday)
```

    ## [1] "character"

``` r
typeof(three_fav_colors)
```

    ## [1] "character"

###### (4) Functions

Functions perform repeatable actions on the parameters passed into them.
There are three important components to a function:

1.  Name  
    All functions have a name that is used to call them

2.  Arguments (parameters)  
    An argument is passed into a function. A function can have any
    number of arguments, including none, depending on the function
    definition

3.  Return value  
    The return value is the output of the function.

To call a function, use the syntax: return_value \<- function_name(arg1,
arg2, arg3) Note that it can be helpful to save the return value to a
variable, as shown above, but it isn’t always necessary.

``` r
sum(3, 4, 5) ## calling the function without saving the output automatically prints to the console
```

    ## [1] 12

``` r
max_value <- max(1, 10, 100) ## storing to a variable does not automatically print
max_value
```

    ## [1] 100

Call the following functions on the list of numbers below: sum(), min(),
mean(), mode(), summary()

``` r
list_of_numbers <- c(1, 1, 2, 3, 5, 8, 13, 21)

## call functions here
sum(list_of_numbers)
```

    ## [1] 54

``` r
min(list_of_numbers)
```

    ## [1] 1

``` r
mean(list_of_numbers)
```

    ## [1] 6.75

``` r
mode(list_of_numbers)
```

    ## [1] "numeric"

``` r
summary(list_of_numbers)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    1.00    1.75    4.00    6.75    9.25   21.00

###### (5) Logic and Control Flow

Control flow allows you to run certain chunks of code based on a
condition. We can do this by implementing logical statements. Logical
statements are statements of equality that evaluate as booleans to
either TRUE or FALSE. For example, if our logical statement is TRUE, we
can then control flow to run chunk ‘A’ of code, and if our logical
statement is FALSE, we could use that same control flow to run chunk
‘B’.

Below are common operators used in logical statements in R. Run each
statement to see what it evaluates to.

``` r
"QBIO" == "QBIO" ## is equal to
```

    ## [1] TRUE

``` r
"USC" != "UCLA" ## is not equal to
```

    ## [1] TRUE

``` r
10 > 9 ## greater than
```

    ## [1] TRUE

``` r
1 < 2 ## less than
```

    ## [1] TRUE

``` r
8 >= 3 ## greater than or equal to
```

    ## [1] TRUE

``` r
4 <= 7 ## less than or equal to
```

    ## [1] TRUE

``` r
100 %in% c(10, 100, 1000, 10000) ## is present in a vector/list
```

    ## [1] TRUE

You can also link multiple logical statements using AND (&), OR (\|), or
NOT (!)

Predict what each statement will evaluate to:

``` r
"cat" == "cat" & "dog" == "dog" # prediction: TRUE
```

    ## [1] TRUE

``` r
"cat" == "cat" & "fish" == "hamster" # prediction: FALSE
```

    ## [1] FALSE

``` r
1 < 2 | 3 < 1 # prediction: TRUE
```

    ## [1] TRUE

``` r
1 < 2 | 3 < 5 # prediction: TRUE
```

    ## [1] TRUE

``` r
"blue" %in% c("yellow", "red", "blue") &! "happy" %in% c("sad", "angry")
```

    ## [1] TRUE

``` r
# prediction: TRUE
```

“If” statements (along with “else if” and “else” statements) are the
most simple control flows to write, and they are also what we will use
the majority of the time.

The syntax for “if”, “else if”, and “else” statements is as follows.
Fill in possible conditions and actions so that the “if” statement is
skipped, and the “else if” runs, printing out “Success!”. Run the block
to test.

``` r
if (1 > 3) {
  # action
  print("Fail")
} else if (2 > 1) {
  # action
  print("Success!")
} else {
  # action
  print("Fail")
}
```

    ## [1] "Success!"

An “if” block can be used alone or in conjunction with any number of
“else if” blocks that can end in up to one “else” block. Note that you
cannot have an “else if” or an “else” block without an “if” statement.
These blocks are executed in order until one expression is true. At a
true expression, the contents of the block runs, and the control flow is
exited (ie none of the below blocks are tested).

Sometimes using “if… else if… else” doesn’t work. You might get the
error code: “the condition has length \> 1”. This is because an if
statement only checks ONE element to evaluate the condition. To performs
an element-wise evaluation on a vector, we must use ifelse(), a
vectorized function. The syntax is follows:

``` r
# ifelse(expression, x, y) # where x happens if the expression is true, and y happens if it is false

# output <- ifelse(expression1, x, ifelse(expression2, y, ifelse(expression3, z, a)))
# the resulting vector from an ifelse statement can be saved in a variable
```

Predict the outcome of the following control flow, then run the code
block to confirm your prediction.

``` r
new_list <- c("starbucks", "elephant", 232, "magenta", -10)

if (7.5 %in% new_list) {
  print("A")
  if (!7.5 %in% new_list) {
    print ("B")
  }
} else if  (!(232 %in% new_list)) {
  print("C")
} else if ("starbucks" %in% new_list &! 9 > 10) {
  print("D")
  if (100 < 1 | "elephant" %in% new_list) {
    print("E")
  }
  else if ("magenta" %in% new_list) {
    print("F")
  }
} else {
  print("G")
}
```

    ## [1] "D"
    ## [1] "E"

###### (6) Loops

If you want to do one action multiple times or run the same operation on
a large number of items, a loop can be utilized to avoid repetitive
code. There are two main types of loops: “while loops” and “for loops”

While loops are like if statements that repeat multiple times until the
condition is no longer true. The syntax is as follows:

``` r
# while (# condition) {
  # do something
  # update condition
```

Here’s an example:

``` r
i = 1
while (i < 10) {
  print(i)
  i = i + 2
}
```

    ## [1] 1
    ## [1] 3
    ## [1] 5
    ## [1] 7
    ## [1] 9

Starting with x = 0, write a while loop that returns the mean of 1, 10,
and x until that average is greater than 10. Each time the loop runs,
increment x by 1.

``` r
x = 0
my_list <- c(1, 10, x)
mean <- mean(my_list)
mean_value <- 0 

while (mean_value < 10) {
  my_list <- c(1, 10, x)
  mean_value <- mean(my_list)
  x <- x + 1
  print(mean_value)
}
```

    ## [1] 3.666667
    ## [1] 4
    ## [1] 4.333333
    ## [1] 4.666667
    ## [1] 5
    ## [1] 5.333333
    ## [1] 5.666667
    ## [1] 6
    ## [1] 6.333333
    ## [1] 6.666667
    ## [1] 7
    ## [1] 7.333333
    ## [1] 7.666667
    ## [1] 8
    ## [1] 8.333333
    ## [1] 8.666667
    ## [1] 9
    ## [1] 9.333333
    ## [1] 9.666667
    ## [1] 10

The other type of commonly used loop is a for loop. In R and Python, you
can think of a for loop as doing something for each element in some
list. The syntax is as follows:

``` r
# for (i in list) {
  # do something
```

Here’s an example:

``` r
list <- c(2, 4, 6, 8)

for (element in list) { # note that I can call "element" whatever I want, it like a temporary variable that stores the list's item
  print (element * 2)
}
```

    ## [1] 4
    ## [1] 8
    ## [1] 12
    ## [1] 16

Write a for loop that prints the cube of each item in the list “list”:

``` r
list <- c(1, 5, 20, 0)

# write loop here
for (i in list)
  print(i^3)
```

    ## [1] 1
    ## [1] 125
    ## [1] 8000
    ## [1] 0

You can also use a for loop to run code a specified number of times by
using a sequence (ex: 1:5) instead of a list. The syntax is as follows:

``` r
for (i in 1:10) {
  # do something
}
```

Use this syntax to print all numbers between -7 and 7.

``` r
# write loop here
for (i in -7:7) {
  print(i)
}
```

    ## [1] -7
    ## [1] -6
    ## [1] -5
    ## [1] -4
    ## [1] -3
    ## [1] -2
    ## [1] -1
    ## [1] 0
    ## [1] 1
    ## [1] 2
    ## [1] 3
    ## [1] 4
    ## [1] 5
    ## [1] 6
    ## [1] 7

VERY IMPORTANT NOTE: In R, we generally want to avoid using loops since
they are fairly slow and because R is already optimized for repeating
actions on any lists/vectors. However, there are certain instances where
loops must be used, so if you absolutely cannot think of any other
solution, a loop is always a good backup.

You can use certain built-in functions to avoid looping. For example,
say we wanted to sum up the elements in a list. We could write a for
loop, or we could use the sum() function.

``` r
list <- c(1, 10, 100) 

# using a loop
sum_loop <- 0
for (i in list) {
  sum_loop = sum_loop + i
}

# using a function
sum_func <- sum(list)

# they are the same!
sum_loop
```

    ## [1] 111

``` r
sum_func
```

    ## [1] 111

``` r
sum_loop == sum_func
```

    ## [1] TRUE

Some good functions to use when avoiding loops are sum(), rowsum(),
colsum(), and ifelse().

###### (7) Vectors

Vectors are lists where all of the objects have the same data type.
Recall from the “variables” section that vectors are defined using
“c()”.

You can access an item in a vector using bracket notation as follows;

``` r
vector <- c("CSCI102", "CSCI103", "CSCI104")

vector[3] ## remember that R is a one indexed language, so we start counting from 1 (not 0)
```

    ## [1] "CSCI104"

The reason why vectors are so import for us is that R is a vectorized
language, meaning it is specifically set up to work well with vectorized
data. Many of the built in functions work just the same on vectorized
objects as they do on individual objects. Hence, we should always try to
utilize these functions on vectors rather than doing the same work with
a loop working on an individual object.

Let’s explore this further (you don’t need to fully understand
everything here quite yet, just look at the comments for help):

``` r
vector <- 1:10^6 # here's a huge vector (all numbers between 1 and 10^6)

loop_sum <- function(vector) { # here, I created a user-defined function that sums up the elements in "vector" using a loop
  x=0
  for (i in vector) {
    x = x + i
  }
  return(x)
}

function_sum <- sum(vector) # here, we sum up the elements in "vector" using a built-in vectorized function

loop_sum(vector) == function_sum # tests that these are equal
```

    ## [1] TRUE

It is clear that the function notation is much simpler and easier to
understand than the loop notation, but we can see another clear reason
to use vectorization over loops when we explore run time:

``` r
install.packages("rbenchmark")
```

    ## Installing package into '/home1/kehuffma/R/x86_64-pc-linux-gnu-library/4.4'
    ## (as 'lib' is unspecified)

``` r
library(rbenchmark) # this library allows us to use the benchmark function to explore run time

print(benchmark(
  vectorized = function_sum, #this compares the vectorized sum (function_sum)...
  loop = loop_sum(vector), # to the loop sum (loop_sum)
  replications = 100
))
```

    ##         test replications elapsed relative user.self sys.self user.child
    ## 2       loop          100   1.881       NA     1.875    0.002          0
    ## 1 vectorized          100   0.000       NA     0.001    0.000          0
    ##   sys.child
    ## 2         0
    ## 1         0

We can see that the loop implementation takes 1.741x as long as the
vectorized implementation. When we are running (numerous) even more
intensive implementations, this can significantly impact our run time.

###### (8) Installing Packages

A package (or library) contains a group of functions that are not
implemented in the base installation of R. Especially for bioinformatics
and computational biology uses, there are lots of great packages with
helpful functions for analysis.

To install and load a package, use the following syntax:

``` r
# if (!require(package)) # you only need to install a package once, this checks to see if it has already been installed
# install.packages("package")


# library(package) # you need to load in a package in every file that uses it (it's good practice to run all package related lines at the top of your file)
```

In your TCGA Data Download assignment, all of the required packages for
our course have already been installed. From this point on, to use a
package, you only need to run library(package).

###### (9) Getting Help

Forget how to use a function? No worries! Here are three ways to get
info when you need it:

1.  “?function_name” or “help(function_name)”: brings up help tab for
    the function (see bottom right panel)
2.  args(function_name): gives arguments for the function
3.  Google!

Try this out on the is.na() function (you’ll need this in your homework)

``` r
# write code here
help(is.na)
```

###### (12) Further Practice

For even more practice, use swirl(), a packages that holds multiple
courses on R basics, statistics, and data analysis.

To use swirl, open up an R Script file (use the + icon in the top left
corner of RStudio). Then run the following commands.

``` r
if (!require(swirl)){
install.packages("swirl")
}
```

    ## Loading required package: swirl

    ## 
    ## | Hi! I see that you have some variables saved in your workspace. To keep
    ## | things running smoothly, I recommend you clean up before starting swirl.
    ## 
    ## | Type ls() to see a list of the variables in your workspace. Then, type
    ## | rm(list=ls()) to clear your workspace.
    ## 
    ## | Type swirl() when you are ready to begin.

``` r
library(swirl)
install_course_github("swirldev", "R_Programming_E")
```

    ## Downloading: 3.2 kB     Downloading: 3.2 kB     Downloading: 8.7 kB     Downloading: 8.7 kB     Downloading: 13 kB     Downloading: 13 kB     Downloading: 21 kB     Downloading: 21 kB     Downloading: 35 kB     Downloading: 35 kB     Downloading: 37 kB     Downloading: 37 kB     Downloading: 43 kB     Downloading: 43 kB     Downloading: 43 kB     Downloading: 43 kB     Downloading: 43 kB     Downloading: 43 kB     Downloading: 59 kB     Downloading: 59 kB     Downloading: 65 kB     Downloading: 65 kB     Downloading: 88 kB     Downloading: 88 kB     Downloading: 93 kB     Downloading: 93 kB     Downloading: 100 kB     Downloading: 100 kB     Downloading: 140 kB     Downloading: 140 kB     Downloading: 170 kB     Downloading: 170 kB     Downloading: 190 kB     Downloading: 190 kB     Downloading: 220 kB     Downloading: 220 kB     Downloading: 230 kB     Downloading: 230 kB     Downloading: 250 kB     Downloading: 250 kB     Downloading: 330 kB     Downloading: 330 kB     Downloading: 370 kB     Downloading: 370 kB     Downloading: 400 kB     Downloading: 400 kB     Downloading: 430 kB     Downloading: 430 kB     Downloading: 430 kB     Downloading: 430 kB

    ## Warning in file.rename(file.path(swirl_courses_dir(), old_name),
    ## file.path(swirl_courses_dir(), : cannot rename file
    ## '/home1/kehuffma/R/x86_64-pc-linux-gnu-library/4.4/swirl/Courses/swirldev-R_Programming_E-e0e0a5e'
    ## to
    ## '/home1/kehuffma/R/x86_64-pc-linux-gnu-library/4.4/swirl/Courses/R_Programming_E',
    ## reason 'Directory not empty'

``` r
swirl()
```

To get extra credit, email completed assignments to “<kaylaxu@usc.edu>”
when prompted. You will receive 0.25 points for completion of any swirl
exercise, with a max of 5 points to be added to your homework grade.
