% A Brief Introduction to R
% Michael Hannon
% 2013-10-03

# Acknowledgment

This document was inspired by and partially based on:

    http://www-stat.wharton.upenn.edu/~buja/STAT-541/Stat-541-R-intro.R

The R website:
=============

    http://cran.r-project.org

You should browse this web site to learn about R and the associated resources.

R and related tools for STA 032
===============================

There are four essential steps required to set up your own computer for the
work you need to do in STA 032:

  1. Install R
  2. Install RStudio
  3. Install the knitr package
  4. Start using R Markdown


Step 1: Install R
-----------------

Look again at the main R site:

    http://www.r-project.org/

It has lots of good information, including pointers to pre-compiled versions
of R for various platforms.

One thing to mention is that whenever you install R-related software, you're
asked to choose a CRAN mirror, i.e., a place from which to download the
software.  There are mirrors at UC Berkeley and at UCLA (sometimes referred to
as "CA 1" and "CA 2" or similar), and these are probably the best ones to use
at UCD.

### Getting started

Once you have R installed, you might want to open the program and type:

    help.start()

at the prompt.  Then follow the link to:

    An Introduction to R

This is really all you need to know to get started using R.  The rest of
**this** section is mainly for culture and **can be ignored** (proceed to Step
2 below).

### Windows versus Mac, linux

In the opinion of many people, Windows is really not the best platform for
this kind of computing, although it certainly *can* be done on Windows.  If
you're running Windows, you might wish to consider running some form of linux
in a virtual machine.  VirtualBox is free and is widely used:

    https://www.virtualbox.org/

Check with the instructor if you have questions about this.

### Software on linux

If you're fortunate enough to already be running some form of linux, all you
need to do is to tell your package manager that you'd like to have R
installed:

    sudo apt-get install R    #### Debian family (including Ubuntu)
    (see also: http://cran.r-project.org/bin/linux/ubuntu/README )

    sudo yum install R    #### Redhat family (including Fedora)

### Software on Mac

If you're using a Mac, you can get a ready-made version of R from:

    http://cran.r-project.org/bin/macosx/

Mac users might also want to have a look at the "Homebrew" package manager for
Macintosh:

    http://mxcl.github.com/homebrew/

Homebrew is overkill for this particular task, and it requires a bit of
fiddling to get it right.  If that's not your thing, then you should stick
with the pre-built package from CRAN.  But there are other benefits to using
Homebrew.

Step 2: Install RStudio
-----------------------

Open a browser and navigate to:

    http://www.rstudio.com/ide/download/

Select:

    Download RStudio Desktop

and pick the version that's appropriate for your system.

Step 3: Install the knitr package
---------------------------------

Strictly speaking, you can do all of the calculations for this class using
only R (from Step 1).  The use of RStudio (from Step 2) simplifies many of the
tasks involved in using R.

The "knitr" package is an add-on package for R (one of 6000+ such packages
available at CRAN and other places).  See the discussion of packages below for
some more details.

The purpose of knitr is to allow you to combine descriptive text and R code in
a single document (so-called "literate programming") and to make it easy to
generate publication-quality documents with a click of a button.

You can install knitr (and other packages) from RStudio.  Go to the RStudio
pane on the lower-right of the screen and select the "Packages" tab.  Select:

    Install Packages

by clicking on the icon near the upper-left of the pane.  Just put:

    knitr

in the Packages field of the pop-up window and then select "Install".

For the record, note that you can install packages directly from R, i.e.,
whether or not you're in RStudio.  E.g.,

    > install.packages("knitr")

Regardless of the method you use, you *are* making use of CRAN, or one of its
mirrors.  RStudio just constructs the appropriate command and executes it on
your behalf.

Step 4: Start using R Markdown
------------------------------

You're going to be using the knitr package to "knit" from an R Markdown file
to an HTML file.  This will produce a nicely formatted document that you will
then submit to SmartSite (i.e, for your homeworks, etc.).  The knitr package
will do all the formatting for you, although it *is* highly customizable.

### The "knitting" process

To knit to HTML you first have to be working in an R Markdown file, usually
named with the suffix "Rmd":

    junk.Rmd

To get some practice doing this, do the following:

    1. Open RStudio
   
    2. Open a new Rmd file:
   
        File --> New --> R Markdown

This will open a file in the upper-left pane of the RStudio display that will
ALREADY have some example content in it.  You can convert that to HTML by
selecting the:

    Knit HTML

button that appears in the row of icons just above the Rmd file.

You'll be asked to save the file.  Pick any name you like, such as:

    junk.Rmd

You should see a window pop up with some bold text, a table of numbers, and a
plot.  IN ADDITION to this pop-preview, there will be a corresponding file:

    junk.html

in you current working directory (or "folder").  That's the file that you can
send to SmartSite or to a colleague.  (There will also be an intermediate
file, "junk.md", that you can safely ignore.)

### Adding your own R code

This should show you how the process works.  Next, put your own R code into an
Rmd file if you haven't done so already.

Note that all of the R code goes into "code chunks" that look like:


```
    ```{r someLabel}

        x <- 42    #### That is, some R code goes between the backticks
    
    ``` 
```

### Some words about code chunks

Have a look at the "Chunks" icon at the upper-right of the Rmd pane.  Note, by
the way, that there are **numerous** options that you can put on `{r}` line.
The template Rmd file shows some options for figures.  Have a look at:

    http://yihui.name/knitr/options

for a detailed discussion.  It's good practice to always include a label for
the code chunk, as with `someLabel` in the example above.  This will make it
easier for you to pinpoint mistakes (i.e., just in case you make any).

### R Markdown reference

All this stuff is discussed very clearly at:

    http://www.rstudio.com/ide/docs/authoring/using_markdown

### Summary

Once you have an R markdown file with at least one code chunk and, preferably,
some discussion outside of the code chunk(s), you knit to HTML just as you did
with the template file (called `junk.Rmd` in the example above). Again, this
process creates a permanent file (`junk.html` in the example) in addition to
the preview window.  Here, "permanent" means that the file continues to exist
even after you close the preview window, and you can view the file in your
regular browser (Chrome, Firefox, Opera, etc.).

The simplest use of R
=====================

Load the ".Rmd" version of this file into RStudio.  Then place your cursor on
each of the lines of code in turn inside the following "code chunk" and send
each line to the R interpreter by typing:

    CTRL-Enter (Windows/linux)
    Command-Enter (Macintosh)

at each line.  Note: this means to hold down two keys simultaneously, the key
marked "Ctrl" on most keyboards and the key marked "Enter" on most keyboards.
(Or the key marked "command" and the key marked "enter/return" on Macintosh
keyboards.)



```r

1 + 2
1:10
2^(1:20)
runif(10)
rnorm(10)
1:10 + rnorm(10)

```


Note that some of the above will be explained only later in the course.  You
should experiment with the code until you have a reasonable understanding of it.

Some Background Information about R
===================================

R is an **Interpreted Language**
--------------------------------

This means that users type expressions and see results immediately.  For
example:


```r

for (i in 1:10) {
    if (i%%2 == 0) 
        print(i)
}
```

```
## [1] 2
## [1] 4
## [1] 6
## [1] 8
## [1] 10
```


This is as opposed to:

  1. Compiled languages (C, C++, Fortran)
  2. Point-and-click software (SAS JMP)

R is **High Level**
------------------

It operates on complex data structures such as vectors, matrices, arrays,
lists, dataframes, (all to be defined later) as opposed to C and Fortran, for
instance, that operate on individual numbers only.

This may seem awkward at first to C and C++ programmers.

**Autoprinting**
----------------

In an interactive session, whatever is typed gets printed:


```r

2
```

```
## [1] 2
```

```r
print(2)  # same
```

```
## [1] 2
```


The _print_ statement is optional here, but it may be required in
non-interactive sessions.

Why is there `[1]` preceding the results? It's because R considers numbers
as vectors of length 1. Compare with a vector of length greater than 1:


```r

1:40
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40
```

```r
print(1:40)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40
```


**Syntax**
-----------


  1. R uses largely scientific/math notation; base 10.
  2. R has a wealth of functions (examples later).
  3. Comments run from a `#` to the end of the line; no multiline comments.
  4. Spaces are irrelevant, except inside strings.  Put your cursor on each
     of the following lines and send the lines to R:


```r

    2+3
    2  +    3
    "red and blue"
    "   red   and   blue"

```


**More Syntax**
---------------

  1. Statements can run over multiple lines.  Send the following lines to R:


```r

  2 + 3 +
  4

```


But note that there has to be a "hint" to R that this is a multi-line
statement.  Send the following to R:


```r
2 + 3
+4

```


Finally, you can put multiple statements onto a single line, separating them
by semi-colons:


```r

    2; 2^10; sqrt(625)

```


There is typically no advantage to this.


Basic Data Types
================

Double Precision
----------------

Numeric objects in R are double-precision (usually 64 bits or 8 bytes) by
default.  There is no single precision, and things that "look" like integers
really are not -- they're double-precision, except as indicated below.

Here are some examples of numeric objects in R:


```r

-2
1e+05
0.002

```


All the usual unary and binary operations are allowed on numerical objects,
and the usual "math stuff" is defined as well: +, -, *, /, %%, %/%, ^, log,
sqrt, sin, acos, ...

Here are some examples:


```r

2 + 3  # Add.
5.3 * 1e+10  # Multiply.
10%%3  # Modulo.
exp(1)  # Exponentiation.
log(2.718282)  # Log of the number `e`; `log` is `e`-based.
log10(10)  # 10-based log
pi  # That's the number `greek pi`, 3.14159...
sin(pi/2)  # Angles are to be given in radians, not degrees.
sin(pi)  # Ditto.
acos(0)  # This is the inverse of cos, arccos, hence pi/2.
pi/2  # `pi` is the only hardwired constant: 3.14159...

```


Integers
--------

Numeric objects are double-precision by default, but it's possible to create
truly integer-valued objects in R.  If you add an `L` to a numeric literal,
you force it to be an integer.  And some functions in R produce integer-valued
results by default.  Here are some examples:


```r

uuu <- 7  ## a regular, double-precision numeric
uuu
str(uuu)

vvv <- as.integer(uuu)  ## 'coerce' a numeric to an integer
vvv
str(vvv)

www <- 7L  ## an integer constant; the `L` is required
www
str(www)

zzz <- 1:5  ## some functions produce integers
zzz
str(zzz)

```

Here's a **digression**: we used the term "some functions" in the example
above.  Where's the function in that example?  Send the following code to R,
and you'll see:


```r

  yyy <- `:`(1, 5)
  yyy               ## spoiler: same as 1:5
  str(yyy)
  
```

  
In other words, the "operator" denoted by `:` is actually a function that can
be called in the same way as, for instance, the `sqrt` function.  The same is
true for other operators:

```(r stillCantBeSerious, eval=FALSE, tidy=FALSE}

  `+`(7, 11)  ## same as: 7 + 11
  `*`(6, 7)   ## same as: 6 * 7

```

This is occasionally useful, but it probably won't be of much use in this
course.

End of digression.

Strings
-------

These are pieces of text, or "words".  They are delimited by single or double
quotes, but the `print` function will show them with double quotes:


```r

"a"
"a"
"abc"
"abc"

```


In C and Python strings are character vectors.  Here's an example from Python,
for instance:

```
    Python 2.7.3 (default, Aug  9 2012, 17:23:57) 
    [GCC 4.7.1 20120720 (Red Hat 4.7.1-5)] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> myString = "Now is the time"
    >>> myString[0]
    'N'
    >>> myString[4]
    'i'
    >>> myString[4:6]
    'is'
    
```

In R strings are basic types; there is no single character type.  Characters
are just strings of length 1.

There is no indexed access to individual characters and substrings in R; one
uses the `substring` function instead:


```r

substring("abcxyz", 4, 6)

```


Other basic string manipulations include:


```r

paste("my", "word")
nchar("supercalifragilistikexpialidocious")

```

There are two built-in character vectors that contain the lower and
upper case letters:


```r

letters
LETTERS

```


These are often used in examples and are sometimes used with the `paste`
function to create labels, etc.


Logical
-------

These are objects that can take on only two values: `TRUE` and `FALSE`.

*Note*: R recognizes `T` and `F` as synonyms for `TRUE` and `FALSE`.  It's a
*bad idea* to use the short forms.  (For one thing, you can *redefine* `T` and
`F`.  Try sending `T <- 42` to R, for example.)  Take the extra two seconds
and type out the whole word.  You'll be glad you did.

Another note: `TRUE` and `FALSE` are stored as the numbers `1` and `0`,
respectively.  This makes possible the seemingly dubious practice of doing
arithmetic on logical objects.

One way to generate logical values is to use the usual comparison operators:

  `<, >, <=, >=, ==, !=`

Some examples:


```r

1 < 2
1 > 2
"ab" <= "abcd"
"ab" > "ac"
"ab" != "AB"
"ab" != 2
0 == FALSE
1 == TRUE
FALSE + TRUE + TRUE + FALSE

```


Missing and exceptional values: NA, NaN, Inf, -Inf
--------------------------------------------------

### Missing values

It is sometimes the case that some data are missing.  You may ask R to read in
a table of experimental results, where, by accident, some of the results have
not been recorded;

```
    Name    Mass[kg]        Accel[m/s]
    Earth   5.98 * 10^24    9.81
    Mercury                 3.59
    Mars    6.42 * 10^23    3.77
    Jupiter 1.90 * 10^27        

```

Ooops.  Somebody forgot to write down the mass of Mercury and the acceleration
of gravity on Jupiter.  In such cases, R will go ahead and read the table but
will assign a special value, `NA`, to the missing items.  There are ways to
deal with the `NA`'s in subsequent calculations.  For instance,

```
  is.na(x)

```

will return `TRUE` if `x` has a value of `NA` and `FALSE` if it doesn't.

### Infinite numbers

R will also deal gracefully with `infinite` numbers:


```r

x <- 1/0
x
2/x
-3/0

```


### Numbers that just don't make no sense

But there are times, in mathematics and in R, where calculations lead to
results that just don't make sense in the normal framework.  In such cases, R
will assign a value of `NaN` (not a number):


```r

x <- 0/0
x

```


R is a Functional Language
==========================

R is a functional language in what you might call the colloquial sense: it has
built-in functions that return values, and you can define and use your own
functions.


```r

x <- sqrt(16)  ## `sqrt` is a built-in function
y <- x * 42  ## now using the result of the function call
y

zFn <- function(w) {
    ## write our own function to do the above
    wRt <- sqrt(w)
    wRt * 42
}

zFn(16)

```


**Note**: we'll discuss below in much greater detail the ways to define and
use your own functions in R, but you can use the `zFn` example above as a
template.  (Or take a peek ahead if you want the details now.)


R language details for geeks ;-)
--------------------------------

This paragraph is essentially a digression, but people with an interest in,
say, computer science, may have some interest in it.  R also has attributes of
a functional language in the technical sense.  It was derived originally from
Lisp.  But R is clearly NOT a purely functional language: you can use R to
generate plots, PDF files, etc., which are side-effects of function calls.
It's also the case that R incorporates two different paradigms, referred to as
`S3` and `S4`, for doing object-oriented programming.  We won't be directly
concerned with these in this class.

Statements/Expressions
======================

There are **two types** of expressions: *assignments* and *side effects*.

Assignments
-----------

These expressions allocate data structures and make variables point to them.


```r

x <- 1:3  # Allocate a vector 1,2,3 and make 'x' point to it.

```


Side effects
------------

These are essentially display operations such as printing, plotting, showing
help.  Unlike assignments, they don't change the computational state of the R
system.


```r

x <- 1:3
x
print(x)
plot(x)
help("+")  # Show the help page of addition.
help(sqrt)  # Show the help page of the square root function.
help("sqrt")  # Ditto.

```


Composite Statements
--------------------

These are multiple statements, considered as one, enclosed in "curly braces":


```r

{
    print(1)
    plot(1:10)
}

```


We saw an example of this in the function definition above, and it will
also be needed in loops (discussed below).  The notation is common to all
"C-like" languages.

Various forms of the assignment statement
-----------------------------------------

Assignments to variables come in four equivalent syntactic forms:

```
  x <- ...
  x = ...
  ... -> x
  assign("x",...)

```

Here are some examples:


```r

x <- sqrt(2 * 3)  # Root of product of 2 and 3
x = sqrt(2 * 3)  # Both can be used: '=' and '<-'
## sqrt(2 * 3) -> x # This can be used, too, if you must...
y <- c(1, 3, 10, 1, 1, 1111, 0, 1, 1)  # combine 1,3,10... into a vector 'y'
z <- 1:3  # Assign the vector containing 1,2,3 to a 'z'.
assign("x", sqrt(2 * 4))
print(x)

```


No type declarations
--------------------

Note that variables jump into existence upon assignment.  Unlike C and
Fortran, there is no need to declare variables.  The variables are not
"typed"; that is, any variable can point to data of any type, such as
vectors, lists, matrices, ...

Getting Help
============

R's built-in `help` function
----------------------------

Once you're in R, help(function) or help("function") shows the documentation
for "function".


```r

  help(sqrt)  ## And from the "See Also" section of the output:

  help("Arithmetic")
  help("log")
  help("sin")
  help("Special")

  help(c)
  help("c")   ## Same as help(c)  
  help("*")   ## help(*) does not work

```


Note that `?topic` can be used as a synonym for `help(topic)`:

```

  ?sqrt
  ?c
  ?"*"

```
Note also that most help topics in R have working, example code at the end of
the help page.  Furthermore, the R command:

```

   example(help-topic)

```

will automatically run *all* the example code for that topic.  Here's a
specific example:


```r

example(log)  ## examples of the use of the logarithm function

```


Apropos
-------

The `apropos` function in R is used to find functions related to some search
term.  For instance:


```r

apropos("char")

```


lists all functions whose names contain the string "char".

The `apropos` function is typically used when you remember that the function
you need has *something* to do with `locale` (for example), but you can't
quite recall the details.  Use:


```r

apropos("locale")

```


to pin it down.  You'll find that there are **lots** (thousands) of
functions available in R, so you really need a tool like `apropos`.

A couple of *notes*:

  1. As mentioned above, the "See Also" section of help pages is also
     useful in tracking down the function you need.

  2. The `apropos` function accepts regular expressions (to be discussed
     in more detail later).  For instance, the command:
     apropos("nchar$") will show you all the currently available
     functions that *end* in "nchar".

Vignettes
---------

There are sometimes extended discussions of packages in R (packages are
discussed below).  The extended discussions are referred to as "vignettes".

Here's an example.  Calling the `vignette()` function without an argument
lists all the vignettes that are currently available on your system.  Suppose
you call `vignette()`, and you notice the following in the output from the
function:

```
Vignettes in package ‘knitr’:

datatables                  Display Tables with the DataTables Library
(source, pdf)
knit_expand                 Templating with knit_expand() (source, pdf)
knitr-html                  An R HTML Vignette with knitr (source, pdf)
knitr-intro                 An Introduction to knitr (source, pdf)
knitr-markdown              An R Markdown Vignette with knitr (source, pdf)
knitr-refcard               knitr Reference Card (source, pdf)
docco-classic               R Markdown with the Docco Classic Style (source,
pdf)
docco-linear                R Markdown with the Docco Linear Style (source,
pdf)


```

Hmmm.  What *is* this `knitr` thing?  I think I've heard people talk about it.
Ah, I see from the list that there's a `knitr-intro` vignette (i.e., a
possibly lengthy discussion introducing me to the `knitr` package).  Let's
have a look:


```r

vignette()  ## lists all vignettes currently available
library(knitr)  ## load the knitr package into your current R session
vignette("knitr-intro")  ## assuming you're now using knitr

```



Functions: arguments and other details
======================================

Function arguments
------------------

Sometimes even if you know the function you need, you still can't remember the
arguments to the function.  One way to display the arguments is to use the
`str` function.  For example:


```r

str(rnorm)
str(runif)

```


What about the rest of the function?
------------------------------------

You can find more information about functions just by typing their names:


```r

rnorm
print(rnorm)  ## same

runif
print(runif)  ## same

```


Note that this is sometimes a dead end, because many functions in R consist of
little more than calls to some compiled C code.  On the other hand, some
functions in R are written using (other) R code, and you *can* examine those
in detail (often not for the faint of heart).  Send the command:


```r

ls

```


to R to see an example of the latter.

The `str` function considered useful
------------------------------------

By the way, the function `str` is extremely useful for finding out details
(the _str_ucture of) any R object:


```r

x <- 1:5
x
str(x)
str(mtcars)  ## a built-in data set
```


Management of Data and Functions 
================================

Listing R objects, both data and functions
------------------------------------------

Use either of:

```
  ls();  objects()

```

to list all the data structures and functions that **you** defined in the
current session.

Note also that the `ls` function takes a `pattern` argument, that allows you
to search for partial matches (among other things):


```r

xytz <- 1:5  ## you define a variable with a `t` in its name
data(mtcars)  ## you explicitly load a data set with a `t` in its name
ls(pattern = "t")  ## you look for anything with a `t` in its name

```

(Finally, note also that the `pattern` argument can be a regular expression,
which allows you to search for, say, names *ending* in `t`:

    pattern="t$"

or *starting* with `t`:

    pattern="^t"

etc., etc.  Much more on this later.)

Removing data and functions
---------------------------

Send the following code to R to see that R first creates a variable called `x`
and asssigns a value to it, then removes that variable:


```r

x <- 1:10
x
rm(x)
x

```


Packages and the `search` list
==============================

General discussion of packages
------------------------------

There are literally tens of thousands of functions, data sets, help files, and
vignettes available in R.  To make this enormous collection of information
more manageable, *related* functions, data, and documents are commonly bundled
together in a thing called a **package**.  Imagine taking all the textbooks,
class notes, exams, etc., from your last English class and putting them all in
a box, marking ENGLISH on the outside of the box, and putting the box on a
shelf in your closet. Next year, when one of your friends takes the same
English class, you take down the box and hand it to your friend, to help
him/her get through the class.  A package in R serves roughly the same
function.

R always has *some* packages loaded (available)
-----------------------------------------------

### Packages loaded by default

You can see the list of packages that R loads by default (i.e., unless you
tell it to do otherwise) by sending the following to R:


```r

getOption("defaultPackages")

```

(There's actually another package, the `base` packages that's *always* loaded,
so the command above doesn't list it.)

Packages loaded *now*
---------------------

To see what packages are currently loaded in *your* R session, send the
following to R:


```r

search()

```


What's in a given package?
--------------------------

The `search` command has given you a list of loaded packages.  What's in these
packages?  You can use the `ls` command to see the functions that are included
in a package.  For example,  to see all functions that come with the base
package of R:


```r

ls("package:base")

```


Sorting this out a bit more
---------------------------

If you've run the `ls` command above, you've seen that you get what you might
call an embarrassment of riches: hundreds of functions names, but no clue as
to what the functions do, except that function names usually give *some* clue
about purpose of the function.

You can get brief description of *some* of the functions in a package by using
the `library` command:


```r

library(help = base)

```


What else does `library` do?
----------------------------

A more-common use of the `library` command is to load additional packages into
your R session.  Send the following code to R and observe the results of the
two `search` commands:


```r

search()
library(parallel)
search()

```


Namespace
---------

### General remarks

Suppose you have *two* boxes in your closet, the one marked ENGLISH and one
marked GEOLOGY.  Your friend is taking both classes this quarter but has
declined to borrow your boxes (no room in his/her apartment). He/she asks to
see "Midterm 1".  Hmmm.  Both of your classes had a "Midterm 1".  Which one to
use?

You would disambiguate by asking your friend: do you want "ENGLISH:Midterm 1"
or "GEOLOGY:Midterm 1"?

This is the idea of a `namespace`.  Each package has its own set of variables
that are distinct from the variables in other packages, **even if the
variables have the same name**.

### Searching package namespaces

When you refer to a variable (or function) in R, R goes through, in order, the
packages listed by the `search` command and stops as soon as it finds a match.

This means that a variable of a given name can "mask" a variable of the same
name that occurs later in the search.  Here's an example in which a careless
programmer uses `ls` as the name of a function and "masks" the function `ls`
that appears in the `base` package:


```r

ls <- function(x) x  #### NOT a good idea!
ls
ls("package:base")  #### compare to the results above

```


### Dealing with namespace "collisions"

How can we deal with this?  There are two options:

  - disambiguate using the name of the package (as for ENGLISH, etc., above)
  - remove our definition of `ls`


```r

base::ls("package:base")  ## Note the double colon
rm(ls)  ## removes the first one in the search path (our defn. of `ls`)
ls

```


Getting into and out of R
=========================

Starting R
----------

When you're using RStudio, you automatically have an R session running (in the
lower-left portion of the screen).  You can also start R from a terminal
window (i.e., the command line) by typing:

    R

The "R machinery" is *exactly the same* in both cases, but RStudio provides
many additional bells and whistles.

Leaving R
---------

If you type:

    q()

at the R prompt ("> ") in any version of R, you will terminate the R session.
You can do the same in RStudio by clicking on the window-close icon (usually
an `x` located in one of the top corners of the screen).

R hates to say goodbye
----------------------

When you terminate an R session, R will ask you if you want to save the
workspace.  If you *do* save the workspace, R will create a file in your
current working directory ("folder") called:

    .RData

that contains all the variables, functions, etc., that you currently have
defined in your R session.  Here's a simple example from a command-line
session of R:

```

$ R

R version 3.0.1 (2013-05-16) -- "Good Sport"
Copyright (C) 2013 The R Foundation for Statistical Computing
Platform: x86_64-redhat-linux-gnu (64-bit)
.
.
.

> x  ## Nothing up my sleeve
Error: object 'x' not found
No suitable frames for recover()
> x <- 42  ## x is now defined
> x
[1] 42
> q()  ## I'm outta here, but I don't want to lose my work!
Save workspace image? [y/n/c]: y
.
.
.
$ R    ## start R again

R version 3.0.1 (2013-05-16) -- "Good Sport"
Copyright (C) 2013 The R Foundation for Statistical Computing
Platform: x86_64-redhat-linux-gnu (64-bit)

.
.
.

[Previously saved workspace restored]

> x  ## poof! x is here again!
[1] 42
> 

```

To save or not to save
----------------------

In cases where you're just doing some kind of exploratory work, you probably
do **not** want to save your session.  If you do save, when you start your
next R session you'll "inherit" all the mistakes, blind alleys, etc., that you
went through in your previous session.

But suppose, for instance, that you've finally figured out how to do the STA
032 homework, and you've been doing serious, useful R calculations for about
two hours now.  On your laptop.  Wait.  Are you running out of battery?
No problem: just plug in your A/C adapter and you're good to ... **Oh no!**
It's back at the apartment!  This might be a good time to exit R and save your
work.


Semantics
=========

Every assignment in R creates a *copy* of the assigned object.  The assignment
is done "by value", not "by reference" as in some other languages.

The following code chunk demonstrates this feature.


```r

a <- c(1, 3, 5)  # 
a
b <- a  # 'b' gets its own copy.
b  # We couldn't tell from this, though.
a[1] <- 2  # Assign the value 2 to the first element of 'a'.
# This yields a test of whether 'a' and 'b' point to the same object.  If
# they did, then 'b' would also have 2 in the first position.
a  # We know this.
b  # Aha!  'b' was not changed by 'a[1] <- 2'.
# Therefore, 'b' has its own copy.

```


Operator syntax and precedence
==============================

R has all the usual mathematical (and other) operators (`+`, `-`, `*`, etc.)
and many not-so-usual operators.  We'll be introducing these as we need them,
but you can find a summary on the "Syntax" help page:


```r

  ?Syntax

```


Vectors
=======

The fundamental data type in R is the **vector**.  It is an ordered collection
of items, all of the **same** data type (numeric, logical, integer, etc.).

We've already seen examples of vectors.  The following code chunk shows a few
more.


```r

c(1, 3, 4.5)  # Collect three numeric values in a vector.
c("a", "ab")  # Collect two strings in a vector.
c(TRUE, FALSE, TRUE)  # Collect three logical values in a vector.
c(2.1, TRUE)  # Not an error.  Coercion of TRUE to 1.
c(2, "a", TRUE)  # Not an error.  Coercion of 2 and TRUE to strings.

```


Coercion
--------

Note in this example, as in many places in R, if you enter the "wrong" type of
argument, R assumes you *meant* to do that and will try to convert data types
as necessary to make things work out ("work out" in this case meaning "have
all items of the same data type").  This conversion among data types is
usually referred to as `coercion` in R.

If the items are not of the same type, they are coerced as follows:

```
  string <-- numeric <-- logical

```

A peek ahead: lists
-------------------

Note that if you have a situation in which you *need* to have disparate data
types in a single data structure, you can use a generalized form of vector,
called a **list**.  These are discussed below.

You might be wondering why we bother at all to use vectors when lists are
obviously "better".  There are good reasons, and they are discussed below.

Indexing and subsetting vectors
===============================

R has a very powerful set of tools for getting at the elements of a vector
(and other data structures):

  - selection/mapping with positive integer indices
  - de-selection with negative integer indices
  - selection with logical indices
  - selection by name when vector entries are named ("associative array")

Numeric indices
---------------

Note that vectors in R are ONE-based (unlike C, but like Fortran), meaning
simply that you refer to the initial value of the vector with index `1`, and
*not* index `0`.  (You might argue that this is the "natural" way of counting:
you call the first element "element 1".  But there are advantages to using the
"unnatural" way, starting at 0.)

Here are some examples of indexing and subsetting a vector:


```r

a <- c(1, 3, 5)
a[1]
a[2]
a[3]

a[c(1, 3)]  ## using a vector to subset another vector
b <- c(1, 3)  ## the subset-specifier can be a variable
a[b]

a[c(1, 2, 1, 2, 1, 1, 1, 3, 3, 3)]  ## this one is interesting

```


In the last example we're telling R: give me the first element of `a`, then
the second element, then the first element again, then the second element
again, etc., and R happily obliges.

Exclusions with negative numeric indices
----------------------------------------

Giving R a negative index to a vector tells R to *exclude* that element (as
distinct from Python, for instance, where a negative index *selects* a
particular element).


```r

a <- c(1, 3, 5)
b <- c(1, 3)
a[-1]
a[c(-1, -3)]
a[-c(1, 3)]  ## ditto
b <- c(-1, -3)
a[b]  ## same as above
a[c(-1, -2, -3)]  ## Nothing left.

```


Logical selection
-----------------

If you index a vector in R with a collection of TRUE/FALSE values, R will
return just the elements of the vector whose positions match the positions of
the TRUE values in the index.  As you'll see, this is a powerful tool.  Here
are some examples:


```r

a <- c(1, 3, 5)
b <- c(1, 3)

a[c(TRUE, FALSE, TRUE)]
b <- c(TRUE, FALSE, TRUE)
a[b]  # same as above
a > 2
a[a > 2]  # !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
b <- (a > 2)
a[b]  # same as above

```


Just to emphasize, in the last four lines of the code chunk above we were able
to pick out all elements of the vector `a` that were greater than 2.  Using
logical operations (AND, OR, NOT) we can make very complex selection rules.
More on this later.

A word of *caution*: the vector of TRUE/FALSE values must be of the same
length as the vector you're indexing.  If it is *not*, R (again) assumes you
intended that, and it "fixes" the problem by cyclically "recycling" the
TRUE/FALSE values (if there aren't enough) or truncating them (if there are
too many).  Some examples will help:


```r

a <- c(1, 3, 5)
b <- c(1, 3)

a[FALSE]  ## c(FALSE,FALSE,FALSE)  'FALSE' is repeated 3 times
a[TRUE]  ## c(TRUE,TRUE,TRUE)

a[c(TRUE, FALSE)]  ## too short: recycle to c(TRUE,FALSE,TRUE)   
a[c(TRUE, TRUE, FALSE, FALSE, FALSE)]  # too long: truncate

(1:12)[c(TRUE, TRUE, FALSE)]  # recycle (and leave out every third item)

```

Repeated indexing
-----------------

Vectors can be indexed repeatedly.  Here are some examples:


```r

  a <- c(1, 3, 5)
  b <- c(1, 3)

  a[c(1, 3)][2]  # Select item two of a[c(1,3)], i.e. item 3 of 'a'.
                 # (Looks like a matrix element in C, but isn't!!)
  (a[c(1, 3)])[2]   # This is what the previous expression really means.  

  a[c(1, 3)][c(1, 2, 1, 2)]

```


Vector indexing and subsetting used for assignment
--------------------------------------------------

Vector indexing and subsetting can be used for assignment.  Here are some
examples:


```r

a <- c(1, 3, 5)
b <- c(1, 3)

a[1:2] <- c(10, 20)
a  # Print 'a' to see the effect of the assignment.
a[c(1, 3)] <- c(100, 200)
a
a[-2] <- c(1000, 2000)
a
a[c(FALSE, TRUE, TRUE)] <- c(10000, 20000)
a
a[2:3] <- 0
a  # '0' is repeated to fill both vector elements.
b <- 1:10
b[3:6] <- c(10, 20)
b  # 'c(10,20)' is cyclically repeated.
b[7:9] <- c(1000, 2000)  # works, but generates a warning

```


In the last example, the segment of `b` that is to replaced has length `3`,
but the thing that's being put into `b` has length `2`.  R warns you of this,
but goes ahead and does the replacement using recycling:

```

   c(1000, 2000, 1000)  ## the replacement pattern extended by one element

```

Some functions that create vectors
==================================

We've already seen numerous examples of creating a vector using the `c`
function.  Here are some other ways to create vectors.

The `c` function (or "manual entry")
------------------------------------


```r

x <- c(-1, 2, 5)  ## the 'usual' way (so far)

```


Sequences of equally spaced numbers
-----------------------------------


```r

3:10
10:3
seq(3, 10)  # where to start, where to stop
seq(3, 10, by = 1/3)  # third argument 'by' = step size
seq(3, 10, len = 4)  # where to start, where to stop, how many?
seq(letters)  # List of indexes into 'letters'

```


### Digression on data type

Note that two of the sequences above are "numeric", i.e., double-precision
floating-point.  The rest are integers.  One of the numeric sequences is
obvious.  But the other one "looks" like a bunch of integers.  Can you tell
which it is?  (Hint: the `str` function)  This is sometimes important, as you
**cannot reliably test two floating-point numbers for equality**.

Repetitions
-----------


```r

rep(3, 10)
rep(1:3, 5)
# Here is something more complex that 'rep' can also do:
rep(c(1, 2, 3, 4), c(2, 3, 2, 4))
rep(1:3, rep(2, 3))
# Logical values:
rep(TRUE, 5)
((1:10) > 5)
(1:10)[(1:10) > 5]

```


Again, note the varying data types in the above.

Miscellaneous ways of generating vectors
----------------------------------------

There are many other functions in R that you can use to create vectors.  Here
is a potpourri of some of those functions.  We'll discuss these functions in
context later in the course.


```r

    #   Random numbers:
  x <- runif(5) # Five uniform random numbers in [0,1]
  x
  y <- rnorm(5) # Five standard normal random numbers
  y

    #   Random permutations:
  x <- sample(10) # Random permutation of the numbers 1,2,...,10.
  x

    #   Read a vector from file:
  x <- scan("some.file")  ## need to have "some.file" for this to work!

```


Automatic vector extension
==========================

You may be used to seeing in other languages errors generated when you try to
index beyond the limits of an array.  Here's an example from Python:

```

  $ python
  Python 2.7.3 (default, Aug  9 2012, 17:23:57) 
  [GCC 4.7.1 20120720 (Red Hat 4.7.1-5)] on linux2
  Type "help", "copyright", "credits" or "license" for more information.
  >>> x = [1, 3, 5]
  >>> x
  [1, 3, 5]
  >>> x[1]
  3
  >>> x[4]
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  IndexError: list index out of range
  >>> 

```

This kind of thing does **not** happen in R.  If you *reference* an element of
a vector that is beyond the limits of the vector, you don't get an error
message: you get back an `NA` (meaning "I'm not complaining, but you asked me
for something that's not there".)

On the other hand, if you *assign* something to a previously non-existing
element of a vector, R will happily extend the vector, stick in at the end the
value you assigned, and fill in the intermediate slots with `NA`.

Here are some examples:


```r

  x <- runif(5)  # x has length 5.
  x[6]           # NA, not an error message.
  x[10] <- 9.99  # Not an error!  Element 10 now exists.
  x              # So do elements 6,7,8,9, filled in with NA.
  length(x)      # Assignment can extend the length.
  #     However, negative indexes (used for exclusion) can be out of bounds:
  x[-11]           # Out of bounds, but OK: "exclude item 11" = nothing to do
  x[-9]            # Ok, due to fill-in after assigning element 10.

```


*Note*: Automatic vector extension makes vectors very different from
*matrices* and *arrays* (discussed below), for which automatic extension does
**not** exist.

Named vector elements
=====================

It is possible to *name* the elements of a vector, either as part of the
definition of a vector, or after the fact:


```r

x <- c(first = 1, second = 3, third = 5, fourth = 7)
x

x <- c(1, 3, 5, 7)
names(x) <- c("first", "second", "third", "fourth")
x
names(x)

```


Why is this useful?  It makes things clearer,  but, also important, the names
can be used for indexing and subsetting:


```r

x <- c(first = 1, second = 3, third = 5, fourth = 7)
x["second"]
x[c("second", "fourth")]
nm <- c("second", "third", "second", "third")
x[nm]

## Named assignment/extension is possible:
x[c("fifth", "fourth")] <- c(10, 11)
x
## Note: 'fourth' existed and is re-assigned; 'fifth' did not exist and is an
## extension of 'x'.

## If names are not unique, the first matching name is selected:
c(a = 1, b = 2, a = 3)
c(a = 1, b = 2, a = 3)["a"]

```


Some functions in R will automatically assign names to the values they return.
Here's one important example:


```r

x <- sample(letters, size = 1000, replace = TRUE)
table(x)

```


We'll discuss both `sample` and `table` in much more detail later, but the
example above is just "randomly" grabbing 1000 lower-case letters and keeping
track (via the `table` function) of the number of `a`'s, the number of `b`'s,
etc.

Vectors with named elements as associative arrays
=================================================

Vectors with named elements in R can be used to create a limited form of
"associative arrays":

    http://en.wikipedia.org/wiki/Associative_array

(These are referred to as *dictionaries* in Python and as *maps* in C++., for
instance.)

The idea is that an object (a vector in this case) can be indexed by *keys*
that are not necessarily numeric.

Here's an example that illustrates the idea.  Suppose you'd like to look up
the salaries of employees by specifying just the *name* of the employee.  You
can create a named vector in R that lets you do this:


```r

salaries <- c(John = 35000, Brenda = 1e+05, Jim = 12000)
salaries

salaries["Brenda"]

```


There is one small "gotcha" in this: you *can* use numbers as the keys, but
they will be converted (coerced) to strings in the process.


```r

salaries <- c(35000, 1e+05, 12000)
names(salaries) <- c(5, 7, 2)
names(salaries)  ## these are strings now

salaries["2"]  ## beware that these two are not the same
salaries[2]

```


Ranking, sorting, reversing, permuting
======================================

Basic sorting
-------------

As in most languages, sorting is important in R.  Here are some functions that
are used in the context of sorting.


```r

x <- c(5:1, 5:10)  ## unsorted vector
x
rank(x)  ## what posn. would each item have if sorted?  Note the tie.
rank(x, ties.method = "first")  ## another way to deal with ties
sort(x)  ## default is to sort in increasing order
rev(x)  ## reverse the order of the entries in x

```


Permutations and other uses of `sample`
--------------------------------------

Something like the opposite of sorting, a "permutation" is a (potentially)
scrambled listing of the elements of a vector.  Permutations are important in
probability, and it's somewhat surprising that R has no built-in `permutation`
function.  The rationale may be that the built-in function `sample` will
produce a permutation.

The `sample` function is one of the more-important functions that we'll
encounter in this course.  We've seen an example of it above.  Here are some
more examples:


```r

x <- c(5:1, 5:10)  ## unsorted vector
sample(x)  ## random permutation of 'x'
sample(x, size = 100, replace = TRUE)  ## random sample of size 100 from x 
sample(x, size = 100)  ## generates error.  Why?

```


The `order` function
--------------------

From the R help page:

```
  `order` returns a permutation which rearranges its first argument into
  ascending or descending order, breaking ties by further arguments.

```

Here is the canonical example for the `order` function:


```r

x <- c(5:1, 5:10)  ## unsorted vector
x
x <- c(5, 10, 6, 1, 2, 9, 8, 7, 4, 3)
x
order(x)
sort(x)
x[order(x)]  # Same!

```


If you run the example above, you should see from the output of the `order()`
function that:

  - x[4]  would be the first element if x were sorted
  - x[5]  would be the second element if x were sorted
  - x[10] would be the third element if x were sorted

and so on.

Hmmm.  Well, *that* was underwhelming.  Why bother with `order` at all, if
it's no more than a lengthier version of `sort`?  The answer is that `order`
can be used to sort more-complicated objects, such as matrices and data
frames, which are both discussed below.  See also the example below on
parallel sorting, which is essentially the same idea.

R can sort non-numeric data, such as strings, for example.


```r

x <- sample(letters)  ## some permutation of `a`, ..., `z`
x
sort(sample(letters))  ## undoes the permutation

```



```r

x <- runif(10)  ## 10 random numbers from the interval [0, 1]
y <- -x - 100  # `y` is just another vector of the same length as `x`.
x  # Unordered parallel vectors
y
ordx <- order(x)
x[ordx]  ## sort both `x` and `y` in ascending order of `x`
y[ordx]

```


Simple statistics
=================

R has many functions for doing statistics (duh!).  Here are some of the common
ones:


```r

x <- runif(10, min = 0, max = 5)  ## generate some numbers for the things below
length(x)
sum(x)
mean(x)
var(x)
sqrt(var(x))
min(x)
max(x)
range(x)
median(x)

```


We'll discuss these in context later in the course.

Cumulative operations
=====================

R has some useful functions for computing cumulative values, e.g., a running
sum of a series of numbers.  Here are some examples:


```r

x <- 1:10
x
cumsum(x)
cumprod(x)
x <- 1:10 * c(1, -1)
x
cummax(x)
cummin(x)

```


Simple numeric functions/transformations; vectorization
=======================================================

R has built-in functions for doing all of the usual mathematical operations
(square root, cosine, etc., etc.).  An unusual feature of the R implementation
of these functions is that most of them (and many other functions in R) are
automatically "vectorized": if you give one of these functions an argument
that is a vector containing, say, seven items, you'll get back an answer
containing seven items.  Here are some concrete examples:


```r

x <- runif(20, min = -10, max = +10)
x
round(x)  ## multiple values in, multiple values out: 'vectorized'
round(x, digits = 2)
## 
round(1.5)  ## see the help page for 'round'
round(2.5)
## 
trunc(x)
ceiling(x)
abs(x)
## 
y <- c(4, 9, 16, 25, 36)
sqrt(y)
sqrt(x)  ## works but NaN's produced for negative values in 'x'
z <- c(3 + 4, 6 + 8)  ## but R DOES handle complex numbers
sqrt(z)
## 
log(x^2)
exp(1)
exp(x/100)
cos(pi)  # 'pi' is predefined; the number e=exp(1) is not.
cos(pi * c(1, 2, 3, 4, 5, 6))  ## vectorized
## 
acos(0.5)  ## trig functions use radians, not degrees
pi/3

```


Matrices
========

Matrices have many uses in theoretical and applied statistics.  See, for
instance:

    http://en.wikipedia.org/wiki/Matrix_(mathematics)

for a quick overview.

In R, matrices are implemented as *vectors*, but with additional
"meta-information" that indicates that the vectors should be viewed as
"rectangular" objects, with rows and columns.

Note that in a matrix, as with any vector, all of the elements must be of the
**same** data type (all numeric or all logical or all strings, etc.).  (Below
we'll discuss a generalization that removes this restriction.)

The elements of a matrix fill in column by column (so-called **column-major
order**), as in Fortran, but unlike C and C++ (that use row-major order).  On
the other hand, there *are* ways to tell R that you want to fill in row by
row.

Note also that you can change the *shape* of a given vector or matrix, i.e.,
make it "fatter" or "thinner", "shorter" or "taller", by supplying new values
for the number of rows and columns.  This will *not* change the order of the
elements within the matrix.

Creating a matrix "by hand"
--------------------------

Here are some examples:


```r

aDozen <- 1:12  ## a vector of integer objects
matrix(aDozen, ncol = 4)  ## reshape into a matrix with 4 columns
matrix(aDozen, nrow = 3)  ## Same; ncol is inferred; using column major

matrix(aDozen, ncol = 4, byrow = TRUE)  ## Force the use of row-major
matrix(aDozen, nrow = 3, byrow = TRUE)  ## Same

matrix(0:1, nrow = 2, ncol = 4)  ## supplied two values, asked for 8???
matrix(0, nrow = 2, ncol = 4)  ## same kind of thing

matrix(letters, ncol = 2)  ## elements are now strings
matrix(paste("UCD", letters), ncol = 2)  ## same but paste in a prefix

```


Reading a matrix from a file
----------------------------

You can read data into a matrix from a text file.  You'd typically need to
tell R to insert the data by row, and you might need to tell R to skip the
first line of the file, if that line is just a header (and not data).

```

  myMat <- matrix(scan("laser.dat",  ## need to have file "laser.dat" first!
                        skip=1),     ## skip the header line
                        ncol=4,      ## rows determined by length of file
                        byrow=TRUE)
  myMat

```

Later we'll see a more convenient way to read tabular data (`read.table()` and
related functions).

Is this object a matrix?
-----------------------

Sometimes we encounter objects in R that look like matrices but aren't.  Doing
matrix-like operations on them would result in an error.  But you can check
first:


```r

is.matrix(matrix(1:12, 3))
is.matrix(1:12)
x <- 2
is.matrix(x)
x <- 1:10
is.matrix(x)
x <- matrix(0, nrow = 3, ncol = 5)
is.matrix(x)
is.matrix(matrix(0, nrow = 3, ncol = 5))  # tautology

```


A vector by any other name would ... be a matrix?
------------------------------------------------

As we discussed above, a matrix is just a vector with an additional
attribute: the `dimension`:


```r

myMat <- matrix(as.numeric(1:12), nrow = 3)  ## force to double precision
dim(myMat)  ## Vector of length 12 with the two dimensions.
dim(myMat)[1]  ## view each dimension separately
dim(myMat)[2]
attributes(myMat)  ## another way to see the dimensions
nrow(myMat)  ## yet another way
ncol(myMat)

```


Vector to matrix and back again
-------------------------------

A vector can be turned into a matrix by assigning the dimension attribute.
And a matrix can be turned back into a vector by removing that attribute.


```r

myMat <- 1:12  # Just a vector (despite the name!)
myMat
dim(myMat) <- c(3, 4)  # NOW it's a matrix.
myMat
is.matrix(myMat)  # Let's check (it's TRUE)
dim(myMat) <- NULL  # Stripping to a vector. 'NULL' is a reserved word
myMat
is.matrix(myMat)  # Check it again (it's FALSE)

```


Names for the rows and columns
------------------------------

By default, R refers to the elements of a matrix numerically, i.e., `myMat[2,
3]`.  But it's sometimes convenient to have more-descriptive identifiers, such
as "Height" and "Weight" for the columns and "Name" for the rows.  Here's an
example where we're simply using the alphabet for the identifiers.


```r

myMat <- matrix(1:12, nrow = 3)  ## ncol has to be 4
myMat

colnames(myMat) <- letters[1:4]
rownames(myMat) <- LETTERS[1:3]
myMat

colnames(myMat)
rownames(myMat)

```


Indexing and subsetting a matrix by rows and columns
----------------------------------------------------

It's possible to subset a matrix.  This is best explained by examples.  Note
that this is generally *not* the same as similar-looking operations in C.


```r

  myMat <- matrix(1:12, ncol=4)
  myMat
  myMat[1, 4]             # Element in row 1, column 4.
  myMat[1:3, ]            # First 3 rows.
  myMat[ ,3:4]            # Last 2 columns.
  myMat[1:3, 3:4]         # Submatrix of size 3x2 (unlike Python!)
  myMat[c(1, 2, 1, 2), ]  # Repeat rows 1 and 2.
  myMat[ ,c(1, 2, 1, 2)]  # Repeat columns 1 and 2.
  myMat[c(1, 2, 1, 2),
        c(1, 2, 1, 2)]    # Repeat left-upper 2x2 matrix 4 times.
  myMat[-1, ]             # Select all but the first row.
  myMat[ , -c(2, 4)]      # Select all but columns 2 and 4.
  ##
  colnames(myMat) <- letters[1:4]
  rownames(myMat) <- LETTERS[1:3]
  ##
  myMat["A", ]            # Works only if col/rownames have been assigned.
  myMat[c("A", "C"), ]
  myMat[c("A", "C"), "a"]
  str(myMat[c("A", "C"), "a"])
  myMat[c("A", "C"), "a", drop=FALSE]  # do NOT reduce the dim of the result
  str(myMat[c("A", "C"), "a", drop=FALSE])

```


A vector is a vector
--------------------

As in the example above, selecting an individual row or column of a matrix
will generate a vector that doesn't "know" it was once a row or column of a
matrix.  R has no concept of column vectors or row vectors.

But you can force the issue by turning such vectors into Nx1 or 1xN matrices,
or you can use the `drop` argument (as above).


```r

myMat <- matrix(1:12, ncol = 4)
myMat[, 1]
is.matrix(myMat[, 1])
is.matrix(myMat[1, ])

x <- 1:10
dim(x) <- c(10, 1)
x
dim(x) <- c(1, 10)
x

is.matrix(myMat[, 1, drop = FALSE])

```


Indexing/subsetting can be used for assignment
----------------------------------------------


```r

myMat <- matrix(1:12, ncol = 4)
myMat

myMat[1, 2] <- 0  ## row 1, column 2
myMat

myMat[1, ] <- 11:14  ## row 1, all columns
myMat

myMat[, 1] <- 0  ## all rows, column 1
myMat

myMat[1, c(FALSE, FALSE, TRUE, TRUE)] <- c(7, 10)  ## row 1, last 2 cols
myMat

```


Associative-array feature for matrices
--------------------------------------

If you have set up the appropriate names for the rows and/or columns of a
matrix, you can use the names for indexing and subsetting.


```r

  myMat <- matrix(1:12, ncol=4)
  myMat

  rownames(myMat) <- c("x", "y", "z")       # like 'names(vec)'
  colnames(myMat) <- c("a", "b", "c", "d")
  myMat

  myMat["x", "d"]           # single item (vector of length 1)
  myMat["x", ]              # vector (the "x-th" row)
  myMat[ , "c"]             # vector (the "c-th column)
  myMat[c("x", "z"), c("c", "a")]  # submatrix (different from Python!)
  myMat[c("x", "z", "x", "y"),
        c("c", "a", "a")]   # col-row rearrangement

```


Column and row binding
----------------------

R has functions that let you aggregate a collection of vectors into a matrix:
`rbind` and `cbind`.  Some simple examples:


```r

x <- c(3, 1, 4, 1, 5)  # Play data.
cbind(1:5, x, x, rep(10, 5))  # Column binding.
rbind(1:5, x)  # Row binding.

```


As we discussed above, vectors are **not** thought of as columns or rows on
their own: they take on these roles inside the "cbind" and "rbind" functions.

Both functions accept an arbitrary number of conforming arguments.  Conforming
for `cbind()` means the arguments have equal numbers of rows; for `rbind()` it
means equal numbers of columns.  If vector arguments are not conforming, R
extends them cyclically or clips them but may give you a warning if the length
of the longest argument is not an even multiple of the lengths of the shorter
arguments.


```r

cbind(1:3, 0)  # second arg has size 1; 3 is an even multiple of 1
cbind(1:6, 1:3)  # size 6 is an even multiple of size 3
cbind(1:3, 1:2)  # size 3 is not an even multiple of size 2 ==> warning!
myMat <- matrix(11:14, 2)
myMat
cbind(1:3, myMat)  # clipping: the matrix arg dictates nrow

```


Generally speaking, it's a good idea to be explicit and not rely on recycling
(cyclic extension) except for the simplest cases such as repeating constants.

Above we've seen examples of binding vectors to vectors, and one example of
binding a vector to a matrix.  You can also bind whole matrices:


```r

myMat1 <- rbind(1:3, 11:13, 21:23)  # 3x3
myMat1
myMat2 <- cbind(1001:1003, 2001:2003)  # 3x2
myMat2
cbind(myMat1, myMat2)  # 3x5

```



Coercion of matrices to vectors
-------------------------------

A matrix can always be treated as a vector.  The following displays the first
five elements of a matrix and does not generate an error message:


```r

myMat <- matrix(1:12, nrow = 3)
myMat
myMat[1:5]

```


Recall that R stores data in matrices in column-major order.

Generating patterned matrices
-----------------------------


```r

  diag(5)  ## unit matrix is assumed if row/col not specified
  diag(5, nrow=3, ncol=4)  ## row/col changes behavior!
  outer(1:3, 1:4)  ## products of all combinations of 1st arg and 2nd arg
  outer(1:3, 1:4, FUN=paste)  ## but function doesn't HAVE to be "multiply"
  x <- outer(1:3, 1:4)
  x
  row(x)  ## a matrix giving just the row numbers of x
  col(x)  ## a matrix giving just the column numbers of x
  ## why do we care?  we can isolate elements of a matrix with these fns.
  row(x) > col(x)  ## isolate sub-diagonal elements
  diagx <- x[row(x) == col(x)]  ## extract the diagonal elements
  diagx
        

```



Arrays: the generalization of matrices to more than 2 indexes
=============================================================

Suppose we're interested in studying rainfall totals for California cities
over a period of years.  We find a source for the data we want, and it has a
table similar to the following for **every** year for the past `50` years.
(Table is abbreviated for simplicity.)

City        |  Jan | Feb  | Mar  | Apr
------------|------|------|------|---------
eureka      | 6.50 | 5.83 | 5.30 | 3.32
sacramento  | 3.97 | 3.82 | 3.02 | 3.30
salinas     | 3.09 | 3.08 | 2.74 | 1.03
bakersfield | 1.16 | 1.28 | 1.21 | 0.52
irvine      | 2.82 | 3.50 | 2.14 | 0.87
san_diego   | 1.98 | 2.35 | 1.81 | 0.78

We recognize that the numbers in one of these tables could be treated as a
matrix in R, so we have some hope of analyzing the data.  But how do we deal
with the fact that we've got *50* such matrices?  We can imagine that we have
a stack of such matrices, one behind the other.  Do we have to duplicate our
code fifty times?  Nope.

This stack of matrices illustrates the idea behind the `array` construct in R.
An `array` is like a matrix, but with more dimensions (not limited to just
three dimensions, by the way). We could put our matrices into an array and
index through the rows, columns, and "planes" systematically, without having
to duplicate code.

Here's a simple example of defining and indexing an array:


```r

a <- array(1:24, dim = c(2, 3, 4))  ## 2 rows, 3 columns, 4 planes
a
a[1, 2, 1]  ## row 1, column 2, plane 1
a[, 2:3, c(1, 4)]  ## all rows, columns 2 & 3, planes 1 and 4

```


Lists
=====

Recall that vectors and matrices can contain only **one** basic data type:
all numeric *or* all logical *or* all string, etc.


```r

matrix(c(TRUE, FALSE), nrow = 4, ncol = 4)  ## all logical
matrix(paste(LETTERS, letters)[1:25], nrow = 5)  ## all strings
z <- c(5, 7, "99")  ## mix of numeric and string -- not what you expect!
z  ## ALL strings now

```


It *is* possible to do calculations with this constraint.  **All** of our code
and data are stored as binary numbers inside the computer, for example, so we
*could* just code everything numerically.

The obvious downside to doing that is that it's hard to look at code and
remember what the numbers mean (did that `17` refer to *Indiana* or *Iowa*?),
and it's very easy (for most people) to make mistakes without some kind of a
hint as to the meaning of the numbers.

Lists are data structures without the restriction to one type of data.  Lists
are sequences of anything.  They can contain: basic data types, vectors,
matrices, arrays, lists (recursion), ... .   In particular, they can contain
arbitrarily nested lists of lists (which is the only point of the binary-tree
example, the details of which are otherwise unimportant in this context).

Here are some examples:


```r

  z <- list(5, 7, "99")  ## mix of numeric and string --  OK now.
  z

  # the kitchen sink

  list(1,
       "1",
       TRUE, FALSE,
       1E100,
       NA, -Inf, NULL,
       1:5,
       letters[2:5],
       list(1, 2, "a")
       )


  # Balanced binary tree:
  list(
        list(list(1, 2),list(3, 4)),
        list(list(5, 6),list(7, 8))
      )  

  # a list containing a matrix; also, elements are given names
  myList <- list(vec=1:3,
                 mat=cbind(1:2, 3:4),
                 flags=c(TRUE,TRUE,FALSE,TRUE),
                 lst=list(1:3,1:4)
                )
  myList

  # Component names are optional.  They can be glued on by force:
  x <- list(1, "a", TRUE, NULL)
  names(x) <- LETTERS[1:4]
  x

```


Note the relative complexity in the output when lists are printed.  The
flexibility comes at a price.  Here's a very simple example showing a list
with and without names:


```r

list(1, TRUE)
list(a = 1, b = TRUE)

```


Access to list items
--------------------

Access to *list items* is by index with "[[...]]", or by "$name" if names
exist:



```r

  myList <- list(vec=1:3,
                 mat=cbind(1:2, 3:4),
                 flags=c(TRUE,TRUE,FALSE,TRUE),
                 lst=list(1:3,1:4)
                )
  myList[[2]]
  myList$mat
  myList[["mat"]]

```


Note that the standard indexing, "[...]",  *does* "work", but it may not give
what you want:


```r

  myList <- list(vec=1:3,
                 mat=cbind(1:2, 3:4),
                 flags=c(TRUE,TRUE,FALSE,TRUE),
                 lst=list(1:3,1:4)
                )
  myList[1]
  myList["mat"]

  str(myList["vec"])
  str(myList[["vec"]])

```


You might think of the "[...]" as returning a "box of stuff".  The double
bracket, "[[...]]" tells R to "look inside the box".  In the example above you
can see that `myList["vec"]` is still a list, while `myList[["vec"]]` is the
contents of that list.


Access to sublists
------------------

A list is really a generalized form of vector, and, as such, the indexing
techniques used for vectors can also be applied to lists, keeping in mind the
distinction between "box" and "stuff in the box" mentioned above.  Here are
some more examples:


```r

  myList <- list(vec=1:3,
                 mat=cbind(1:2, 3:4),
                 flags=c(TRUE,TRUE,FALSE,TRUE),
                 lst=list(1:3,1:4)
                )

  myList[2:3]                           # Sublist of length 2.
  myList[2]                             # Sublist of length 1.
  myList[c(1, 4, 1, 4, 2, 3, 2, 3)]     # Out-of-order and expansion.
  myList[c("lst", "mat", "vec", "mat")] # Named access.
  myList["vec"]                         # Sublist of length 1.
  myList[["vec"]]                       # Vector!!!
  myList[c(TRUE, FALSE, TRUE, FALSE)]   # Logical selection

```


Sublists are still lists
------------------------

If you use indexing to pick off a sublist from a list, you still have to use
the list indexing described above to drill down to the contents of the
sublist.  Here are some examples:


```r

  myList <- list(vec=1:3,
                 mat=cbind(1:2, 3:4),
                 flags=c(TRUE,TRUE,FALSE,TRUE),
                 lst=list(1:3,1:4)
                )
  myList
  myList[2:3]        ## sublist with two items: $mat, $flags
  myList[2:3][[1]]   ## have to dig further to get the numerical matrix!
  myList[2:3]$mat    ## ditto
  myList[2]          ## a list of length 1: $mat
  myList[2][[1]]     ## the contents of the $mat element
  myList[2]$mat      ## ditto

```


Dataframes
==========

Background
----------

In statistics we often encounter studies that include sets of data in the form
of rectangular tables, with each row of the table representing a set of
observations for one person or thing (the "case") and each column representing
a set of measured or observed values for the variables in the study.

Here's a snippet of such a table that illustrates the idea:

```

    Observation    Sex    BMI            Age    DGEstimate    DGDifference
          1       Female  underweight     78        44             -34    
          2       Male    normal          44        32             -12    
          3       Male    overweight      72        32             -40    
          4       Male    overweight      59        44             -15    
          5       Male    normal          60        32             -28    
          6       Male    underweight     34        25              -9    
         13       Female  overweight      52        44              -8    
         14       Male    normal          67        44             -23    
         16       Male    normal          68        50             -18    
         17       Female  overweight      35        12             -23    

```

Note some of the features of the table:

  - There is a *header* line, identifying the variables.  This is optional but
    useful.
  - The variables for a given observation (row) are of different data types:
    integer, string, numeric (could also be logical).

As we discussed previously, all of this information **could** be encoded
numerically.  For instance we might have:

  - Sex
    - Male   --> 0
    - Female --> 1 

  - BMI
    - underweight --> 0
    - normal      --> 1
    - overweight  --> 2

Then our table would look like:

```

    Observation  Sex  BMI   Age    DGEstimate    DGDifference
          1       1    0     78        44             -34    
          2       0    1     44        32             -12    
          3       0    2     72        32             -40    
    .
    .
    .

```

This is a very `1960's` approach and would almost certainly lead to errors in
entering and interpreting the data.

Thus, we seem to have a dilemma: use an all-numeric approach, in which case
our data could be encoded in a matrix, or use the appropriate combination of
numeric and non-numeric data for clarity, in which case we could analyze it
using -- what???

The answer is to use a *dataframe*, which is an R structure that *looks*
something like a matrix, but with the flexibility to have different data types
in different columns.  The columns are actually stored as lists.

Making a data frame "by hand"
----------------------------

The function "data.frame()" can bundle conforming vectors, matrices, other
dataframes into a single dataframe:


```r

  myFrame <- data.frame(someNumbers=1:3,
                        someCharacters=c("a", "b", "c"),
                        someLogicals=c(TRUE, FALSE, TRUE))

  myFrame

```


Here are a couple of auxiliary functions for dataframes:


```r

  myFrame <- data.frame(someNumbers=1:3,
                        someCharacters=c("a", "b", "c"),
                        someLogicals=c(TRUE, FALSE, TRUE))

  is.data.frame(myFrame)               # Checking type.
  someMatrix <- cbind(1:4, 11:14)
  someDF <- as.data.frame(someMatrix)  # Coercing a matrix to a dataframe.

  someMatrix
  str(someMatrix)
  someDF
  str(someDF)

```


Operations on dataframes
------------------------

Many of the operations we've discussed above for matrices carry over to
dataframes:


```r


  newFrame <- data.frame(someNumbers=1:3,
                        someCharacters=c("a", "b", "c"),
                        someLogicals=c(TRUE, FALSE, TRUE),
                        someMoreNumbers=c(3, 1, 4)
                       )

  dim(newFrame)
  nrow(newFrame)
  ncol(newFrame)
  rownames(newFrame)
  colnames(newFrame)
  length(newFrame)   # NOT equal to the number of rows!
  newFrame[ , 3]     # Col 3 coerced to vector.
  newFrame[2, ]      # Sub-dataframe with row 2, NOT coerced to vector!
  str(newFrame[2, ])
  newFrame[ , 2:3]   # Sub-dataframe consisting of cols 2 and 3.
  newFrame[2:3, ]    # Sub-dataframe consisting of rows 2 and 3.

```


Why is `newFrame[2, ]` not coerced to a vector?  Because the items in the
different columns in row `2` might in general not all be of the same data type
(and in fact in this case they are *not* of the same data type).


It sometimes looks like a matrix, but it isn't
----------------------------------------------

We haven't discussed matrix multiplication yet, and we likely won't use it in
this course, but it *is* possible to do linear-algebra-style matrix
multiplication in R:


```r

  aMat <- rbind(c(1, 0, -2), c(0, 3, -1))
  aMat
  bMat <- cbind(c(0, -2, 0), c(3, -1, 4)) ## could also have used rbind
  bMat

  aMat %*% bMat

  aFrame <- data.frame(aMat)  ## coerce aMat to a dataframe
  aFrame           ## LOOKS like aMat, but...
  aFrame %*% bMat  ## generates an error: a data frame is not a matrix

```


Making a dataframe from other data sources
------------------------------------------

The function `read.table()` will read a table from a text file into a
dataframe.  Here's a simple example.  First, here are the contents of a file,
`atable.dat` as seen by the file system outside of R:

```
  $ cat atable.dat ## "cat" is used to display the contents of a file
    Id Age  Weight Height  Gender Smoker
    3  18    150     65    Female  FALSE
    1  21    160     68     Male   TRUE
    4  45    180     65     Male   FALSE
    5  54    205     69     Male   FALSE


```

Now we read the contents of that file into R.  Note that if you want to run
this example, you first have to *create* the file outside of R.  You can use
the text editor of your choice to make the file, but the file *does* have to
be a text file (i.e., not a Word document, for instance).

Also, you need to create the file in the place where R is currently looking
for files, that is, the place in the file system that the R command:

```

  getwd()

```

shows you.


The data end up looking pretty much the same in R as outside of R:


```r

myTable <- read.table("atable.dat", header = TRUE)
myTable

```


We had to use `header=TRUE` so that R wouldn't consider the strings "Id",
"Age", etc., as part of the data.

There are *many* optional arguments to `read.table()`, and there are also a
number of related functions, the most common of which is `read.csv` for
reading a table (typically) exported from a spreadsheet.  See the help page
for `read.table` for details.  Here's an excerpt:

```

  read.table(file, header = FALSE, sep = "", quote = "\"'", dec = ".",
             row.names, col.names, as.is = FALSE, na.strings = "NA",
             colClasses = NA, nrows = -1,
             skip = 0, check.names = TRUE, fill = !blank.lines.skip,
             strip.white = FALSE, blank.lines.skip = TRUE,
             comment.char = "#")

```

Note that the first argument to `read.table()`, the *file* argument, can
actually be any of the things that are called *connections* in R, the
most-common example of which is a URL.  (I.e., you can read data directly from
the web.)  Here's an example:



```r

  myNewTable <- read.table("http://lib.stat.cmu.edu/jcgs/tu",
                           skip=4,
                           header=TRUE)
  head(myNewTable)  ## show just the first few rows of the dataframe
  str(myNewTable)

```


Sorting a data frame
--------------------

In a previous section we noted that the `order()` function is useful in
sorting matrices and data frames.  We're now in a position to give an example
of that.

In the following example, we're given a data frame containing some information
about a few people.  (For simplicity we're constructing the data frame in the
example, but you can imagine we got the data from some outside source, so that
we have no control over the initial format.)

Suppose that we wish to sort the data frame according to the heights of the
people in the data frame.  We can pull the heights out of the data frame, but
then what?  It might be an interesting exercise to try to find another way to
do this, but the canonical approach is to use the `order()` function:


```r

  myDF <- data.frame(rbind(list(72, 160, "blue", "Fred"),
                           list(60, 120, "green", "Bob"),
                           list(84, 250, "brown", "Ron")
                          )
                    )

  colnames(myDF) <- c("ht", "wt", "eyeColor", "name")
  myDF

  heights <- unlist(myDF$ht)
  heights

  ordHts <- order(heights)
  myDF[ordHts, ]

```


If you run the code chunk above, you'll see that the first row does indeed
contain the smallest height, and, furthermore, all the other attributes of
short, green-eyed Bob also appear in the first row, as they should.


Flow control: conditionals and loops
====================================

R has the kinds of conditional and looping statements that you would expect to
find in a "C-like" language, along with some you might not expect.  R also has
a family of functions (the "apply" family -- see below) that (a) are in most
cases better to use for looping than the "C-like" constructs and (b) are
similar in spirit to the "transform" function, for instance, in the C++
standard library.

**Note**: you don't have to know anything about C or C++ to understand and use
these features of R.

Making decisions: the `if` statement
------------------------------------

You use the `if` statement as follows:

```

  if (condition is true)
     do something

```

In the pseudo-code above, the "do something" part can be either a single
statement or a compound statement (multiple single statements enclosed in
curly braces `{...}`).

The form of the statement above implicitly says that if the `condition` is
*not* true, then never mind -- just continue what you were doing.  Don't
interrupt the flow of the program.

It's typically the case that you check to see if `condition` is true, and if
it's *not*, you still do want to interrupt the flow of the program and do
something *else*.  R provides the `else` clause for this purpose.

Some examples may clarify:


```r

mVec <- 1:12  # play data

if (length(mVec) > 15) print("mVec is longer than 15")  ## nothing printed

if (length(mVec) > 10) {
    print("mVec is longer than 10")
    mVec2 <- mVec * 2  ## just doing some other stuff inside the {...}
    print(mVec2)
} else {
    print("length of mVec <= 10")
    mVec4 <- mVec * 4  ## again, just to show other stuff can be done
    print(mVec4)
}

```


A couple of comments:

(1) The use of the `print` function is optional in interactive use.  It never
*hurts* to use it, but it's *required* in some cases (inside functions or
loops, for instance):


```r

  foo <- function(x) {
      x
      y <- x^2
  }

  foo(7)

  bar <- function(x) {
      print(x)
      y <- x^2
  }

  bar(7)

```


(2) There is some latitude in the placement of the curly braces.  It is to
some degree just a matter of the style you prefer.  But if you don't put the
`{` on the same line as the `else`, R will sometimes get "confused".  So:

```

  } else {   ## good
  ...
  }

  } else  ## bad
  { ...
  }

```

Something a little different: the `ifelse` function
---------------------------------------------------

We've been talking about `if` and `else` clauses in R.  These are flow-control
constructs.  R also has *function* called `ifelse()` that is really a
combination of looping and conditional statements rolled into one.

And like many other functions in R, `ifelse()` is *vectorized*, meaning it can
operate on all elements of a vector "at once" (at least from the perspective
of the programmer -- the code may or may not run all at the same time on the
actual hardware).

Here's are some examples:


```r

ifelse(c(TRUE, FALSE, TRUE), c(1, 2, 3), c(-1, -2, -3))  # c(1, -2, 3)

multipliers <- rep(1:4)/2
pies <- pi * multipliers
pies
sin(pies)
ifelse(sin(pies) >= 0, rep("positive", 4), rep("negative", 4))

```


The `ifelse()` function processes the three arguments in parallel.  If an
element in the *first* argument is `TRUE` (or is some expression that
*evaluates* to `TRUE`) the result returned from the function will be the
corresponding item in the *second* argument.  If an element of the *first*
argument evaluates to `FALSE`, the result returned will be the corresponding
item in the *third* argument.

What happens if the second and third arguments to `ifelse()` are not
"conforming", i.e., don't have the same number of elements as the first
argument?  R will "recycle" the elements (extend them cyclically) until there
*are* enough of them:


```r

## simulate some coin tosses
tosses <- runif(10)  ## much more on this later in the course
tosses
ifelse(tosses > 0.5, "Heads", "Tails")  ## recycle to 10 Heads, 10 Tails

```


The `for` loop
--------------

The `for` loop executes a statement, usually a compound (`{...}`) statement,
once for every item in a given vector.  It has the general form:

```

  for (dummyName in someExpression) someOtherExpression

```

The `dummyName` is assigned, in turn, each of the values in `someExpression`,
and `dummyName` can then be used in calculations in `someOtherExpression`.
Here's an example:


```r

  for (nextNum in c(10, 100, 1000)) {
      nextProduct <- 2 * nextNum
      print(nextProduct)
  }

```


Note that the braces are optional if there is only one statement in the loop,
but it's probably a good idea to use them in all cases.

Note also the following warning from the Introduction to R manual on the R
Project web site (

http://cran.r-project.org/doc/manuals/R-intro.html#Repetitive-execution

)

**Warning**: for() loops are used in R code much less often than in compiled
languages. Code that takes a "whole object" view is likely to be both clearer
and faster in R.

This is discussed in more detail below.

The `while` loop
----------------

The `while` loop is a first cousin to the `for` loop (and one can be
formulated in terms of the other).  The general syntax is:

```

  while (someExpressionEvaluatesToTRUE) someOtherExpression

```

Here's an example in which we pick a random number between 0 and 1 and stop
when the number is sufficiently large:


```r

  howMany <- 0  ## count how many samples it takes
  while(runif(1) < 0.95) {
      print("Not yet...")
      howMany <- howMany + 1
  }

  print(paste("It took", howMany, "samples."))

```


*Note*: the `paste` function in the example above does just what the name
implies: it "pastes" together a bunch of strings, converting the arguments to
strings in the process as necessary (e.g., converting the `howMany` numeric to
a string in the above).  Using `paste` is a simple way to format your output.

The `next` and `break` commands
-----------------------------------

If you *do* find that you have to use explicit loops (`for` or `while`) in R,
you may also find that you need to alter the program flow, based on some
computed condition.  R has a number of constructs to do this, the most common
of which are `next` and `break`.

The `next` command tells R to proceed with the next step in the
iteration, if there is one.  Here's an example in which we want to print out
only the odd numbers in a sequence:


```r

  for (aNum in 1:20) {
      if ((aNum %% 2) == 0) next
      print(aNum)
  }

```

Of course we could have done the same thing in numerous other ways, but this
illustrates the idea: if the number is even, just go on to the next number in
the `aNum` vector.

The `repeat` loop
-----------------

The `repeat` loop will just go on forever unless it contains some code to
break out of the loop.  Here's a toy example, just to illustrate the concept:


```r

  nextNum <- 0
  repeat { 
    nextNum <- nextNum + 1
    print(nextNum)
    if(nextNum > 20) break() 
  }

```


A more-realistic example might be to implement an interactive dialog with a
user of your program, asking for input from the user, checking the input for
validity, and breaking out of the loop only when the input is valid.  Here's
some pseudo-code:

```

  repeat {
    Ask user for some input
    if (input is valid) break()  ## if it is NOT, just keep bugging the user!
  }
  go on to process the now-valid input

```

As usual, this kind of loop could be implemented in various other ways.


Writing functions
=================

We've already had one *ad hoc* example of defining and using your own function
in R (the `zFn` example above).  Now we want to explore the topic
systematically.

Syntax
------

Here's a simple example showing the *syntax* ("grammar") of some functions:


```r

myFn1 <- function(x) {
    plot(x)
}
myFn2 <- function(x) {
    2 * x
}

```


That is, you define a function by using the `function` keyword, followed by
*mandatory* parentheses `(  )`, optionally containing the parameter or
parameters to be sent to the function when it is later executed. Next comes
the `body` of the function: a statement or statements in which you tell the
function what you want it to do.  Finally, you assign your function definition
to a variable (`myFn1`, `myFn2`).

**Notes**

  - The "Fn" part of the variable name has no particular meaning to R. We're
    using it here just to help *us* remember that the thing is a function and
    not, say, a vector or a list.  "elephant" or "socrates" or "Lord.Vader"
    would all be perfectly acceptable (to R) function names.

  - In our examples we routinely include a single argument `x` in our function
    definitions: `function(x)`.  This is just to simplify the examples.  Your
    functions can have as many arguments as you like:

      + myFn <- function() { } ## zero arguments; parens STILL required
      + myFn <- function(zebra) { } ## one argument (named "zebra" here)
      + myFN <- function(dorothy, toto) ## two arguments
      + myFn <- function(alpha, beta, gamma) ## three arguments
      + myFn <- function(math, physics, ...) ## 2 + an unspecified number

Semantics
---------

Here are some words about *semantics*, that is, the *meaning* of function
statements (as opposed to *syntax*, the *structure* of function statements).

Note that `myFn1` *does* return a value (see below), but its real mission in
life is to create a so-called "side effect", namely (in this case), a picture
(plot) of the stuff you give it when you call the function.  On the other
hand, `myFn2` has no side effects, and it does return a *meaningful* value:


```r

  myFn1 <- function(x) {
      plot(x)
  }
  myFn2 <- function(x) {
      2*x
  }

  myFn1(1:10)  # plots 1, 2, ..., 10
  myFn2(1:10)  # returns the vector containing 2, 4, ..., 20

```


More semantics
--------------

A little more about semantics: functions are *first class citizens*, that is,
they can be assigned, printed, passed as arguments, etc.  Here are some
examples:


```r

  myFn1 <- function(x) {
      plot(x)
  }
  myFn2 <- function(x) {
      2*x
  }

  myFn2            # Print the function.
  print(myFn2)     # Same.
  myFunx <- myFn2;
  myFunx(1:5)  # Application:   len <- length;  len(1:10)
  (function(x) {
    2*x
  })(1:10)   # define and call the function "simultaneously"
  printFn <- function(f) print(f)
  printFn(1:5) # "ordinary" (integer) argument
  printFn(printFn)  # a *function* argument to a function.  (prints itself!)

```


Return values
-------------

A function returns a value.  Sometimes that's interesting, sometimes not:


```r

myFn1 <- function(x) {
    plot(x)
}
myFn2 <- function(x) {
    2 * x
}

x <- myFn2(1:10)  ## myFn2 returns a value we probably want to keep
x
x <- myFn1(1:10)  ## myFn1 returns a NULL, but it DOES plot (side effect).
x

```


Syntax *and* return values
--------------------------

And now here are a few more words about syntax.  All of the following are
equivalent ways of writing `myFn2()`.


```r

    myFn2 <- function(x) {
        2*x
    }   # The original.

    myFn2 <- function(x) 2*x       # Single-statement bodies don't need braces.

    myFn2 <- function(x) {
        return(2*x)
    }   # Make the return explicit.

    myFn2 <- function(x) {
        y <- 2*x
        y
    }  # Value of last statement is returned.

    myFn2 <- function(x) {
        y <- 2*x
        return(y)
    }  

```


It's worth emphasizing that the value of the *last* statement in a function
will *automatically* be returned.  In most cases R programmers will omit the
explicit `return` statement, but using `return` can sometimes help to clarify.

A realistic example
-------------------

Here's an example of defining and using a function with multiple arguments and
multi-statement bodies:


```r

  myFn3 <- function(x, y) {
      pdf(file="test.pdf", width=5, height=5)  ## make a plot in a PDF file
      par(mgp=c(1.8, 0.5, 0), mar=c(3, 3, 2, 1))  ## set some graphics params
      plot(x, y, pch=16, cex=0.5)
      dev.off()  ## close the newly-created PDF file
  }
  myFn3(1:100, rnorm(100))  ## send some data to be plotted

```


The details of the above example are not important at this point, but you can
see:

  - The function has multiple (two) arguments
  - The function has multiple statements in the body of the function
    (technically just a single compound statement)
  - If you run the code, you should get a file "test.pdf" with a picture in it

Arguments to functions
----------------------

Ordinarily, for functions with multiple arguments, the formal arguments (the
ones in the *definition* of the function) get assigned the actual arguments
(the ones in the *calling* of the function) in order.  But if a function is
called with *named* arguments, the arguments can appear in any order.  (There
is no great advantage to this for functions with short argument lists, but it
can be useful in more-complicated cases, especially in conjunction with
default values for arguments -- see below.)  Here's an example:


```r

  myArgsFn <- function(x, y) {
      par(mgp=c(1.8, 0.5, 0), mar=c(3, 3, 2, 1))  ## set some graphics params
      plot(x, y, pch=16, cex=0.5)
  }

  myArgsFn(1:10, (1:10)^2) ## x gets 1:10, y gets (1:10)^2 

  myArgsFn(y=(1:5)^3, x=1:5) ## x gets 1:5, y gets (1:5)^3 

```


It's possible to define *default* values for arguments when you define a
function.  That is, if a given argument has a default value in the definition
of a function, and you *omit* that argument when you call the function, the
argument takes on the default value for the duration of the function.

Note that doing this makes it imperative that you name the arguments that you
*do* include when you call the function.  Here's an example.  **Note**: the
point of the example is to show that a function defined, in this case, with
seven arguments, can be successfully called with zero to up to seven arguments
(a maximum of five in the example), *provided* the formal arguments have been
assigned default values during the definition of the function.

It is **not** necessary to focus on the details of the function at this point.


```r

  myFn4 <- function(y=rnorm(20),
                    x=1:length(y),
                    cex=0.5,
                    pch=16,
                    w=5,
                    h=5,
                    new=TRUE) {

    if(new) pdf(file="newtest.pdf", width=w, height=h)
    par(mgp=c(1.8, 0.5, 0), mar=c(3, 3, 2, 1))
    plot(x, y, pch=pch, cex=cex)  ## "cex" in "plot" gets value of input "cex"
    if(new) dev.off()
  }                     
  myFn4()   # All arguments defaulted.  PDF file created.
  myFn4(1:25, rnorm(25))  # 1st and 2nd argument passed by order.
  myFn4(1:25, rnorm(25), new=FALSE)  # Last argument is 7th by order, so needs name.
  myFn4(1:25, rnorm(25), new=FALSE, cex=0.2) # cex is out-of-order
  myFn4(1:25, rnorm(25), new=FALSE, cex=1, pch=3)
  myFn4(x=1:25, y=rnorm(25), pch=2, w=10, h=2) # x= and y= not needed but more readable
  myFn4(cex=0.2)
  
```


Notes:

  - The details of the plotting, etc., are unimportant at this point.  Just
    focus on the handling of the arguments.
  - Note that "downstream" arguments can make use of the "upstream" arguments.
    In the example above, the default value of `x` depends on the "upstream"
    argument `y`.
  - In the `plot` statement in the function definition, the first `cex` is a
    parameter to be passed to the `plot` function.  The second `cex` is the
    current value of the input argument `cex`.



Functions returning complex data structures
-------------------------------------------

"Complex" in this context means "something other than a single number (or
single logical, etc.)", not anything to do with complex numbers (`a + b*i`).
The point is that if R always returns the last thing evaluated in a function,
how do you make it return more than one thing?

The answer is to pack your return values into a `list` and return the `list`.
In the special case that all the items being returned are of the same type,
you can pack them into a vector ("c(x, y, z)", rather than "list(x, y, z)").

Here's a simple example.  Note that we assign names to the returned list
items, so that they explicitly appear in the result of the function call.


```r

  convToPolar <- function(x, y) {
      r     <- sqrt(x^2 + y^2)
      theta <- atan2(y, x)
      list(r=r, theta=theta)  ## "name r = computed value of r", etc.
  }

  convToPolar(1, 1)  ## expect to get root(2), 45 degrees (pi / 4)
  pi /4

```


Function arguments passed by value
----------------------------------

In R, arguments are passed to functions "by value", *not*  "by reference" or
"by name".  This means that all arguments get *copied* into a function, so
that any calculations done on those arguments inside the function do *not*
affect the original variables.  Here's an example.


```r

  alpha <- 1
  omega <- 26

  myFn5 <- function(x, y) {
    z1 <- x * y
    omega <- sqrt(z1)  ## this value gets returned; this omega then discarded
  }

  print(myFn5(2, 32))
  print(omega)  ## this omega still has the original value

```


Here's another example:


```r

myFn5 <- function(x) {
    x[1] <- Inf  ## vector is copied to the function; 1st element modified
    x  ## return the now-modified vector
}

x <- 1:3
x
myFn5(x)
x  ## no change in this x

```


Notes:

  - There *are* ways to simulate call by reference, using an `environment`,
    for example, but we won't be dealing with these.
  - R tries to be "smart" about copying arguments and won't copy things
    unless they're *modified* inside the function.

R uses *lexical scoping*
-----------------------

This topic is somewhat technical for a statistics course, but *somebody* is
going to ask about it.  Feel free to skip to the next section.

We saw above that variables in R have some kind of restriction on the places
where they can be "seen".  The `x` inside a function may not be the same as
the `x` outside that function, for instance.

The variable names used in a function in R fall into one of three categories,
as illustrated by the following (taken from the R documentation):


```r

  foo <- function(x) {
      y <- 2 * x ## "y" is a LOCAL variable, defined only inside the function
      print(x)   ## "x" is a FORMAL parameter (argument) from the arg list
      print(y)   ## "y" is assigned inside foo, so still a local variable
      print(z)   ## "z" is a FREE variable -- definition is nowhere in sight!
  }

```


When R finds a *free* variable (`z` in the example) it tries to find a value
to assign to it.  With *lexical scoping* (also known as *static scoping*), R
will look in the enclosing piece of code, i.e., the place or *environment*
where the function was **created**.  If R fails to find the variable there, it
will continue to keep looking in enclosing environments until it either finds
a value or reaches the top of the food chain, the so-called *global
environment*.

Take a look at the following two examples.


```r

  z <- 42
  foo <- function (x) {
      y <- 2 * x
      y + z
  }

  z <- 314
  foo(7)  ## result: 328.  Why not 56?

```


If you run the code in the example above, you should get a result of `328`.
But why?  This is lexical (static) scoping, and the value of the free
variable, `z`, at the time the function `foo()` was defined was `42`.  The
result suggests that R is doing *dynamic* scoping: the value used for `z` was
the value assigned to `z` most recently.  But that's just a coincidence.

What happened was that R looked for a value of `z` inside the function `foo()`
and didn't find it.  R then looked in the enclosing environment, which is
essentially a "box" with variables inside.  In this case the enclosing
environment was the top-level environment, and, indeed, inside that "box" was
a variable named `z`, and it had a value `314`.

The impact of lexical scoping is more evident in the following example.  In
this example we've got a function, `new.Fn`, that is used to produce *other*
functions.



```r

  nnn <- 5
  new.Fn <- function(nnn) {
    fn1 <- function(x) {
      x^nnn
    }
    fn1  ## return value is a function!
  }

  someFn <- new.Fn(2)
  moreFn <- new.Fn(3)

  print(someFn)
  print(moreFn)

  nnn <- 10

  someFn(4)
  moreFn(2)

```


If you run the code in the example above, you'll see that:

  1. The two newly-created functions appear to be identical, *except* for
     their environments.
  2. Changing the value of `nnn` at various places in the code has
     *no effect* on the behavior of `someFn` or `moreFn`, even though both
     functions print out as: `x^nnn`.

The relevant value of `nnn` is the one that existed at the time the functions
were constructed.  When `someFn` was created, for instance, a value of `2` was
passed to `new.Fn`, and *that* was the value of `nnn` *at the time `someFn`
was created*.

Hence, `someFn` is *always* going to raise its argument to the power of `2`,
regardless of the value that `nnn` might have in some other environment.

Scoping: a word of caution
--------------------------

It's a little dangerous to depend on R to go off looking for your variables
and using whatever it turns up.  A better idea is to pass to your functions
*all* the variables they're going to use.  That way you at least know where
the values came from.

There are sometimes reasons *not* to pass all the variables to your functions,
but it's probably a good idea to start by passing in everything and then back
off of that ideal only to the extent necessary (for performance or other
reasons).

A better way of looping: the "apply" family
===========================================

Background
----------

What is "apply" in this sense?  It means to "apply" a function to a set of
arguments.  Sort of a loop without a loop.  Have a look at:

    http://en.wikipedia.org/wiki/Apply

for much more than you currently need to know about apply-style functions.

Why do we care about apply-style functions?  Quoting from:

http://nsaunders.wordpress.com/2010/08/20/a-brief-introduction-to-apply-in-r/

    At any R Q&A site, you’ll frequently see an exchange like this one:
    
        Q: How can I use a loop to [...insert task here...] ?
        A: Don’t. Use one of the apply functions. 

Besides the dialog, the site mentioned above has a nice summary of many of the
apply-style functions available in R.  Type:

```

  apropos("apply")

```

at the R prompt to see a brief listing of such functions.

We'll be most concerned with `lapply`, `sapply`, and `replicate` (which
doesn't have the word "apply" in its name but is still an apply-style
function).  We may also make some use of `apply` and `mapply`.

`lapply`
--------

Here's an excerpt from the R help page for `lapply`:

```

  Description:
  
       `lapply` returns a list of the same length as `X`, each element of
       which is the result of applying `FUN` to the corresponding element
       of `X`.
  
  Usage:
  
       lapply(X, FUN, ...)

```

Notes:

  - `lapply` *always* returns a list
  - `X` does *not* have to be a list.  It's basically just an object that
     has individual elements that R can identify.
  - the `...` indicates that the function, FUN, might require some
    *additional* arguments, besides the one that's "fed" to it by `lapply`


Here are some examples:


```r

  myVec <- c(2, 3, 5, 8)  ## iterating over a numeric vector
  someSquares <- lapply(myVec, function(someNum) {
                                 someNum^2
                                }
                       )
  someSquares
  unlist(someSquares)  ## don't always need or want a list

  myList <- list(42, FALSE, "groundhog")  ## iterating over a list
  lapply(myList, function(nextItem) {
                   if (is.numeric(nextItem)) {
                     nextItem * 3
                   } else {
                     nextItem
                   }
                 }
        )

  myMat <- matrix(rbind(c(2, 4), c(3, 5)), nrow=2)  ## iterate over a matrix
  myMat

  lapply(myMat, function(xij) {
                  xij^3
                }
        )

  myVec <- c(10, 100, 1000)  ## the "log" function has an optional 2nd arg
  myVecLog.e <- lapply(myVec, log) ## default is base "e"
  unlist(myVecLog.e)

  myVecLog.10 <- lapply(myVec, log, base=10)  ## here's the "..." thing
  unlist(myVecLog.10)

```


`sapply`
-------

Here's an excerpt from the R help page for `sapply`:

```

  Description:
  
       `sapply` is a user-friendly version and wrapper of `lapply` by
       default returning a vector, matrix or, if `simplify = "array"`, an
       array if appropriate, by applying `simplify2array()`.  `sapply(x,
       f, simplify = FALSE, USE.NAMES = FALSE)` is the same as `lapply(x,
       f)`.
  
  Usage:
  
       sapply(X, FUN, ..., simplify = TRUE, USE.NAMES = TRUE)

```

Stripped of some of the jargon, this means that `sapply` is a "simplifying"
version of `lapply`.  For instance, recall from the examples for `lapply` that
we repeatedly used the `unlist()` function in cases where we knew that all
elements returned by `lapply` were of the same type.  In those cases, we had
numeric vector in, list out.  Then unlist.  There must be a simpler way.
That's where `sapply` comes in.

Here's an example:


```r

  myVec <- c(2, 3, 5, 8)  ## iterating over a numeric vector
  someSquares <- sapply(myVec, function(someNum) {
                                 someNum^2
                                }
                       )
  someSquares

```


Numbers in, numbers out -- no need to `unlist`.

**Caution**: be careful of getting into the habit of using `sapply` for all
types of iterations.  Here's an example using a slightly more-complex object:
a list of matrices.  Run through the following code, and you'll see that
`sapply` *guesses* what you want and simplifies to a form you probably *don't*
want, while `lapply` does the thing you probably *do* want.



```r

  mat1 <- matrix(rbind(c(2, 4), c(3, 5)), nrow=2)
  mat1
  mat2 <- matrix(rbind(c(20, 40), c(30, 50)), nrow=2)
  mat2

  someMats <- list(mat1, mat2)
  someMats
  sapply(someMats, function(inMat) {
                     2 * inMat
                   }
        )

  lapply(someMats, function(inMat) {
                     2 * inMat
                   }
        )

```


Of course, it *is* possible to use `sapply` safely in the more-complicated
cases.  In the example above, just adding `simplify=FALSE` after the function
definition would make `sapply` work the same as `lapply`.  But as a rule of
thumb, it's better to use `sapply` only in simple cases (numeric in, numeric
out, for instance).

`replicate`
----------

Here's an excerpt from the R help page for `replicate`:

```
  Description:
  
       `replicate` is a wrapper for the common use of `sapply` for
       repeated evaluation of an expression (which will usually involve
       random number generation).
  
  Usage:
  
       replicate(n, expr, simplify = "array")

```

OK, so now we have a wrapper (`replicate`) on top of a wrapper (`sapply`).
Where will this all end?  As the help page indicates, there *is* a use for
this shorthand, in the appropriate context, and we'll see a fair amount of
`replicate` in this course.

It's hard to give a meaningful example without some more background.  Here's a
toy example in which we generate three sets of ten random numbers from a
normal/Gaussian/"bell-shaped" distribution.  (Much more on this later in the
course.)


```r

  myResults <- replicate(3, rnorm(10))
  myResults

```


In the context of this course you would typically write your own function that
involved some degree of randomness (whatever that means) and evaluate that
function repeatedly as a sort of numerical experiment to see what you can say
about the randomness.  In pseudo-code:

```

  myFunction <- function(x, y, z) {
                  do some random-number calculations with x, y, and z
                }
  myResults <- replicate(10^6, myFunction(a, b, c))

```

`apply`
------

Here's an excerpt from the R help page for `apply`:

```

  Description:
  
       Returns a vector or array or list of values obtained by applying a
       function to margins of an array or matrix.
  
  Usage:
  
       apply(X, MARGIN, FUN, ...)

```

This should look familiar by now, *except* for the "MARGIN" business. `apply`
is built for working with matrices (or their higher-dimensional equivalents),
and the MARGIN argument tells `apply` that you want to apply the function FUN
to either the *rows* of the object (MARGIN = 1), or the *columns* of the
object (MARGIN = 2), and so on for higher dimensions.

Here are some examples:


```r

  myMat <- matrix(1:24, nrow=3)
  myMat

  apply(myMat, 1, sum)  ## calculate the sum of each row
  apply(myMat, 2, prod) ## calculate the product of each column

  ## look in BOTH dimensions to find odd-numbered values
  thatsOdd <- apply(myMat, c(1, 2), function(x) x %% 2)
  thatsOdd

```


`mapply`
-------

Here's an excerpt from the R help page for `mapply`:

```

  Description:
  
       ‘mapply’ is a multivariate version of ‘sapply’.  ‘mapply’ applies
       ‘FUN’ to the first elements of each ...  argument, the second
       elements, the third elements, and so on.  Arguments are recycled
       if necessary.
  
  Usage:
  
       mapply(FUN, ..., MoreArgs = NULL, SIMPLIFY = TRUE,
              USE.NAMES = TRUE)

```

Hmmm.  This all looks more or less familiar, but why does FUN now come at the
*beginning* of the argument list, instead of second, where it belongs?  The
answer is that there is no way for `mapply` to "know" how many arguments
you're going to give it.  That's where the `...` comes in: you stick in there
all the vectors (or whatever) you want to operate on.

Here's a simple example:


```r

  mapply(paste, letters[1:4], LETTERS[1:4], 1:4, MoreArgs=list(sep="//"))

```


Given that the `paste` function is vectorized to begin with, using `mapply` in
this context doesn't really "buy" us anything, but the example illustrates the
idea: grab the first item from `letters` and the first item from `LETTERS`,
and the first item from `1:4`, then feed all those to the function named in
the first argument (`paste`); then do the same for the second items, the third
items, etc.


`do.call` and its applications
==============================

The use of the function `do.call` is a somewhat specialized topic, but we use
the function extensively in this course, so it merits discussion here.

From the help page for `do.call`:

```

  Description:
  
       ‘do.call’ constructs and executes a function call from a name or a
       function and a list of arguments to be passed to it.
  
  Usage:
  
       do.call(what, args, quote = FALSE, envir = parent.frame())

```

If you think this sounds suspiciously similar to just calling a function,
you're correct.  Here's an example that demonstrates the equivalence:


```r

  myPowerFn <- function(x, n) {
      x^n
  }

  myPowerFn(2, 5)
  do.call(what=myPowerFn, list(2, 5))

```


The usefulness of `do.call()` stems from the fact that the second argument is
a `list`, which can be a `list` that you've computed or read in.  You don't
have to know the details in advance.

Here's a common scenario: you've got a bunch of data frames, all with
identical structure (but different values), and you'd like to "stack" them all
into one big data frame.  How could you do that?

We've seen above that the `rbind` function will do just that.  Here's a
reminder:


```r

  df1 <- data.frame(cbind(num=c(3, 1), book=c("hitchhiker", "guide")))
  df2 <- data.frame(cbind(num=c(4, 1), book=c("don't", "panic")))
  df1
  df2
  bigDF <- rbind(df1, df2)
  bigDF

```


This is all fine, but what if you had, say, 1000 individual data frames?  You
could type them all in to one very large `rbind` statement, but that would be
tedious and error-prone.  But what if you had a `list` of data frames?  Then
you could use `do.call` to process them:


```r


  df1 <- data.frame(cbind(num=c(3, 1), book=c("hitchhiker", "guide")))
  df2 <- data.frame(cbind(num=c(4, 1), book=c("don't", "panic")))

  dfList <- list(df1, df2)
  bigDF  <- do.call(rbind, dfList)
  bigDF

```


This doesn't seem to have bought us anything: in fact, there's slightly *more*
typing involved in the `do.call` approach.  But suppose that there were some
way to generate a list of data frames programmatically.  Then we could use our
program to generate lists that were arbitrarily long and still bind them
together using exactly the same, simple call to `do.call` as in the example
above.

But we've already seen something that generates a list: the `lapply` function.
Consider the following example:


```r

  xVals <- seq(-pi, pi, by=0.2)

  trigTable <- do.call(rbind,
                           lapply(xVals, function(x) {
                               data.frame(
                                   sinx=sin(x),
                                   cosx=cos(x),
                                   tanx=tan(x)
                               )
                           })
                      )
  trigTable

```


If you run the code above, you'll see that you get a nicely-formatted table of
selected values of the trig functions, and by *naming* the elements of the
data frame, you get a nice header for the table as well.  This formatting is
actually the motivation for introducing the `do.call` function at the point.

Note, by the way, that if, for instance, you decided you needed to have a
finer granularity in your result, you could change `by=0.2` to `by=0.1` (for
example) in the code above, then run the code, and get a larger, but still
nicely-formatted, table as a result, with *no other change in the code*.
 

String manipulation
===================

R has a number of functions that are useful for manipulating strings,
including, in particular, pattern matching with so-called *regular
expressions*.  We'll touch on these only briefly here and revisit them later,
as necessary.


```r

  #      paste(..., sep = " ", collapse = NULL)
  paste("abra", "cadabra", sep="!!!")

  #      substr(x, start, stop)
  substr("Popsicle", start=4, stop=7)

  #      substring(text, first, last = 1000000)
  substring("Popsicle", first=4, last=7)    ## older version of substr

  #      substr(x, start, stop) <- value
  oldSong <- "MagicalMysteryTour"
  substr(oldSong, 1, 7) <- "Musical"
  print(oldSong)

  #      substring(text, first, last = 1000000) <- value
  substring(oldSong, first=1, last=7) <- "Magical"
  print(oldSong)

  #      strsplit(x, split, fixed = FALSE, perl = FALSE, useBytes = FALSE)
  stringsTrebleClef <- "Every Good Boy Does Fine"
  stringsTrebleClef
  strsplit(stringsTrebleClef, split=" ")
  strsplit(stringsTrebleClef, split="o")

  #      nchar(x, type = "chars", allowNA = FALSE) # string length
  nchar("this string has thirty-nine characters ")

  #      tolower(x)
  tolower("BIG NOISE!")

  #      toupper(x)
  toupper("ucd")

  #      match(x, table, nomatch = NA_integer_, incomparables = NULL)
  match(4, c(3, 1, 4, 1, 5, 9, 2, 6, 5))
  match(c(3, 5, 9), c(3, 1, 4, 1, 5, 9, 2, 6, 5))

  #      x %in% table
  c(2, 4, 6) %in% c(1, 1, 2, 3, 5, 8, 13)

  #      pmatch(x, table, nomatch = NA_integer_, duplicates.ok = FALSE)
  pmatch("med", c("mean", "median", "mode")) # returns 2

  #     grep(pattern, x, ignore.case = FALSE, perl = FALSE, value = FALSE,
  #          fixed = FALSE, useBytes = FALSE, invert = FALSE)
  someText <- c("Let", "There", "Be", "Light")
  grep("e", someText)  ## all but the last entry
  grep("e", someText, value=TRUE)
  grep("Le", someText)
  grep("l", someText)  ## not found -- now lower-case 'l'
  grep("l", someText, ignore.case=TRUE) ## look for 'l' or 'L' 
  grep("[tT]", someText)  ## look for either 't' or 'T'
  grep("^[tT]", someText)  ## look for either 't' or 'T' at the START (^)
  grep("e$", someText, value=TRUE)  ## 'e' at the END ($)

  #     sub(pattern, replacement, x, ignore.case = FALSE, perl = FALSE,
  #         fixed = FALSE, useBytes = FALSE)
  sub("ere", "at", someText)
  sub("hate", "love", "I hate R")

  #     gsub(pattern, replacement, x, ignore.case = FALSE, perl = FALSE,
  #          fixed = FALSE, useBytes = FALSE)
  moreText <- "The address is 640 Oak Street, Apt. 2"
  sub ("\\d+", "NNN", moreText)  ## look for digits -- match the first
  gsub("\\d+", "NNN", moreText)  ## look for digits -- match all of them

  #     regexpr(pattern, text, ignore.case = FALSE, perl = FALSE,
  #             fixed = FALSE, useBytes = FALSE)
  regexpr ("\\d+", moreText) ## find locations, length of 1st digit substr
  gregexpr("\\d+", moreText) ## find locations, length of all digit substr


  
```


Pseudo-random numbers
=====================

Background and motivation
-------------------------

Much of the work in this course will involve generating "random samples" of
data.  Most of this work will be done on a computer, although it's possible to
use some physical process, such as flipping a coin, to get random samples.
As you can see, it would be tedious to obtain, say, a million random things
by flipping a coin a million times.  Computers can do the same task in
practically no time, and with more or less no work on your part.

Generation of random numbers
----------------------------

The concept of "randomness" is somewhat slippery.  In particular, the methods
used to generate random numbers on a computer rely on computer programs to
generate the random numbers.  But if you tell (program) a computer to run
through some given series of operations, the results by definition can't be
truly random.  Any time you run the same program, with the same initial
conditions, you get exactly the same output.

This topic is discussed in detail at:

    http://en.wikipedia.org/wiki/Random_number_generation

The thing that makes computer generation of "random" numbers useful, despite
the obvious non-randomness, is that it's possible to program a computer to
generate sequences of numbers that, when subjected to various mathematical
tests,  exhibit the properties expected of a truly random sequence of numbers.

This topic is discussed in detail at:

    http://en.wikipedia.org/wiki/Statistical_randomness

Random numbers in R
-------------------

R has many functions that explicitly or implicitly involve the use of its
random-number generator.  We've looked briefly at several examples of such
functions (`sample`, `runif`, `rnorm`).  Every such function will use and
modify the so-called `seed`, which represents the state of the random-number
generator.

It might be helpful to visual the output of the random-number generator as a
long, closed loop of string, with pieces of paper attached to the loop at
various points, and each piece of paper containing two numbers: the first
number is just a sequence number, identifying the piece of paper (1, 2, 3,
...); the second number is one of the sequence of random numbers.   (The
random numbers will always eventually loop back and start repeating
themselves.)

In this model, the `seed` is just the first number on the next piece of paper
to be read.  If the `seed` is 1, the next random number you'll get from
`sample`, etc., is the second number on the first piece of paper in the loop.
If the `seed` is 31415, the next random number you get will be the second
number on the piece of paper whose first number is 31415.

The following table represents schematically the first ten pairs of numbers in
our imaginary loop:

    seed | random.number
    -----|--------------
    1    |    5567940
    2    |    2047711
    3    |    8085826
    4    |     403246
    5    |     954011
    6    |    7003668
    7    |     697330
    8    |    7949082
    9    |    8542808
    10   |    6045173

Thus, if the `seed` is 7, the next random number you'll get is 697330, etc.
(The numbers are for purposes of illustration only: don't take them
literally.)

Note: the actual structure used by R to store the state of the random-number
generator is called `.Random.seed`, and it's much more complicated than just a
single integer, but we'll see that the single-integer model is sufficient for
our purposes.

Here's an example:


```r

  set.seed(42)  ## more or less arbitrary place to begin our calculations
  .Random.seed.save <- .Random.seed  ## save the full RNG state
  runif(1)  ## generate one random number (uniform distribution)
  all.equal(.Random.seed, .Random.seed.save) ## things have changed
  runif(1)  ## generate another one; different value this time
  runif(1)  ## ditto
  set.seed(42)  ## back to our starting point
  all.equal(.Random.seed, .Random.seed.save) ## really the same?  Yep.
  runif(1)  ## same as the first value we got

```


The idea here is that you first pick a number and feed it to `set.seed`.  The
actual number isn't important: it's important that you *know* what the seed
is.  Then your collaborators (or instructor or ...) can get your code **with**
the seed and produce exactly your same results.  If you send a collaborator
only your code and not the seed, he or she will almost certainly get numerical
results that are *different* from yours, and, hence, have no way to evaluate
the results.

Plotting
========

Background
----------

R has extensive facilities for making plots, graphs, charts, etc., on a wide
variety of graphic devices, including the standard displays on linux,
Macintosh, and Windows, as well as PDF, PNG, JPEG, etc.

R currently has many packages devoted to graphics, including, for example,
`lattice`, `grid`, `ggplot2`, etc.  We'll restrict our attention to the
so-called "base graphics", the set of graphics tools that comes with R by
default.

You can type:

```

  demo(graphics)

```

in the R console (i.e., at the `> ` prompt) to get a quick overview of R's
graphics capabilities.

The following web site has some very clear demonstrations of R's base
graphics:

    http://www.harding.edu/fmccown/r/

We'll have more to say about the base graphics system below.

The Murrell book
----------------

The "bible" on R graphics is this book by Paul Murrell:

    http://www.amazon.com/Graphics-Second-Edition-Chapman-Series/dp/1439831769

This book contains a good deal of material that, while useful, is beyond the
scope of the graphics we'll use in this course.  Nevertheless, the book is an
excellent reference, and you should be aware of it if you plan to make serious
use of R graphics.

The following discussion is optional.  Feel free to jump ahead to the next
section, where we begin our discussion of R graphics functions.

You can browse the figures in the book at:

    https://www.stat.auckland.ac.nz/~paul/RG2e/

At that site you can view the figures and the associated R code for the
figures, although this is a little tedious.

Fortunately for the R community, Paul has made much of the material in his
book available as an R package, and it's worthwhile to study the material in
the package.

To study the package, you first have to install it, which you can do in a
couple of ways:

  1. At the "> " prompt in the R console (the pane on the lower left in
     RStudio) type:
         install.packages("RGraphics")

  2. Select the `Packages` tab in the pane on the lower right in RStudio, then
     select "Install Packages".  Type:
         RGraphics
     into the "Packages" box in the window that pops up and click `Install`

Once you have the package installed, go to the R console and type:

```

  library(RGraphics)
  ls("package:RGraphics")

```

You should see a listing of the stuff in the package.  Here are the first few
lines:

```

  > ls("package:RGraphics")
    [1] "faceA"          "faceB"          "faceC"          "faceD"         
    [5] "faceE"          "figure1.1"      "figure1.10"     "figure1.11"    
    [9] "figure1.12"     "figure1.13"     "figure1.14"     "figure1.2"     
   [13] "figure1.3"      "figure1.4"      "figure1.5"      "figure1.6"
   .
   .
   .

```

You use the items in the package as follows.  Suppose, for instance, that you
see Figure 1.3 either in the book or at Murrell's web site and decide it would
be worth investigating.

At the prompt in the R console type:

```

  figure1.3()  ## to run the R code and draw the picture
  figure1.3    ## to see the R code used to draw the picture

```

The same technique works for all the figures in the book/package.


`plot` and related functions
----------------------------

We'll now begin our actual study of R's base graphics.

The most-important function to use for plotting is, surprisingly, `plot`.  The
basic syntax is as follows:

```
  plot(x, y) ## plot the object "y" as a function of the object "x"
  plot(y ~ x)  ## the same, expressed in "formula notation"

```

Note that `x` and `y` have to be of the same length.

Here are some actual examples:


```r

    ## generate some (arbitrary) data and make a simple plot
  xVals <- seq(from=(-2*pi), to=(2*pi), by=0.2)
  plot(xVals, sin(xVals))

    ## generate some dependent (on xVals) data and make a simple plot
  yVals <- xVals + rnorm(length(xVals), mean=0, sd=1.0)
  plot(xVals, yVals)

    ## add some color to the plot
  plot(xVals, yVals, col="blue")

    ## change the color and use a different plotting character
  plot(xVals, yVals, col="green", pch=17)

    ## ditto, but also compute the limits for the x axis
  plot(xVals, yVals, col="magenta", pch=3,
                     xlim=c(min(xVals)-0.5, max(xVals) + 0.5))

    ## compute limits for both axes
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlim=c(min(xVals)-0.5, max(xVals)+0.5),
                     ylim=c(min(yVals)-0.5, max(yVals)+0.5))

    ## ditto, but also put labels on the x and y axes
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlim=c(min(xVals)-0.5, max(xVals)+0.5),
                     ylim=c(min(yVals)-0.5, max(yVals)+0.5),
                     xlab="Fortnights", ylab="Furlongs")

    ## add a main title for the plot
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlim=c(min(xVals)-0.5, max(xVals)+0.5),
                     ylim=c(min(yVals)-0.5, max(yVals)+0.5),
                     xlab="Fortnights", ylab="Furlongs",
                     main="Plot of Furlongs per Fortnight")

    ## add some color to the main title (and go back to default axes)
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlab="Fortnights", ylab="Furlongs",
                     col.lab="forestgreen",
                     main="Plot of Furlongs per Fortnight",
                     col.main="red")

    ## change label colors; magnify labels (cex.lab) and title (cex.main)
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlab="Fortnights", ylab="Furlongs",
                     col.lab="forestgreen", cex.lab=1.5,
                     main="Plot of Furlongs per Fortnight",
                     col.main="red", cex.main=2)

    ## same, but squeeze labels a little closer to axes (mgp)
  plot(xVals, yVals, col="darkblue", pch=20,
                     xlab="Fortnights", ylab="Furlongs",
                     mgp=c(2.5, 1, 0),
                     col.lab="forestgreen", cex.lab=1.5,
                     main="Plot of Furlongs per Fortnight",
                     col.main="red", cex.main=2)

    ## some "decorations" for the last plot
    ## "pos=4" puts text to the right of the (x, y) point
  text(x=2, y=-4, labels="Some added text", col="orange", pos=4)

    ## another decoration: rotated text (srt)
  text(x=2, y=-3, labels="Some rotated text", col="blue", srt=30, pos=4)

    ## decoration: math stuff.  How geek-cool is that?
  text(x=0, y=-5, labels=expression(integral(f(x) * dx, 0, pi)))

    ## more decoration: add a line to the plot
    ## details of the "zzz" stuff are unimportant.  We're just trying
    ## to get some intercept and slope so we can draw a line
  zzz <- lm(yVals ~ xVals)
  zzz.intercept <- zzz$coefficients["(Intercept)"]
  zzz.slope <- zzz$coefficients["xVals"]
    ## here's the important part: drawing a line
  abline(a=zzz.intercept, b=zzz.slope, col="red")

    ## we have two things plotted.  Add a legend to show which is which
  legend(x=-6, y=5, legend=c("Original data", "Fitted line"),
         col=c("darkblue", "red"), pch=c(20, 32), lty=c(0, 1))

```


Graphics parameters.  The `par()` function
------------------------------------------

R has an intimidating array of graphical parameters, some of which we've used
in the examples above.  You can view the help page for the `par` function to
see the details:

```

  ?par

```

You can view and set graphical parameters using the `par` function.  In many
cases, the default values for the parameters work just fine.  But you might,
for instance, need to make a series of plots and decide that you need to have
thicker lines and bigger characters in *all* those plots.  Instead of
specifying the associated parameters in every call to `plot`, etc., you can
set them once with `par`.  Here's an example.  Note that you *might* have to
resize the graphics pane in RStudio to see the first plot.  (You'll get
complaints about the margin and no picture if there isn't enough room.)


```r

  pars.save <- par(lwd=3.5, cex=2)  ## save old params, set new ones
  plot(1:3, 1:3, type="l")

    ## make the rest of your plots with the modified parameters
    ## after that, bring back the original settings
  par(pars.save)  ## restore the saved parameters
  plot(1:3, 1:3, type="l")  ## back to thinner lines, smaller characters

```


Here's a list of some commonly-used graphics parameters:

### Colors

| Param       |  Description [default value]                            |
|-------------|---------------------------------------------------------|
| col         | The default plotting color                              |
| col.axis    | The color to be used for axis annotation [black]        |
| col.lab     | The color to be used for x and y labels [black]         |
| col.main    | The color to be used for plot main titles [black]       |
| col.sub     | The color to be used for plot sub-titles [black]        |
| fg          | The color to be used for the foreground of plots        |
| bg          | The color to be used for the background of device region|

### Font

| Param     |  Description [default value]                       |
|-----------|----------------------------------------------------|
|font       | An integer which specifies the font to use for text|
|font.axis  | The font to be used for axis annotation            |
|font.lab   | The font to be used for x and y labels             |
|font.main  | The font to be used for plot main titles           |
|font.sub   | The font to be used for plot sub-titles            |

### Character expansion

| Param     |  Description [default value]                              |
|-----------|-----------------------------------------------------------|
|cex        | A numerical giving the magnification for text and symbols |
|cex.axis   | The magnification to be used for axis annotation          |
|cex.lab    | The magnification to be used for x and y labels           |
|cex.main   | The magnification to be used for plot main titles         |
|cex.sub    | The magnification to be used for plot sub-titles          |


### Plotting characters and lines

| Param     |  Description [default value]                               |
|-----------|------------------------------------------------------------|
| pch       | An integer or a single character to be used to plot points |
| lty       | The line type (0=blank, 1=solid, 2=dashed, etc.)           |
| lwd       | The line width, a *positive* number [1]                    |


### Margins

See:

    http://research.stowers-institute.org/efg/R/Graphics/Basics/mar-oma/index.htm

for an informative discussion of margins in R plots.

| Param     |  Description [default value]                                 |
|-----------|--------------------------------------------------------------|
| mar       | A numerical vector of the form `c(bottom, left, top, right)` |
|           | which gives the number of lines of margin to be specified on |
|           | the four sides of the plot.  [`c(5, 4, 4, 2) + 0.1`]         |
| mai       | The same, but in inches, not lines                           |
| oma       | A vector of the form `c(bottom, left, top, right)` giving    |
|           | the size of the outer margins in lines of text.              |

### Layout

| Param     |  Description [default value]                                 |
|-----------|--------------------------------------------------------------|
| mfrow     | A vector of the form `c(nr, nc)`. The next nr*nc figures     |
|           | will be drawn (by rows) in an `nr`-by-`nc` array.            |
| mfcol     | The same, but drawn by columns, not by rows                  |

     
We'll see an example of the use of `mfrow` below.

More decorations
----------------

In the plotting examples above, we plotted some points (`yVals` vs. `xVals`)
and then "decorated" the plot with a line (and various text items).  It's also
possible to do this in reverse order: plot a line and decorate with points.
Here's an example:


```r

  xVals <- seq(from=1, to=10, by=0.1)
  yVals <- xVals^2
  plot(xVals, yVals, type='l', col="darkblue", lwd=2)

  noise <- rnorm(length(xVals), mean=2, sd=5)
  zVals <- yVals + noise
  points(xVals, zVals, col="red", pch=20)

```


Multiple plots on one display
-----------------------------

There are several ways in traditional R graphics to put multiple plots onto a
single display.  The most-common way is to set the graphics parameter `mfrow`
(or the essentially equivalent `mfcol`).

The following example uses the built-in `iris` data set to generate three
different data subsets and then makes a plot of Petal Length versus Petal
Width for each of the three subsets.  The plots all appear in one graphics
pane.  You can type the command:

```

  iris

```

in the R console to see the full data set.

The details of splitting the `iris` data set into three data frames are not
important at the moment.  All that matters is that we do have a list of data
frames and that we can set graphics parameters so as to plot them all in one
graphics pane.



```r

    ## some R voodoo to split the iris data set
  differentSpecies <- by(iris, iris$Species, `[`)
  needRows <- length(differentSpecies)  ## count the number of subsets

    ## set `mfrow` so that ALL plots will appear in one pane.
    ## tweak the margins (by trial and error) to get the spacing right
  par.save <- par(mfrow=c(needRows,1), mar=c(3.5, 4, 3.5, 2))

    ## iterate over the different species, generating one plot for each
  lapply(differentSpecies, function(nextSpecies) {

      plot(nextSpecies$Petal.Length, nextSpecies$Petal.Width,
           xlab="Petal Length", ylab="Petal Width",
           col="green", pch=20,
           col.lab="darkblue", cex.lab=1.5,
           mgp=c(2.5, 1, 0),
           main=nextSpecies$Species[1],
           col.main="red", cex.main=2.0)
    }
  )

    ## restore the previous graphics parameters
  par(par.save)

```



Multiple plots on multiple displays
-----------------------------------

In the example above we managed to squeeze all three of our `iris` plots into
one display.  To make things look reasonable we had to fiddle with the
margins.  But suppose there were, say, ten species of iris, and that we wanted
to have a look at some plots for all ten.  It's likely that no amount of
fiddling with the margins, etc., would let us squeeze all ten into the same
display.

One way around this problem is to open multiple displays.  Unfortunately, the
function used to open a new display depends on the system you're using (linux,
Macintosh, Windows).  Here's an example:


```r

  plot(rnorm(10))  ## generate some points and plot them
  X11()            ## open a NEW display on linux
  plot(rnorm(100)) ## plot some more points.  Should see BOTH plots now.

```


Here are the commands to open a new display on various systems:

```

  X11()      ## linux
  quartz()   ## Macintosh
  windows()  ## Microsoft Windows

```

Note that if you're using RStudio, the commands above will open a graphics
display *outside* the boundaries of the RStudio window.

Saving a plot to a file
-----------------------

If you create a plot interactively (i.e., so that it shows up in the graphics
pane in RStudio) and decide you'd like to keep that plot, you have a couple of
options for doing so.  You can print the contents of the current graphics
device to a printer or a file, using `dev.print()`.  In RStudio you can go to
the `Plots` tab in the pane on the lower right and select `Export` to do
essentially the same thing.  You would typically do this while you're doing
some exploration of some data.  After you've done all the exploring you need
to do, you can rerun your plotting code (in what you might call "production
mode") and specify in your code that you want the plot output to go to files.
Here are some examples.


```r

  plot(1:10, rnorm(10)) ## exploring -- generate some data and plot it
  dev.print(device=pdf, file="firstPlot.pdf")  ## looks good: save to file

    ## Now we know we want plots to go to files
  pdf(file="secondPlot.pdf", width=7, height=6) ## file name and geometry
  plot(1:20, rnorm(20))
  dev.off()  ## we won't see the file until we close the device

```


There are potentially many graphics devices available, depending on your
operating system and on the options used to compile R for that system.
Besides PDF, PNG is commonly used these days.  (Note that PDF uses so-called
"vector graphics", and PNG uses "bitmap graphics", meaning that the
parameters may be a little different for the two functions.  Look for these
terms on, say, Wikipedia for some background information.)  Type:

```

  ?Devices

```

to see a list of the graphics devices available on your system.

Plots for exploratory data analysis
-----------------------------------

There are some graphics functions in R that are commonly used to explore sets
of data, including `histogram()` and `boxplot)`.  Here are some details.

### Histogram

A histogram is a graphical tool that lets us examine the variability of a set
of data.  A very common use of histograms in an academic setting is to
determine the grades of students in a class: count all the students with final
scores between, say, 90 and 100 and give them a grade of `A`, then count all
the students with final scores between, say, 80 and 90 and give them a grade
of `B`, etc.

Here's an example.  The details of generating the numbers are not important.
There's more discussion below.


```r

  set.seed(42)  ## just to get repeatable results
  zzz <- rpois(100, c(3, 5, 7))  ## generate some data: details don't matter
  hist(zzz)  ## draw a histogram of the generated data

    ## sort out the data so we can compare the numbers to the picture
  sort(zzz)
  rz <- rle(sort(zzz))  ## rle counts how many numbers in a row
  data.frame(rz$values, rz$lengths)  ## display the numbers

```


You should see (from the data frame) that there are 19 (6 + 6 + 7) values less
than or equal to 2.  This is the height of the leftmost bar in the histogram.

Then there are 22 (9 + 13) values between 2 and 4. This is the height of the
bar in the histogram that is second to the left.

Then there are 29 (15 + 14) values between 4 and 6.  This is the height of the
third bar in the histogram.  Etc.

There are *numerous* options that you can supply to modify the appearance of a
histogram.  Type:

```

  ?hist

```

for details.

Here's a more-realistic example that also uses some of the additional options.
This example uses a data set that can be installed in R and that contains a
ton of data about major-league baseball in the United States.  (You don't have
to be a baseball fan for this.  The goal is the same as above: generate some
numbers and draw a picture.)

To follow the discussion you *do* have to install the "Lahman" package in R.
Type:

```

  install.packages("Lahman")

```

in the R console (or do the equivalent thing via the `Packages` tab in
RStudio).

You can get a sense of the what's in the Lahman package by typing:

```

  library(help=Lahman)

```

Here's the (somewhat lengthy) example:


```r

    ## Load the package with the baseball data
  library(Lahman)
    ## Get an overview of the "batting" portion
  names(Batting)
```

```
##  [1] "playerID"  "yearID"    "stint"     "teamID"    "lgID"     
##  [6] "G"         "G_batting" "AB"        "R"         "H"        
## [11] "X2B"       "X3B"       "HR"        "RBI"       "SB"       
## [16] "CS"        "BB"        "SO"        "IBB"       "HBP"      
## [21] "SH"        "SF"        "GIDP"      "G_old"
```

```r
  
    ## Look at data only back to 1990
  batRecentYears <- Batting[Batting$yearID >= 1990, ]
  summary(batRecentYears$yearID)  ## some useful attributes of the data
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1990    2000    2000    2000    2010    2010
```

```r
  
    ## Discard the columns that we don't need in this calculation
  batRecentYears <- batRecentYears[ , c("G_batting", "AB", "H")]
                                   
    ## remove lines with missing data (NA) and select only "starters",
    ## meaning anybody that's played about half the games
  starters <- batRecentYears[(!is.na(batRecentYears$G_batting)) &
                             (batRecentYears$G_batting >= 82), ]
  summary(starters)
```

```
##    G_batting         AB            H      
##  Min.   : 82   Min.   :  0   Min.   :  0  
##  1st Qu.:103   1st Qu.:317   1st Qu.: 82  
##  Median :126   Median :425   Median :114  
##  Mean   :125   Mean   :418   Mean   :115  
##  3rd Qu.:146   3rd Qu.:534   3rd Qu.:148  
##  Max.   :163   Max.   :716   Max.   :262
```

```r
  
    ## require that the player have some minimum number of hits, so as to
    ## avoid skewing the data (e.g., 3 at bats, 2 hits in a single year)
  hitters <- starters[starters$H > 50, ]
  
    ## clean up the data a little further.  Remove entries for which
    ## the "at bats" or "hits" is missing (i.e., the value is NA).
  hitters <- hitters[!(is.na(hitters$AB)), ]
  hitters <- hitters[!(is.na(hitters$H)), ]
  
  summary(hitters)
```

```
##    G_batting         AB            H      
##  Min.   : 82   Min.   :169   Min.   : 51  
##  1st Qu.:107   1st Qu.:337   1st Qu.: 88  
##  Median :130   Median :441   Median :119  
##  Mean   :127   Mean   :437   Mean   :120  
##  3rd Qu.:148   3rd Qu.:540   3rd Qu.:151  
##  Max.   :163   Max.   :716   Max.   :262
```

```r
  head(hitters)
```

```
##     G_batting  AB   H
## 97         89 244  68
## 113       101 345  86
## 114       120 420 107
## 115       109 320  81
## 116        94 252  69
## 119        96 286  78
```

```r
  
    ## compute batting average as hits/at-bats.  Force conversion from
    ## integer to double-precision (technically not necessary)
  battingAverages <- (as.numeric(hitters$H) / as.numeric(hitters$AB)) * 1000
  
  head(battingAverages)     ## look at the first few
```

```
## [1] 278.7 249.3 254.8 253.1 273.8 272.7
```

```r
  summary(battingAverages)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     159     252     272     273     292     394
```

```r
  length(battingAverages)   ## how many data points do we have?
```

```
## [1] 5997
```

```r
  
    ## calculate the mean and standard deviation of the final data
  meanBA <- mean(battingAverages)  ## sum them up, divide by no. of points
  meanBA
```

```
## [1] 272.6
```

```r
  
  sdBA <- sd(battingAverages)  ## measure the spread of the data
  sdBA
```

```
## [1] 29.1
```

```r
  
    ## draw a histogram of the data
    ##    prob=TRUE scales the y axis to [0, 1]
    ##    breaks tells how many bars to put in the histogram
  hist(battingAverages, prob=TRUE, breaks=20, col="lightblue")
  
    ## this could be a "normal" distribution.  Overlay the curve for
    ## the corresponding normal and check visually.  Note that by using
    ## "add=TRUE" we're using "curve" to decorate the previous plot
  curve(dnorm(x, mean=meanBA, sd=sdBA), add=TRUE, col="red", lwd=2)
```

![](figure/battingAverages.png) 

```r
  
```

  
Our preliminary conclusion, based on our visual inspection, is that our batting
averages follow a normal distribution.

It's important to note that visual appearance of a histogram depends on the
number of bins (breaks) used in the histogram.  Here's an example in which
histograms of the same data set look different with different breaks.


```r

par.save <- par(mfrow = c(2, 1), mar = c(2, 0, 1, 0))

hist(mtcars$hp)
hist(mtcars$hp, breaks = 30)

par(par.save)

```


In the second histogram of `mtcars$hp` there seem to be "holes" in the
distribution, and the peak seems to be shifted to the right, all with the same
underlying data.

Similarly, it's often important to set the range of the axes in order to make
meaningful comparisons.  If you run the code in the following chunk and
examine the resulting three histograms, you might erroneously conclude the the
`virginica` species typically has the shortest petals, while, in fact, the
opposite is true.



```r

    ## some R voodoo to split the iris data set
  differentSpecies <- by(iris, iris$Species, `[`)

    ## set `mfrow` so that ALL plots will appear in one pane.
    ## tweak the margins (by trial and error) to get the spacing right
  par.save <- par(mfrow=c(3,1), mar=c(3.5, 4, 3.0, 2))

    ## iterate over the different species, generating one histogram for each
  lapply(differentSpecies, function(nextSpecies) {

      hist(nextSpecies$Petal.Length,
           main=nextSpecies$Species[1],
           col.main="red",
           xlab="Petal Length",
           mgp=c(2.5, 1, 0))

    }
  )

    ## restore the previous graphics parameters
  par(par.save)

```


In the following code chunk we generate the same three, petal-length
histograms, but this time we set y axis to be a probability (thereby giving
the same maximum vertical range to all three histograms), and we explicitly
set the range of the x axis to be the same for all three histograms.


```r

    ## some R voodoo to split the iris data set
  differentSpecies <- by(iris, iris$Species, `[`)

    ## set `mfrow` so that ALL plots will appear in one pane.
    ## tweak the margins (by trial and error) to get the spacing right
  par.save <- par(mfrow=c(3,1), mar=c(3.5, 4, 3.0, 2))

    ## compute the "global" minimum and maximum of the petal length for
    ## the iris data set

    lengthMin <- min(iris$Petal.Length)
    lengthMax <- max(iris$Petal.Length)

    ## iterate over the different species, generating one histogram for each
  lapply(differentSpecies, function(nextSpecies) {

      hist(nextSpecies$Petal.Length,
           prob=TRUE,
           xlim=c(lengthMin - 0.5, lengthMax + 0.5),
           main=nextSpecies$Species[1],
           col.main="red",
           xlab="Petal Length",
           mgp=c(2.5, 1, 0))

    }
  )

    ## restore the previous graphics parameters
  par(par.save)

```



### Box plot

In the example above where we were "sanitizing" the baseball data, we made
repeated (and otherwise unexplained) use of the `summary` function to track
our progress through the data-cleanup process.

The `summary` function will accept an arbitrary object as its argument, but we
use it primarily to give us summaries of numerical objects, and in those cases
the `summary` function tells us:

  - the minimum value of the items contained in the object
  - the 1st quartile (25% of the values are less than this)
  - the 2nd quartile, or median (50% of the values are less than this)
  - the mean, or average, value of the items contained in the object
  - the 3rd quartile (75% of the values are less than this)
  - the maximum value of the items contained in the object

Here's a very simple example that illustrates the idea:


```r

summary(1:200)

```


(Note that the mean is not always equal to the median.  Send this:


```r

  summary(1/(1:10))

```


to R to see an example of that.)

The `boxplot` is essentially a graphical representation of the `summary`.
Here's a simple example:


```r

  set.seed(42)
  boxplot(rnorm(100, sd=2))

```

The example above generates 100 values from a normal distribution and then
creates a boxplot of the data.  The rectangle shows where the middle 50% of
the values lie.  The "whiskers", the short, horizontal lines near the top and
bottom of the plot, indicate a range of values where *most* of the values lie.
The circles near the bottom are "outliers", indicating values that are far
from the central value.

You can run the following, messy-looking code chunk to get a detailed picture
of the components of a `boxplot`.  The idea here is just to run the code and
study the resulting picture, rather than to focus on the details of producing
the picture.  Note that in RStudio the picture is best viewed with a maximized
graphics pane.  `IQR` stands for "inter-quartile range".


```r

  zNum <- 250
  zMean <- 10
  zSD <- 2
  set.seed(1)
  
  zzz <- rnorm(zNum, zMean, zSD)
  boxplot(zzz)
  zSumm <- summary(zzz)
  
  zIQR <- zSumm["3rd Qu."] - zSumm["1st Qu."]
  zIQR
  
  zAdjUpper <- zSumm["3rd Qu."] + 1.5 * zIQR
  zAdjUpper
  
  zAdjLower <- zSumm["1st Qu."] - 1.5 * zIQR
  zAdjLower
  
  points(x=rep(1.5, 6), y=zSumm, col="darkorange", pch=16)
  text(x=1.45, y=zSumm["1st Qu."],
       label="Results from summary",
       pos=4,
       col="darkorange",
       cex=1.2,
       srt=90)
  
  text(x=1.25, y=zAdjLower+0.20,      label="1st data pt above Low Adj.", pos=3)
  text(x=1.25, y=zSumm["1st Qu."],    label="1st Qu.", pos=1)
  text(x=1.20, y=zSumm["Median"]-0.15,label="Median",  pos=4)
  text(x=1.20, y=zSumm["Mean"]+0.15,  label="Mean",    pos=4)
  text(x=1.25, y=zSumm["3rd Qu."],    label="3rd Qu.", pos=3)
  text(x=1.25, y=zAdjUpper,           label="Last data pt below Upper Adj.", pos=1)
  
  abline(h=zAdjUpper, col="blue")
  text(x=0.5, y=zAdjUpper-0.5, label="Upper adjacency", col="blue", pos=4)
  abline(h=zAdjLower, col="green")
  text(x=0.5, y=zAdjLower+0.5, label="Lower adjacency", col="green",pos=4)
  
  arrows(x0=0.75, y0=zSumm["1st Qu."],
         x1=0.75, y1=zSumm["3rd Qu."],
         code=3,
         col="red"
         )
  
  text(x=0.70, y=zSumm["Median"]+0.1, label="IQR", col="red", srt=90)
  
  arrows(x0=0.85, y0=zSumm["3rd Qu."],
         x1=0.85, y1=zAdjUpper,
         code=3,
         col="blue"
         )
  text(x=0.82, y=zSumm["3rd Qu."]+2.0, label="(1.5 * IQR)", col="blue", srt=90)
  
  arrows(x0=0.85, y0=zAdjLower,
         x1=0.85, zSumm["1st Qu."],
         code=3,
         col="green"
         )
  text(x=0.82, y=zSumm["1st Qu."]-2.0, label="(1.5 * IQR)", col="green", srt=90)
  
  text(x=1.1, y=zSumm["Min."], label="Outlier", col="purple", cex=1.2)
  
```

  
Note that boxplots *are* plots and can be "decorated" in all the usual ways
(see the code chunk above for numerous examples of that).

Here's a convenient feature of boxplots: if you boxplot a list with labels on
the entries of the list, `boxplot` will use the labels as labels for the plot:


```r

  set.seed(42)
  boxplot(list(baby=rnorm(10),
               mama=rnorm(100),
               papa=rnorm(1000)))

```


And a somewhat more-realistic example:


```r

  par(mfrow=c(1, 1))
    ## Pick off just the petal length from the three species of iris
  stuffToPlot <- lapply(differentSpecies, function(nextSpecies) {
                            nextSpecies$Petal.Length
                          })
  boxplot(stuffToPlot)

```


Even though it's convenient to send a list to `boxplot`, it's sometimes
convenient to view multiple, individual boxplots in the same display, just as
we did for histograms above.  (This allows more control over the colors,
spacing, etc., for instance.)

As with histograms, you have to have a consistent set of axes in order to
compare multiple boxplots.  Here's our histogram example, modified to show
boxplots:


```r

  differentSpecies <- by(iris, iris$Species, `[`)

    ## compute the "global" minimum and maximum of the petal length for
    ## the iris data set
  lengthMin <- min(iris$Petal.Length)
  lengthMax <- max(iris$Petal.Length)

  par.save <- par(mfrow=c(3, 1))

    ## the "invisible" is to suppress output from lapply
    ## we just want to see the plots, not the values returned by lapply
  invisible(lapply(differentSpecies, function(nextSpecies) {
                   boxplot(nextSpecies$Petal.Length,
                     horizontal=TRUE,
                     xlab="Petal Length",
                     ylim=c(lengthMin - 0.5, lengthMax + 0.5),
                     boxwex=1.5,
                     col.lab="darkblue", cex.lab=1.5,
                     main=nextSpecies$Species[1],
                     col.main="red", cex.main=2.0)
    }))

  par(par.save)

```


Some points worth mentioning about the example above:

  - We flipped the box plots on their sides ("horizontal=TRUE")
  - To set the scale of the rotated boxplots, we used *ylim*
  - But to label the axes ("Petal Length") we used *xlab*


Querying R objects
==================

Everything we use in R, including vectors, lists, and even functions,  is an
object.  What does that mean?  For our purposes we can think of an object as a
thing consisting of:

  - a location in the computer's memory
  - a name that's assigned to that location
  - a value that's associated with that location
  - some attributes associated with that location

It's often useful to be able to find out information about a given object.  In
the simplest case, we may be debugging our own programs and have forgotten
whether we made the variable ("object") `zzz` a vector or a list.

Or we might write a function that will accept different kinds of objects, and
we need to determine programmatically whether the thing our function just got
is a matrix or a data frame and dispatch to different sections of our code,
depending on the answer.

Here are some functions in R that will give us information about R objects:

  - `class`
  - `mode`
  - `storage.mode`
  - `typeof`
  - `attributes`

For *practical* purposes, the `str` function is probably all you'll ever need
to get basic information about a given object, but here are some simple
examples of "introspection" in R:


```r

  class(c(1, 3, 5))
  str  (c(1, 3, 5))

  class(iris)
  str  (iris)

  mode(rnorm(10))
  str (rnorm(10))

  storage.mode(rnorm(10))
  storage.mode(1:5)  ## note: integer
  storage.mode(c(1, 2, 3, 4, 5))  ## "the same" numbers, but double-precision

  zzz <- matrix(rbind(c(1, 3, 5),
                      c(4, 6, 8)
                     ),
                nrow=2)
  class(zzz)
  mode (zzz)
  typeof(zzz)
  str  (zzz)
  storage.mode(zzz)
  attributes(zzz)  ## number of rows, columns stored as attributes
  
  class(letters)
  mode (letters)
  str  (letters)
  typeof(letters)
  storage.mode(letters)

  class(TRUE)
  storage.mode(TRUE)

```


As you can see from the above, in most cases the `str` function gives us *at
least* as much information as the other functions.  (`str` doesn't report the
storage mode, but that's seldom of concern to us.)


We now turn to the other scenario mentioned above, in which you need to make
decisions about data types *in your program*.  Basically, the technique used
here is almost always to call a function with a name like:

```

  is.<something-or-other>()

```

of which there are *numerous* instances in R.  Here are some examples of
queries about the basic data types:


```r

  is.numeric(1:10)
  is.numeric(c("alpha", "beta", "gamma"))

  is.character(letters)
  is.character(3.14159)

  is.logical(FALSE)
  is.logical(1)

  is.na(NA)  # !!!!!!!!!!! use for removal of NAs:
  set.seed(42)
  x <- rnorm(10)  ## generate some data
  x
  x[x > 1] <- NA  ## mark the outlying values as unavailable
  x
  is.na(x)  ## TRUE for the ones we tossed out
  x[!is.na(x)]  ## look at the ones we kept

  is.infinite(-Inf)
  is.infinite(42)

  is.null(NULL)
  is.null("Mary Poppins")

```


It's also possible to make queries about composite data types:


```r
 
  is.vector(letters[1:3])
  zzz <- list('a', 'b', 'c')
  is.vector(zzz)  ## R "knows" that all elements are of same type
  is.list(zzz)

  is.array(array(1:12, c(2, 3, 2)))
  is.matrix(iris)  ## not all elements are of same type
  is.data.frame(iris)
  is.list(iris)  ## note that a data frame is a type of list
  is.function(mean)
  is.function('c') ## distinguish between the string 'c' and ...
  is.function(c)   ## ... the function of that name
  is.function(get('c'))  ## but "get" will map string to fn, if possible

```


As mentioned above, all of the query functions start with "is".  You can use
the `apropos` function with a "regular expression" to list them:


```r

  apropos("is")  ## ack! way too much stuff
  apropos("^is") ## '^' means STARTS WITH.  Still too much stuff
  apropos("^is.") ## no change!  '.' means match ANY character
  apropos("^is\\.")  ## the backslashes "escape" the meaning of '.'
  apropos("^is[.]")  ## the same.  both treat '.' as regular text

```


It's also possible to find out (and assign) the names of the components of
lists and the columns of data frames (each column is in fact a list):


```r

  names(mtcars)
  colnames(mtcars)
  rownames(mtcars)

  myList <- list(year=2013, team="Giants", status="bad")
  myList
  names(myList)

  newList <- list(2013, "A's", "good")
  newList
  names(newList) <- c("year", "team", "status")
  newList
  names(newList)

```


The working directory
=====================

R has the concept of *working directory*, that is, the place in your file
system where it currently looks to find files.

You can examine and set the current working directory (CWD) from the R
console:


```r

save.wd <- getwd()  ## gets (and saves) the current working directory
setwd("..")  ## sets the new CWD to the parent of the current CWD

list.files()  ## shows all files in the CWD
setwd(save.wd)  ## go back to the original place

```


Note that R uses the "dot" notation for directory shortcuts (this is common in
many operating systems and on the web):

  - a single period, '.', refers to the current directory
  - two consecutive periods, '..', refers to the parent of the current
    directory

Here's a fairly common scenario.  During a lengthy session in RStudio you load
a file that contains a line similar to:

```

  zTable <- read.csv("../data/foo.csv")

```

and you get a complicated error message that contains:

```

  cannot open file '../data/foo.csv': No such file or directory

```

But you *know* that the file `foo.csv` *is* there, as you copied it to your
computer before you started your current session.  The resolution to the
paradox is usually that the file *is* there, but it's not in the specified
location, **relative to your current working directory**.

The `read.csv()` above is telling R to:

  - go to the parent directory of the current working directory
  - find a subdirectory named `data` in that parent directory
  - go down into the `data` subdirectory and read the file `foo.csv`

If you start out in the wrong place, you won't find the `data` subdirectory.
Just change your working directory so that the file specification is
consistent and all should be well.  (Note that this is a good place to use the
`list.files()` command.)

Note that besides setting the working directory with `setdwd()` in the R
console, you can also set it in a couple of different ways in RStudio:

  - go to the `Session` menu at the top and select `Set Working Directory`
  - go to the `Files` tab in the pane in the lower right of the RStudio
    display, then select the `More` icon, then `Set As Working Directory`

One advantage of using `setwd()` is that it works in *all* R environments, not
just in RStudio.

Regular expressions
===================

General discussion
------------------

A "regular expression" (or "regex" or "regexp") is a sequence of characters
used to make a pattern for search and/or replace operations on strings (at
least that's how we'll use regular expressions).

If you've ever used the command line in Windows, Mac OS, or linux, you've
probably used some form of regular expression.  For instance:

```

  dir *.exe    ## Microsoft Windows: show names of all files ending in .exe
  ls foo*.txt  ## Mac OS or linux: all files starting w/ foo & ending in .txt

```

We usually think of the `*` in the above examples as a "wildcard", but it's a
simple form of regular expression.

We saw a couple of other, simple examples of regular expressions in the
discussion of the `apropos()` function above:

```

  ^    ## forces that pattern to match at the beginning of a string
  $    ## forces that pattern to match at the end of a string

```

Some basic syntax
-----------------

While the syntax of regular expressions is simpler than that of a full-blown
computer language (C++, for instance), it still takes some getting used to.
Here's a nice summary online:

    http://www.regular-expressions.info/reference.html

There is, as usual, a lot of useful discussion in the R help pages.  See, for
instance:


```r

  ?regexpr

```


Generally speaking, each of the characters:

```

  [\^$.|?*+()

```

has a special meaning in regular expressions.  All other characters just match
themselves.

### Escape sequences

What happens if you *have* to search for a dollar sign or a left parenthesis,
or any of the other special characters mentioned above?  That is, you want to
treat the special characters as ordinary characters, devoid of special
significance.

You *can* do that, of course, and the way you do it is to put a backslash in
front of the special character, as, for example:

```

  \$  ## a plain, old dollar sign, not the end of the string

```

We'll see an example of this below, after we discuss some of the functions in
R that *use* regular expressions.

There are also situations in which the backslash does more or less the
reverse: it can turn a plain, old character into something different.  For
instance:

```

  \t  ## means to look for a tab character (ASCII 0x09)
  \n  ## means to look for a newline character (ASCII 0x0A)
  \r  ## means to look for a carriage return (ASCII 0x0D)

```

("ASCII" refers to a set of numerical values that are used to represent
characters in a computer.  See, for instance:

     http://en.wikipedia.org/wiki/ASCII

for some discussion.)

Commonly-used pattern-matching functions
----------------------------------------

### grep

The `grep()` function is the workhorse tool for regular expressions.  Have a
look at:

    http://en.wikipedia.org/wiki/Grep

for some background and details.

Here's the template for `grep`:

```

  grep(pattern, x, ignore.case = FALSE, perl = FALSE, value = FALSE,
       fixed = FALSE, useBytes = FALSE, invert = FALSE)

```

And here's a simple example:


```r

  grep("end", c("blend", "nunca", "splendor", "jamas", "Endothermic"))
  grep("end", c("blend", "nunca", "splendor", "jamas", "Endothermic"),
        value=TRUE)
  grep("end", c("blend", "nunca", "splendor", "jamas", "Endothermic"),
        value=TRUE, ignore.case=TRUE)

```


The `perl` option enables/disables the use of Perl-compatible regular
expressions.  See:

    http://www.perl.org/

The Perl-compatible, regular-expression "engine" is more flexible than the
standard one in R, and many people prefer to use it by default.


### regexpr and gregexpr

The functions `regexpr()` and `gregexpr()` are also used to find patterns in
strings, but they report the results in a different way, compared to `grep`.

Here are the templates for `regexpr` and `gregexpr`:

```

  regexpr(pattern, text, ignore.case = FALSE, perl = FALSE,
          fixed = FALSE, useBytes = FALSE)

  gregexpr(pattern, text, ignore.case = FALSE, perl = FALSE,
           fixed = FALSE, useBytes = FALSE)
```

And here's an example:


```r

  textToSearch <- c("blend", "nunca", "splendor", "jamas", "Endothermic")
  regexpr("end", textToSearch)

```


And here's an example that illustrates the difference between the two:


```r

    ## finds match at posn. 2, length 3
  regexpr ("iss", "Mississippi")
    ## finds match at posns. 2, 5, both of length 3
  gregexpr("iss", "Mississippi")

```


### sub and gsub

You might think of `sub()` and `gsub()` as "find-and-replace" functions.

Here are the templates for `sub` and `gsub`:

```

  sub(pattern, replacement, x, ignore.case = FALSE, perl = FALSE,
      fixed = FALSE, useBytes = FALSE)
  
  gsub(pattern, replacement, x, ignore.case = FALSE, perl = FALSE,
       fixed = FALSE, useBytes = FALSE)

```

Here are some simple examples:


```r

    ## replace the first occurrence of iss with -Ole_Miss-
  sub ("iss", "-Ole_Miss-", "Mississippi")
    ## replace all occurrences of iss...
  gsub("iss", "-Ole_Miss-", "Mississippi")

```


### strsplit

We've seen examples of the use of `strsplit()` above.  It's used, as the name
implies, to split strings into pieces, chopping the string at the places
specified by the `split` argument.  Here's the template:

```

  strsplit(x, split, fixed = FALSE, perl = FALSE, useBytes = FALSE)

```

Here are some typical examples:


```r

    ## pick off each word; separator is a blank
  strsplit("These are some words in a sentence.", " ")
    ## pick off each character; separator is empty string
  strsplit("These are some words in a sentence.", "")

```



More-complicated examples
-------------------------

What was it that was so "simple" about the examples above?  Answer: in every
case, the pattern was a "literal", a bunch of characters for which we were
seeking an exact match ("iss" matched "iss", for instance).  We didn't use any
"wildcards", i.e., any of the special characters mentioned above, and we didn't
really demonstrate the power of regular expressions.  The point was just to
get familiar with some commonly-used functions.

Now we can proceed to *use* those functions to exhibit some of the
more-interesting properties of regular expressions.  Here are some examples:


```r

    ## the "." matches *any* character, so we get back the whole string
    ## note the "greedy" nature of this: one char would do for a match,
    ## but we get ALL of them!
  grep(".", c("This is a string", "and another"), value=TRUE)

    ## the "*" matches the preceding character zero or more times
  grep("colou*r", c("color", "colour", "kolor"))

    ## combine the previous two: match zero or more of *any* character
  stringToMatch <- "This is another string"
  nchar(stringToMatch)
    ## match starts at posn 1, carries on to length of string
  regexpr(".*", stringToMatch)

    ## the "+" matches the preceding character *one* or more times
  grep("colou+r", c("color", "colour", "kolor"))

    ## beware of greedy matching: we want to replace <P>, but...
  gsub("<.*>", "the paragraph token",
       "In HTML both <P> and <BR> generate new lines")

    ## the '^' anchors the match to the beginning of the string
  grep("^ear", c("I", "woke", "up", "early", "and", "what", "did", "I",
                 "hear", "?", "A", "BEAR", "!"),
       value=TRUE, ignore.case=TRUE)

    ## and '$' anchors to the end of the string
  grep("ear$", c("I", "woke", "up", "early", "and", "what", "did", "I",
                 "hear", "?", "A", "BEAR", "!"),
       value=TRUE, ignore.case=TRUE)

    ## what if we need to look for the literal version of a special
    ## character?  Here we look for a '?'
  grep("?", c("I", "woke", "up", "early", "and", "what", "did", "I",
                 "hear", "?", "A", "BEAR", "!"),
       value=TRUE, ignore.case=TRUE)

    ## that wasn't what we wanted!  Need to "escape" the special character '?'
  grep("\\?", c("I", "woke", "up", "early", "and", "what", "did", "I",
                "hear", "?", "A", "BEAR", "!"),
       value=TRUE)

```


Note that in the last example we had to "escape" the special character `?` so
that `grep` would interpret it as a plain, old question-mark character, and
*not* as one of the special characters used in regular expressions.  And we
had to use *two* backslashes to do that, because the R interpreter will read
and "consume" one of them prior to passing the pattern to the `grep` function.

Regular expressions with character classes
------------------------------------------

Up to this point we've been concerned with:

```

  - matching literal strings ("xyz", "1and2")
  - matching bunches of otherwise undefined characters ("*", "+")
  - matching either of the above at the beginning or end of a string ("^",
    "$")

```

We now want to sharpen our focus and look for bunches of specific characters
or classes of characters.  You can find a lot of discussion of this on the
help page for `regexp`:


```r

  ?regexp

```


We'll look at some examples of character classes.  Quoting from the `regexp`
help page:

    A character class is a list of characters enclosed between [ and ]
    which matches any single character in that list; unless the first
    character of the list is the caret ^, when it matches any character
    not in the list.

Here are some examples:


```r

    ## look for either 'b' or 'r' at the start of a string
  grep("^[br]at", c("bat", "cat", "rat"), value=TRUE)

    ## look for things *not* starting with 'b' or 'r'
    ## note that '^' has two different meanings here!
  grep("^[^br]at", c("bat", "cat", "rat"), value=TRUE)

    ## a hyphen indicates a range of characters. here, anything
    ## from 'm' to 't', inclusive
  grep("[m-t]ap", c("capitulate", "mapper", "nap", "tapdance", "zap"),
       value=TRUE)

    ## can combine ranges.  Look for hexadecimal numbers, only 0-9,
    ## a-f, or A-F, from start (^) to finish ($).  Note that "turkey"
    ## has an 'e', but it has non-hex characters as well
  grep("^[0-9a-fA-F]+$", c("123", "FF", "ab", "turkey", "trot"),
       value=TRUE)

```


### Predefined character classes

There are some classes of characters that are used so frequently in dealing
with regular expressions that the classes have been "built in" to some
versions of the regular-expression language.  Here are a few of them:

```

  [:alnum:]
  Alphanumeric characters: [:alpha:] and [:digit:].
  
  [:alpha:]
  Alphabetic characters: [:lower:] and [:upper:].
  
  [:digit:]    (aka \d and \D is a non-digit)
  Digits: 0 1 2 3 4 5 6 7 8 9.
  
  [:space:]    (aka \s and \S is a non-space)
  Space characters: tab, newline, vertical tab, form feed, carriage return,
  space and possibly other locale-dependent characters.


```

See the help page for `regexp` for a full discussion.  Here's an example:


```r

    ## look for at least one [0-9], zero or more space, at least one letter
  grep("[[:digit:]]+[[:space:]]*[[:alpha:]]+",
       c("42 alpha", "314x beta", "gamma 137"),
       value=TRUE)

```


### Repetition quantifiers

We can get even more specific about the match by requiring a character, or
character class, to be repeated a given number of times, or a given range of
times:

```

  {n}    ## preceding object must be repeated n times
  {n, m} ## repeated at least n times but not more than m times
  {n, }  ## repeated n or more times

```

Here's an example:


```r

    ## is your SSN on this list?  (Actual rules for SSN are complicated!)
  grep("^\\d{3}-\\d{2}-\\d{4}$",
       c("512-44-6251",
         "978,53,7567",
         "123-45-67898",
         "314-15-9265pi"),
       value=TRUE
      )

```


### Reusing the matched text

You can tell R to "remember" portions of a matched string  and reuse those
matched portions.  To do this you put parentheses "(...)" in the pattern
surrounding the things you want to remember.  Here's an example that came
originally from research done by a graduate student at UCD.  The task was to
extract numerical information from a URL (a "web address").


```r

  nextURL <- "http://purl.org/phylo/treebase/tree/Tr3212"
  nextNum <- as.numeric(gsub("^.*/Tr(\\d+)$", "\\1", nextURL))
  nextNum

```


Here's a narrative description of the matching process above:

```

  - start at the beginning of the string (^)
  - match any number of characters (.*) until you get to...
  - the literal string "/Tr", followed by...
  - at least one decimal digit (\\d+), which we're going to remember
    (signaled by the parentheses), followed by ...
  - the end of the string ($) (R will return the unmatched portion
    of the string, so here you want to get EVERYTHING out of the way,
    except the piece you're looking for.)

```

The return value from gsub is:

```

  \\1  the first (and, in this case, only) thing you remembered
         from the pattern

```

We convert the return value from gsub ("3212") into a numeric object for use
in later calculations.

### Logical OR

You can search for any of several alternatives by separating the alternatives
by a vertical bar, "|", in the pattern.  Here's an example:


```r

  lookStooge <- grep("[Ll]arry|[Mm]oe|[Cc]urly",
                     c("Fred", "Ethel", "Curly", "Rainman", "moe"),
                     value=TRUE)
  lookStooge

```


Debugging in R
==============

There are times when even the most-experienced programmer encounters seemingly
inexplicable behavior in his or her program.  One response to this situation
is to stare intently at the program code for long periods of time, in the
hopes of spotting the flaw in the program.  This is, perhaps, commendable at
some level, but it's often a waste of time, as our brains tend to make,
subconsciously, the same mistakes over and over if we ask them to do the same
tasks over and over.

Is there an alternative?  The answer is: yes, it's called "debugging".
Debugging a program consists essentially of somehow interrupting the
execution of a program at selected spots and examining the values of program
variables and other aspects of the computing environment.

The oldest and simplest way to do this is simply to embed `print` statements
at the relevant places in the code.  This can be tedious, and it does require
us to remember to remove the `print` statements once we've got things working.

The basic R package includes a number of functions to help us do this
debugging in a more-systematic way:

  - `traceback`
  - `debug`
  - `browser`
  - `trace`
  - `recover`

There is a reasonably-accessible discussion of debugging with these functions
at:

    https://github.com/DavisDaddy/sta032/blob/master/R-debug-tools.Rmd

Also note that, starting with version 0.98, RStudio will have a graphical
interface to most of these debugging tools.

A quick review: "control panels" for R
======================================

You can think of R as a sort of machine with a number of "control panels".

The interpreter: the main control panel
---------------------------------------

The part of R that reads commands and executes the corresponding functions is
the *interpreter*.

### The settings on the interpreter control panel

The settings for this control panel are:

  - the variables that are defined at any one moment
  - the values of those variables

### Reading out the settings on the interpreter control panel

You can examine the state of the interpreter in various ways:

  - ls()
  - print()

### Changing the settings on the interpreter control panel

You change the settings of the interpreter by using an assignment statement:

  - `zzz <- 42`

The `options` control panel
---------------------------

The `options()` function controls what you might call R's general settings.
You can type:


```r

  options()  ## to see the values of all options currently set
  ?options   ## to see a discussion of the many options
  options(digits=18)  ## to set to 18 the number of digits displayed in output
  options(width=120)  ## to make R use more of your screen real estate

```


The `par` control panel
-----------------------

The `par()` function can be used to set or query *graphical* parameters.

You can type:


```r

  par() ## to see the current values of graphical parameters
  ?par  ## to see a discussion a discussion of the graphics parameters
  par(mfrow=c(3, 2)) ## to put the next six plots into a 3-row, 2-col array

```


There are many examples above of other uses of `par`.

The random-number control panel
-------------------------------

The random-number "machinery" in R is activated by the `set.seed()` function
or by the use of any function in R that relates to random numbers (`rnorm`,
`dnorm`, `sample`, etc.), and it is *changed* by **any** subsequent use of
those functions.


```r

  .Random.seed  ## produces an error if no previous use of random numbers
  set.seed(42)  ## pick a starting point in the list of random numbers
  .Random.seed  ## LONG list of numbers used by R to keep track
  saved.seed <- .Random.seed  ## remember the current values
  zzz <- rnorm(10)  ## make one use of the random-number generator
  all.equal(saved.seed, .Random.seed)  ## will show we now have a new seed

```


