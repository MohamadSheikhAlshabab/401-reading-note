# Readings: Game of Greed 2  [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read07.md)

- The Python scope concept is generally presented using a rule known as the LEGB rule. stand for Local, Enclosing, Global, and Built-in scopes.
-------------
## Understanding Scope:

 1- Global scope: The names that you define in this scope are available to all your code.
 2- Local scope: The names that you define in this scope are only available or visible to the code within the scope.
 -------------
 ## Names and Scopes in Python:
 
 
|Operation	         |Statement                                                          |
|---------           |----------                                                         |
|Assignments	       |x = value                                                          |
|Import operations	 |import module or from module import name                           |
|Function definitions|	def my_func(): ...                                               |
|Argument definitions| in the context of functions	def my_func(arg1, arg2,... argN): ...|
|Class definitions   |	class MyClass: ...                                               |

----------------
## Python Scope vs Namespace:

- These dictionaries are commonly called namespaces.
- These are the concrete mechanisms that Python uses to store names.
- They’re stored in a special attribute called .__dict__.
-------------
- you can reference ps1 in at least two different ways:

 1 - Using the dot notation on the module’s name in the form module.name
 2 - Using a subscription operation on .__dict__ in the form module.__dict__['name']
 ----------------
 ## Using the LEGB Rule for Python Scope:
 1 - Local (or function) scope: is the code block or body of any Python function or lambda expression. This Python scope contains the names that you define inside the function.
 2 - Enclosing (or nonlocal) scope:  is a special scope that only exists for nested functions.
 If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function.
 3 - Global (or module) scope: is the top-most scope in a Python program, script, or module.
 4 - Built-in scope:  is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. 
 
 ------------
 ## Big O notation: 
 - __Big O__: it's measuring how an algorithm will respond to an increasing amount of data that it has to process.
 - Time complexity: it measure of how long an algorithm tkaes to do something in its the most basic level.
 - Space comlexity: it is how much memory it takes up whilst it's doing it, how many of computer's resources is it allocating to itself in order to do what you asked of it.
 - The worst case scenario: the length of time without that algorithm going to take to give you the information that you need.
 
 -----------
 ## Computational complexity:
 - O(1): constant running time.
 - O(log n): logarithmic running time.
 - O(n): linear running time.
 - O(n log n): log-linear running time.
 - O(n^k): polynomial running time.
 - O(c^n): exponential running time.
 
 ------------
 - Constant complexity it's doesn't go up as the number of the number of the time it takes to process doesn't go up as the number of inputs increases.
 - Linear complexity the time to process goes up linearly with the number of inputs.
 - Quadratic comlexity it goes up as the square of the number of inputs.
