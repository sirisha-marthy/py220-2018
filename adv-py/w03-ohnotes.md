Topics for week 3
==================

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
* a simple way to implement infomration hiding (https://en.wikipedia.org/wiki/Information_hiding) in programs that don't justify a full object oriented approach
* reduce the use of global variables

Closures in many ways like functions, but closures preserve their internal state between calls (hence recution in global variable use). Closures also "hide" their internal state, preventing clients from accessing that internal state directly.

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
Currying allows you to make new, specialized versions of an existing multi-parameter function by pre-setting some of those parameters. Thus, you create more specialized functions from more general ones.

Currying allows 

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

Itertools
=========



