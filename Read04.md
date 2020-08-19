## Classes & objects:

- objects : are encapsulation variables and functions into a single entity.and get their variables and function from classes.
- calsses : are a template to create own objects.
- You can create multiple different objects that are of the same class, However, each object contains independent copies of the variables defined in the class. 
- acessing to variabel: class.variable
- acessing to function: class.function()



## Recursive Functions in Python:
- A recursive function is a function defined in terms of itself via self-referential expressions.
- This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result. 
  1- Decompose the original problem into simpler instances of the same problem. 
  2- As the large problem is broken down into successively less complex ones, those subproblems must eventually become so simple that they can be solved without further subdivision
- Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case. 
![img](https://files.realpython.com/media/stack.9c4ba62929cf.gif)
- Maintaining State:
  1 - Thread the state through each recursive call so that the current state is part of the current call’s execution context
  2 - Keep the state in global scope
![img](https://files.realpython.com/media/state_3.3e8a68c4fde5.png)

## Recursive Data Structures in Python:
- A data structure is recursive if it can be deﬁned in terms of a smaller version of itself.
- A list is an example of a recursive data structure.
![img](https://files.realpython.com/media/list.3df62a89243d.gif)

## pytest fixtures: explicit, modular, scalable:

- capfd: Capture, as text, output to file descriptors 1 and 2.

- capfdbinary: Capture, as bytes, output to file descriptors 1 and 2.

- caplog: Control logging and access log entries.

- capsys: Capture, as text, output to sys.stdout and sys.stderr.

- capsysbinary: Capture, as bytes, output to sys.stdout and sys.stderr.

- cache: Store and retrieve values across pytest runs.

- doctest_namespace: Provide a dict injected into the docstests namespace.

- monkeypatch: Temporarily modify classes, functions, dictionaries, os.environ, and other objects.

- pytestconfig: Access to configuration values, pluginmanager and plugin hooks.

- record_property: Add extra properties to the test.

- record_testsuite_property: Add extra properties to the test suite.

- recwarn: Record warnings emitted by test functions.

- request: Provide information on the executing test function.

- testdir: Provide a temporary test directory to aid in running, and testing, pytest plugins.

- tmp_path: Provide a pathlib.Path object to a temporary directory which is unique to each test function.

- tmp_path_factory: Make session-scoped temporary directories and return pathlib.Path objects.

- tmpdir: Provide a py.path.local object to a temporary directory which is unique to each test function; replaced by tmp_path.

- tmpdir_factory: Make session-scoped temporary directories and return py.path.local objects; replaced by tmp_path_factory.
