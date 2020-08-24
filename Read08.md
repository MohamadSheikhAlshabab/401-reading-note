# Readings: Game of Greed 3 [url](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read08.md)

## List Comprehensions in Python:
 - It consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses.
 - The expressions can be anything, meaning you can put in all kinds of objects in lists.
 <pre>new_list = []
for i in old_list:
    if filter(i):
        new_list.append(expressions(i))</pre>
- will become in list comprehensions:
<pre>new_list = [expression(i) for i in old_list if filter(i)]</pre>

- this syntax using square brackets :
<pre>[ expression for item in list if conditional ]</pre>
- is equalevent to :
<pre>for item in list:
    if conditional:
        expression</pre>
        
 ----------
 ## Primer on Python Decorators:
 
  -  a decorator is a function that takes another function and extends the behavior of the latter function without explicitly modifying it.
  - a function returns a value based on the given arguments.
  - functions are first-class objects. This means that functions can be passed around and used as arguments, just like any other object (string, int, float, list, and so on).
  - Inner Functions: It’s possible to define functions inside other functions. 
  - Returning Functions From Functions to use functions as return values.
  ----
 - Syntactic Sugar! 
   - use decorators in a simpler way with the @ symbol, sometimes called the “pie” syntax. 
  ----
  - Decorating Functions With Arguments:
    - use *args and **kwargs in the inner function. 
  --- 
  - Slowing Down Code:
    - The @slow_down decorator will sleep one second before it calls the decorated function.
  - Registering Plugins:
    - The @register decorator simply stores a reference to the decorated function in the global PLUGINS dict.
  - Nesting Decorators:
    - You can apply several decorators to a function by stacking them on top of each other.
  - Decorators With Arguments:
    - Sometimes, it’s useful to pass arguments to your decorators. 
  - Stateful Decorators:
    - Sometimes, it’s useful to have a decorator that can keep track of state.
  - Classes as Decorators:
    - For a class to be callable, you implement the special .__call__() method.
