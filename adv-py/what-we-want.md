# List of topics for open house #3

Could you go over this bit of code I found at Wikipedia which uses functools.reduce - [Function Composition](https://en.wikipedia.org/wiki/Function_composition_(computer_science))? I'm having a hard time parsing it for some reason.
Also, would you consider it good or bad code? Can it be made clearer, or is it obvious (and I just need more practice)?

```
# In Python, a way to define the composition for any group of functions, is using reduce 
# function (use functools.reduce in Python 3):

try:
    reduce
except NameError:  # Python 3
    from functools import reduce

def compose(*funcs):
    """ Compose a group of functions (f(g(h(...)))) into a single composite func. """
    return reduce(lambda f, g: lambda *args, **kwargs: f(g(*args, **kwargs)), funcs)

# Example
f = lambda x: x+1
g = lambda x: x*2
h = lambda x: x-3

# Call the function x=10 : ((x-3)*2)+1 = 15
print(compose(f, g, h)(10))

'''
Docstring:
reduce(function, sequence[, initial]) -> value

Apply a function of two arguments cumulatively to the items of a sequence,
from left to right, so as to reduce the sequence to a single value.
For example, reduce(lambda x, y: x+y, [1, 2, 3, 4, 5]) calculates ((((1+2)+3)+4)+5).
If initial is present, it is placed before the items of the sequence in the calculation,
and serves as a default when the sequence is empty.
'''
```
