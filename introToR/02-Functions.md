
# Functions & Classes

<img src="images/toolbox.jpeg" width="50%" /><img src="images/ratchet.jpeg" width="50%" />

<img src="images/socket.jpeg" width="50%" style="display: block; margin: auto;" />

In R, a package is a collection of functions. Imagine a package as a
toolbox and functions as the tools within the toolbox. If we want to
**load** the **wrenches** toolbox, we can load it like so -
`library(wrenches)`. Then, we can use different wrenches from that
toolbox like - `rachet_wrench()`, `small_wrench()`, `big_wrench()`.
These would be called functions. Functions are pre-written chunks of
code that perform an action in R. When we use something like a
`rachet_wrench()`, we’ll need to select a `socket` to put on. In this
example, the `socket` we put on the `rachet_wrench` is called an
argument. Arguments are interchangeable parameters that are needed to
run the function.

## Packages and Functions

In R, a `base` package is automatically loaded in for you. Most of the
time, we will need to install packages as RStudio only comes with a few
pre-installed packages. When we do need to install packages, we only
need to install it one time for it to be downloaded to our machine. All
packages in R are FREE. Now, let’s check back in on our pre-installed
packages. One of these pre-installed packages is called `base`. Within
the `base` package, we can find common functions such as `mean()`,
`min()`, `max()`,`print()`, `seq()`, etc. Even though it’s redundant,
let’s load the `base` package. Next, let’s write create a variable named
`my_val`, and print out the value using the `print()` function.

``` r
library(base)

my_val = 77
print(my_val)
```

    ## [1] 77

The `base` package was opened to use the `print` function which had an
argument of `my_val`. **After you load in an argument in an R session,
you do not need to reload it again**.

Now let’s look at an example where we create a sequence of numbers using
the `seq()` function.

``` r
library(base)

my_seq = seq(from = 10, to = 20, by = 1)
print(my_seq)
```

    ##  [1] 10 11 12 13 14 15 16 17 18 19 20

The `base` package was opened to use the `seq` function which had 3
arguments; `from`, `to`, and `by`.

## Arguments

Arguments must be declared using the `=` operator and are **always
separated by a comma**. In the last example, we used the `seq()`
function which had arguments of `from`, `to`, and `by`. How do we know
the argument names?

``` r
help(seq)
```

The `help()` function is automatically loaded for you and has detailed
information and examples of functions you may want to use. Notice that
we have arguments `from`, `to`, `by`, `length.out`, and `along.with`.
These arguments are **pre-definded**, meaning if you don’t declare the
values for the arguments, the function will automatically have arguments
declared for you. Lets see what happens if we don’t declare any
arguments for this function…

``` r
seq()
```

    ## [1] 1

Now try the same with the `print()` function

``` r
print()
```

`Error in print.default() : argument "x" is missing, with no default`.
There is no pre-defined value of x for `print()` to use. **But, wait a
second, when we coded `print(my_seq)`, we didn’t declare the `x`
argument?**. That’s right, you don’t *have to* declare the arguments by
name *if* you follow the *prescribed order* of the arguments in the
function. For example, the prescribed order of the `seq()` function is
`from`, `to`, and `by`. Let’s remove our argument names and see what
happens…

``` r
my_seq = seq(10,20,1)
print(my_seq)
```

    ##  [1] 10 11 12 13 14 15 16 17 18 19 20

The result is the same because we kept the same order. This notation is
sometimes called shorthand argument declaration. Pay attention to the
commas as they are absolutely necessary for separating the arguments.
Now, let’s see what happens if we have the same `from`, `to` and `by`
values but formally declare them out of order.

``` r
my_seq = seq(by = 1, from = 10, to = 20)
print(my_seq)
```

    ##  [1] 10 11 12 13 14 15 16 17 18 19 20

Once again, the result is the same. Although we can get away with
shorthand argument declaration, it’s always a good idea to formally
declare them for future users of the code (including yourself\!).

## R Objects

R has five basic classes of objects:

  - character

  - numeric (real numbers)

  - integer

  - logical (True/False)

  - complex

Use the `class()` function (from the base package, so we don’t need to
load anything) to figure out what class an object/variable is. Let’s
take a look at the example above.

``` r
val <- 1
class(val)
```

    ## [1] "numeric"

``` r
a = 7.779
class(a)
```

    ## [1] "numeric"

``` r
my_text = "hello"
class(my_text)
```

    ## [1] "character"

R recognizes each of these objects as different classes.

### Characters

Characters are text that are declared within quotations (or
apostrophes). They can be single phrases OR can be a collection of
words. When we have multiple words within quotations we refer to this as
a **character string**.

``` r
my_text = 'hello'
snacks = "Chips and Pretzels are my favorite snacks"
class(snacks)
```

    ## [1] "character"

``` r
my_name = 'Winston Churchill'
class(snacks)
```

    ## [1] "character"

### Numeric

Often times our data contains numbers that carry digits after a decimal
place. In R, these are referred to as **numeric values**.

``` r
a = 7.71
b = 123451.890803843
```

If we have a larger dataset, we may have more than 1 value per object.
Objects can also represent a *vector* of numeric values. Vectors are a
collection of values of the same class. In other words, it can be a
collection of numeric values, a collection of character strings, etc. We
can create vectors using the concatenate (aka combine) function. Let’s
use the combine function `c()` to create a vector of numeric values.

``` r
num_vect = c(7.71, 8.65, 9.34, 10.89, 19.55)
print(num_vect)
```

    ## [1]  7.71  8.65  9.34 10.89 19.55

``` r
class(num_vect)
```

    ## [1] "numeric"

Notice that `num_vect` represents this collection, yet the class of the
collection is numeric. As stated above, vectors must be a collection of
the same class.

### Integers

If we specify a number value in R, it is automatically classified as a
numeric even if that value looks like an integer to us. In order to
create an integer, we can use the `as.integer()` function.

``` r
i = as.integer(9)
class(i)
```

    ## [1] "integer"

We can use the `as.integer()` function to **convert** numeric values to
integer values.

``` r
x = 3.14
i = as.integer(x)
print(i)
```

    ## [1] 3

``` r
class(i)
```

    ## [1] "integer"

There are also similar functions for the other classes such as
`as.character()` and `as.numeric()`.

### Logicals

A logical is a special value in R that details a comparison. Some
logical values you may use include `TRUE`, `FALSE`, `&` (and), `|` (or),
and `!` (negate).

``` r
b = TRUE
y = c(TRUE, FALSE)
class(y)
```

    ## [1] "logical"

The latter logical values - `&` (and), `|` (or), and `!` (negate) - are
usually found in for loops which we’ll cover later on. Here’s a brief
example of how they work.

``` r
a = TRUE
b = FALSE

a & b
```

    ## [1] FALSE

``` r
a | b 
```

    ## [1] TRUE

``` r
!a
```

    ## [1] FALSE

### Complex values

We won’t be using many complex values in R, but R does support them.
Complex values use the letter `i` **immediately following a number**.

``` r
x <- c(1+2i, 3+8i) # complex
class(x)
```

    ## [1] "complex"

## Lists

Lists are a special type of vector that can contain elements of
different classes. Lists are a very important data type in R and you
should get to know them well. Lists, in combination with the various
“apply” functions discussed later, make for a powerful combination.

Lists can be explicitly created using the `list()` function, which takes
an arbitrary number of arguments.

``` r
x <- list(1, "a", TRUE, 7.65334) 
x
```

    ## [[1]]
    ## [1] 1
    ## 
    ## [[2]]
    ## [1] "a"
    ## 
    ## [[3]]
    ## [1] TRUE
    ## 
    ## [[4]]
    ## [1] 7.65334

## Factors

Factors are used to represent categorical data and can be unordered or
ordered. One can think of a factor as an integer vector where each
integer has a *label*.

Using factors with labels is *better* than using integers because
factors are self-describing. Having a variable that has values “Male”
and “Female” is better than a variable that has values 1 and 2.

Factor objects can be created with the `factor()` function.

``` r
x <- factor(c("yes", "yes", "no", "yes", "no")) 
x
```

    ## [1] yes yes no  yes no 
    ## Levels: no yes

``` r
table(x) 
```

    ## x
    ##  no yes 
    ##   2   3

``` r
# See the underlying representation of factor
unclass(x)  
```

    ## [1] 2 2 1 2 1
    ## attr(,"levels")
    ## [1] "no"  "yes"

Often factors will be automatically created for you when you read a
dataset in using a function like `read.table()`. Those functions often
default to creating factors when they encounter data that look like
characters or strings.

The order of the levels of a factor can be set using the `levels`
argument to `factor()`.

``` r
x <- factor(c("yes", "yes", "no", "yes", "no"))
x  ## Levels are put in alphabetical order
```

    ## [1] yes yes no  yes no 
    ## Levels: no yes

``` r
x <- factor(c("yes", "yes", "no", "yes", "no"),
            levels = c("yes", "no"))
x
```

    ## [1] yes yes no  yes no 
    ## Levels: yes no

## Matrices

A matrix is a collection of data elements arranged in a two-dimensional
rectangular layout. As you learn more about R, you’ll find that Matrices
are very popular. A matrix is one way to store a table of data, such as
an excel spreadsheet. For example, let’s create a matrix of fruits
consumed by a family for each day of the week. We have apples and
oranges as our fruits and 7 days in the week. A matrix might look like
this. matrix of fruits consumed by day might look like this.

``` r
apples = c(2, 4, 3, 1, 5, 7, 3) # apples consumed each day of the week
oranges = c(4, 3, 5, 1, 2, 3, 2) # oranges consumed each day of the week

fruits = matrix( 
data=c(apples, oranges),   # the data elements 
nrow=7,                    # number of rows 
ncol=2,                    # number of columns 
byrow = FALSE)             # fill matrix by columns instead of rows
```

Notice that the matrix function takes multiple arguments including
`data`, `nrow`, `ncol`, and `byrow`. The `byrow` argument takes a
logical value. This is a new way to code as we are placing each argument
on it’s own line so we can detail what’s happening with the `#` symbol.
R doesn’t care what happens on each line **as long as arguments are
specified, separated by commas, and enclosed by the proper
parentheses**. Let’s take a look at our fruits matrix…

``` r
fruits
```

    ##      [,1] [,2]
    ## [1,]    2    4
    ## [2,]    4    3
    ## [3,]    3    5
    ## [4,]    1    1
    ## [5,]    5    2
    ## [6,]    7    3
    ## [7,]    3    2

Notice that we didn’t use the `print()` function above, we just keyed in
`fruits`. This is referred to as *auto-printing*. We don’t actually need
to use the `print()` function any longer as we can use the *auto-print*
help here instead. We have 2 columns which are comprised of the apples
and oranges consumed each day, respectively. We have 7 rows for each day
of the week. If we want to, we can *rename* our values in fruits to
reflect our row and column names using `rownames()` and `colnames()`
functions respectively.

``` r
weekday_vector = c("Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun")
fruit_vector = c("Apples", "Oranges")
rownames(fruits) <- weekday_vector
colnames(fruits) <- fruit_vector
fruits
```

    ##     Apples Oranges
    ## Mon      2       4
    ## Tue      4       3
    ## Wed      3       5
    ## Thu      1       1
    ## Fri      5       2
    ## Sat      7       3
    ## Sun      3       2

Our rows and columns have been renamed based on the `weekday_vector` and
`fruit_vector` that we created above using the combine function `c()`.
Let’s double check the class here…

``` r
class(fruits)
```

    ## [1] "matrix" "array"

`fruits` is indeed a matrix class. It is also an array class. While a
matrix is a 2 dimensional set of data like one with rows and columns, an
array is a multi-dimensional dataset. An array can have unlimited
dimensions. Technically speaking, a matrix is a 2 dimensional array
which is why `fruits` is a matrix class *and* an array class. More often
than not, we’ll stick with matrices and dataframes (introduced next) as
opposed to arrays. An important note is that like vectors, the data
(apples and orange vectors) within a matrix must be of the same class.
For example, both the apples and oranges vectors are of a numeric class
which allowed the matrix to be built without any errors.
