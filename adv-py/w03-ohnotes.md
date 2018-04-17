Topics for week 3
==================

Pandas
======
Purpose
-------
Pandas is a Python data analysis library. The name is derived from the term “panel data”, an econometrics term for multidimensional structured data sets. Get it with 

```
pip install pandas
```

Pandas can take data from a diverse range of sources, such as CSV, or a SQL database, and create a Python object called a data frame. A data frame has rows and columns, sort of equivalent to a spreadsheet (a bit of a disservice really), but with full Python programmability. 

Pandas dataframes are very easy to work with when dealing with data that needs to be analyzed, summarized and graphed. Given that such data normally comes from a wide variery of sources, the data itelf can sometimes be of variable quality. Pandas allows the data to be inspected, and then "cleansed", by removing outliers and handling missing or erroneous values, so that results of analysis are not skewed and can be trusted.

Use Pandas when you have potentially large amounts of data on which you want to do some exploratory analysis and where the data may not be clean.

Example
-------
Some very basic examples of how Pandas can be used...

Here is our file:

```
Department,Employee #,Salary,Cost,Income,Years service
Rental,10907," 126,604.71 "," 151,925.66 "," 18,692.25 ", 4.94
Sales,11978," 272,699.95 "," 327,239.94 "," 193,232.76 ", 18.45
Sales,10427," 86,620.43 "," 103,944.51 "," 99,144.36 ", 5.63
Sales,12078," 109,074.10 "," 130,888.92 "," 174,712.37 ", 16.13
Rental,11925," 62,520.65 "," 75,024.77 "," 216,071.33 ", 17.48
Rental,11892," 269,198.63 "," 323,038.36 "," 273,424.46 ", 6.84
Sales,10528," 264,465.04 "," 317,358.05 "," 396,396.59 ", 18.83
Rental,10527," 286,528.79 "," 343,834.55 "," 83,014.67 ", 18.28
Sales,11577," 37,080.84 "," 44,497.01 "," 223,341.01 ", 4.49
```

Let's read the file...

```
>>> import pandas as pd
>>> data = pd.read_csv("emps.csv")
>>> data.head()
```
```
  Department  Employee #        Salary          Cost        Income  \
0     Rental       10907   126,604.71    151,925.66     18,692.25    
1      Sales       11978   272,699.95    327,239.94    193,232.76    
2      Sales       10427    86,620.43    103,944.51     99,144.36    
3      Sales       12078   109,074.10    130,888.92    174,712.37    
4     Rental       11925    62,520.65     75,024.77    216,071.33    

   Years service  
0           4.94  
1          18.45  
2           5.63  
3          16.13  
4          17.48  
```

Just look at salaries and income...

```
>>> subset = data[["Employee #", "Salary", "Income"]]
>>> subset.head()
```
```
   Employee #        Salary        Income
0       10907   126,604.71     18,692.25 
1       11978   272,699.95    193,232.76 
2       10427    86,620.43     99,144.36 
3       12078   109,074.10    174,712.37 
4       11925    62,520.65    216,071.33 
```

And sort it....
```
>>> sorted = subset.sort_values(by=["Salary"])
>>> sorted.head()
```
```
   Employee #        Salary        Income
3       12078   109,074.10    174,712.37 
0       10907   126,604.71     18,692.25 
6       10528   264,465.04    396,396.59 
5       11892   269,198.63    273,424.46 
1       11978   272,699.95    193,232.76 
```

Back to the entire data set, group and sum...
```
>>> data.groupby(["Department"]).sum()
```
```
   Employee #  Years service
Department                           
Rental           45251          47.54
Sales            56588          63.53
```

External sources:
-----------------
* https://towardsdatascience.com/a-quick-introduction-to-the-pandas-python-library-f1b678f34673
* https://pandas.pydata.org/pandas-docs/stable/10min.html
* https://pandas.pydata.org/pandas-docs/stable/overview.html


Easy guide to using git
=======================

* https://www.elegantthemes.com/blog/resources/git-and-github-a-beginners-guide-for-complete-newbies
* http://anitacheng.com/git-for-non-developers


Closures
========
Purpose
-------
Closures fulfill these purposes:
* replacing hardcoded constants
* a simple way to implement information hiding (https://en.wikipedia.org/wiki/Information_hiding) in programs that don't justify a full object oriented approach
* reduce the use of global variables

Closures in many ways are like functions, but closures preserve their internal state between calls (hence redution in global variable use). Closures also "hide" their internal state, preventing clients from accessing that internal state directly.

A closure is created using the following approach:
* A function is created inside another function (in other words, we have a nested function).
* The function that is enclosed (nested) needs to reference variables that are defined in the function in which it is enclosed).
* And finally, the enclosing function returns the nested function.

Example: a closure
------------------
```
def make_addings():
    results = []
    for i in range(10):
        def add(x, i=i):
            return i + x
        results.append(add)
    return results


for add in make_addings():
    print(add(3))
```
And another (making functions):
```
def make_multiplier(factor):
    def multiply(number):
        return number * factor
    return multiply

multiply9 = make_multiplier(9)

print(multiply9(8))
```

External sources
----------------
* https://www.geeksforgeeks.org/python-closures/
* https://www.codevoila.com/post/51/python-tutorial-python-function-and-python-closure

Currying
========
Purpose
-------
Currying allows you to make new, specialized versions of an existing, multi-parameter function by pre-setting some of those parameters. Thus, you create more specialized functions from more general ones.

Currying allows little pieces of functionality to be setup and reused with ease, without clutter;

Example
-------
Uncurried:
```
def func(x, y):
  return 2 * x + y
```
Curried:
```
def func2(x):
  def inner(y):
    return 2 * (x + y)
  return inner

print(func2(7)(3))
```

External sources
----------------
* https://unpythonic.com/01_05_currying/
* https://mtomassoli.wordpress.com/2012/03/18/currying-in-python/
* https://hackernoon.com/ingredients-of-effective-functional-javascript-closures-partial-application-and-currying-66afe055102a

Itertools
=========
Purpose
-------
Itertools provides a set of memory efficient but fast tools, that can be used to provide comprehnsive looping features in pure Python. Examples include counting, repatition and grouping.

Example
-------
chain:
```
import itertools
for i in itertools.chain('ABC', 'DEF'):
    print(i)
```
count:
```
from itertools import *
for i in islice(count(), 5, 10):
    print(i)
```
permutations:
```
from itertools import *
for i in permutations("ABC"):
    print(i)
```

External sources
----------------
* https://medium.com/@mr_rigden/a-guide-to-python-itertools-82e5a306cdf8
* https://docs.python.org/3.1/library/itertools.html

