Week 1: R Software Introduction
================
written by Junvie Pailden

The R Software
--------------

R is a programming environment for data analysis, graphics and statistical computing. The R language is widely used among statisticians for developing statistical software and data analysis.

R processes commands entered by the user, who types the commands at the console, or submits the commands from a file called a script.

When the user use the console, each command or expression to be evaluated is typed at the command prompt, and immediately evaluated when the `Enter` key is pressed.

When the user submits the commands from a file, each line of code is evaluated by hitting `Cntrl + R` or `Cntrl + Enter` for PC or hitting `Cmd + R` or `Cmd + Enter` for Mac.

Helpful tips

-   Press the up-arrow key to recall commands and edit them.
-   Use the `Esc (Escape)` key to cancel a command.
-   Write comments after `#` sign.

What is RStudio?
----------------

RStudio (<http://www.rstudio.org>) is R's popular front-end or integrated development environment (IDE). We will use RStudio for all class related computation and analysis. RStudio provides syntax highlighting, code completion and smart indentation. Some of RStudios features includes

-   plot history, zooming, and flexible image and PDF export;
-   integrated R help and documentation;
-   generating word or pdf file output;
-   searchable command history.

Using R as a simple calculator
------------------------------

Start the RStudio system, the cursor is waiting for you to type in some R commands. For example, use R as a simple calculator:

``` r
7 + 4  # addition
# [1] 11

8 * 9 # multiplication
# [1] 72

17 / 3 # division
# [1] 5.666667

4 ^ 3 # power
# [1] 64

(1 + 0.03)^5 # association
# [1] 1.159274

exp(4) # exponential function
# [1] 54.59815

log(12) # natural log function
# [1] 2.484907

3.1415 * log(3)/(7 - atan(8))
# [1] 0.6214557
```

Assignment Operator
-------------------

Results of calculations can be stored in objects using the assignment operators:

-   an arrow (`<-`) formed by a smaller than character and a hyphen without a space;
-   the equal character (`=`).

Many R users have suggested using `<-`, not `=`, for assignment.

``` r
x <- sin(0)
y <- 3.1415 * cos(pi)
z <- x + y
x
# [1] 0
y
# [1] -3.1415
z
# [1] -3.1415
```

Storing Data in R
-----------------

*Example 1. (Temperature Data).* Average annual temperatures in New Haven, CT, were recorded in degrees Fahrenheit, as

| Year             | 1968 | 1969 | 1970 | 1971 |
|------------------|------|------|------|------|
| Mean temperature | 51.9 | 51.8 | 51.9 | 53   |

The combine function `c()` creates a vector from its arguments, and the result can be stored in user-defined vectors. We use the combine function to enter our data and store it in an object named `temps`.

``` r
temps <- c(51.9, 51.8, 51.9, 53)
temps
# [1] 51.9 51.8 51.9 53.0
```

Suppose that we want to convert the Fahrenheit temperatures (F) to Celsius temperatures (C). The formula for the conversion is *C* = 5/9(*F* − 32).

``` r
(5/9) * (temps - 32)
# [1] 11.05556 11.00000 11.05556 11.66667
```

Let's create another vector containing the year the temperatures were taken.

``` r
years <- c(1968, 1969, 1970, 1971)
years
# [1] 1968 1969 1970 1971
```

The preferred form for variable names is all lower case letters and words separated with dots `(variable.name)`.

We can use the function `cbind` to combine the two vectors (`years` and `temps`) into a matrix.

``` r
temp.data <- cbind(years, temps)
temp.data
#      years temps
# [1,]  1968  51.9
# [2,]  1969  51.8
# [3,]  1970  51.9
# [4,]  1971  53.0
```

Objects in R
------------

Vectors and matrices are two of several types of objects in R. Other types of objects are lists, factors, and data frames. More on this later.

A vector can be defined according to the data type it contains. There are

-   numeric vectors;
-   logical (or Boolean) vectors;
-   character (or string) vectors.

``` r
num <- c(3, 3.1, 3.14, pi, -pi, cos(pi))
num
# [1]  3.000000  3.100000  3.140000  3.141593 -3.141593 -1.000000
char <- c("I", "Love", "Pie")
char
# [1] "I"    "Love" "Pie"
char[2] # second entry of vector char
# [1] "Love"
char[-3] # displays the sub-vector excluding the 3 entry
# [1] "I"    "Love"
```

If a vector mixes different data types, R will store it as a character vector.

``` r
mixed <- c("I", "Love", 3)
mixed
# [1] "I"    "Love" "3"
```

Logical vectors are often defined as the result of control actions on numerical or character vectors.

``` r
num
# [1]  3.000000  3.100000  3.140000  3.141593 -3.141593 -1.000000
logic1 <- num > 2
logic1
# [1]  TRUE  TRUE  TRUE  TRUE FALSE FALSE
```

Vectors can be created using sequences using the operator `:` or using `seq()` function.

``` r
v.for <- 1:15 # generate integer sequence from 1 to 15
v.for
#  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15
v.back <- 15:1  # generate integer sequence from 15 to 1
v.back
#  [1] 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
seq.by <- seq(from = 1, to = 15, by = 2) # generate a sequence from 1 to 15 incremented by 2
seq.by
# [1]  1  3  5  7  9 11 13 15
seq.len <- seq(from = 1, to = 15, length.out = 8) # generate a sequence from 1 to 15 of length 8
seq.len
# [1]  1  3  5  7  9 11 13 15
seq.len[1:5] # displays the first 5 entries
# [1] 1 3 5 7 9
```

Displaying Objects in R
-----------------------

You can display an object in two ways after storing it. The first is by typing the name of the object in a separate line and running the same line. Another is by enclosing the entire command/code in parentheses.

``` r
seq.rev <- seq(from = 12, to = 0, by = -2) 
seq.rev 
# [1] 12 10  8  6  4  2  0
(seq.rev <- seq(from = 12, to = 0, by = -2)) 
# [1] 12 10  8  6  4  2  0
```

The R Help System
-----------------

The help search functions are also available using the functions `help` and `help.search`, and the corresponding shortcuts `?` and `??`.

-   `help("keyword")` or `?keyword` displays help for `“keyword”`.
-   `help.search("keyword")` or `??keyword` searches for all objects containing `“keyword”`.

For example, when looking for information on computing the average or mean of a vector

``` r
help("mean") # or
# starting httpd help server ... done
?mean        # scroll to the bottom to see examples
x <- c(0:10, 50)
x
#  [1]  0  1  2  3  4  5  6  7  8  9 10 50
mean(x)
# [1] 8.75
```

------------------------------------------------------------------------

Some Useful R Documentations
----------------------------

1.  [R Data Types](https://www.statmethods.net/input/datatypes.html)
2.  [Google's R Style Guide](https://google.github.io/styleguide/Rguide.xml)
3.  [R Markdown - Dynamic Documents for R](https://support.rstudio.com/hc/en-us/articles/205368677-R-Markdown-Dynamic-Documents-for-R)
