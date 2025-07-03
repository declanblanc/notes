I'm learning a lot of [Python](Python.md) right now thanks to my work project and though I'd seen these quirky function parameters around before I had never needed to pay them all too much mind. My coursework in school didn't include a Python course thanks to me testing out of taking CS100 at NJIT so my Python knowledge is minimal *at best*. This internship has been the best way to learn, trial by fire :)

Anyway, \*args and \*\*kwargs are quite interesting. They allow you to pass an indeterminate amount of arguments to a function. 

To demonstrate the use of \*args, I can write a simple `add` function with the unique property that accepts any number of parameters

```python title:add(*args)
def add(*args):
	sum = 0
	for num in args:
		sum += num
	print(sum)


add(2,3) # prints 5
add(2,3,4,5,6) # prints 20
```

> 💡
> Both \*args and \*\*kwargs can be named whatever you'd like them to be when declaring the function that accepts them. The important detail is the number of asterisks preceding the parameter

It's pretty neat! And the fun continues with \*\*kwargs. Similar to \*args, kwargs allows you to pass as many arguments as you'd like to a function, with the added benefit of the arguments being passed as key-value pairs

```python title:personal_info(**kwargs)
def personal_info(**kwargs):
	for key, value in kwargs.items():
		print(f"{key} = {value}")

personal_info(name="Declan", age=26, nerd=True)
"""
prints:
name = Declan
age = 26
nerd = True
"""

personal_info(name="You", age=42, nerd="Definitely")
"""
prints:
name = You
age = 42
nerd = Definitely
"""
```

If ya ask me this is pretty exciting stuff!