# Read: Class 11 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read11.md)

## 
- JupyterLab is a next-generation web-based user interface for Project Jupyter.
- JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner.
- JupyterLab also offers a unified model for viewing and handling data formats.
- JupyterLab understands many file formats (images, CSV, JSON, Markdown, PDF, Vega, Vega-Lite, etc.) and can also display rich kernel output in these formats. 
- use - and = to zoom in / out image.
- [] to rotate image to left / right.
- 0 to reset.
- Jupyter notebook is like spreadsheets or presentation, is new way to work with data and code seamlessly together.
- Jupyter has two modes:
  - 1 - command mode: when opens Jupyter  you are in command mode, designed to changing of framework of your notebook.
   - shortcuts: 
    - a - a: add cell above
    - b - b: add cell below
    - c - c: copy cell
    - d - v: paste cell
    - e - x: cut cell
    - f - d d: delete cell
    - g - z: undo
    - h - shift + z: redo
    - i - y: cell format:code
    - j - m: cell format:markdown
    - k - 00: restart kernal
    
  - 2 - Edit mode: when press on active cell you're in editting mode.
  
    - Heading: using "#" to "######", to add some heading from H1 to H6 respectively.
    - italics: using one asterisk "*" prefix and suffix the thing you want to make it italic.
    - Bold: using two asterisk "**" prefix and suffix the thing you want to make it Bold.
    - unorder list: using one hyphon "-" prefix and suffix the thing you want to make it unoreder list.
    - order list: using numbers  prefix the thing you want to make it oreder list.
 ---
 ## NumPy Tutorial: Data Analysis with Python:
 
  ###
  - NumPy is a commonly used Python data analysis package. By using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem, like scikit-learn, that use NumPy under the hood.
 - Operations using NumPy:
   - Mathematical and logical operations on arrays.
   - Fourier transforms and routines for shape manipulation.
   - Operations related to linear algebra. NumPy has in-built functions for linear algebra and random number generation.
 - packages like SciPy (Scientific Python) and Mat−plotlib (plotting library).
 -  to install NumPy: `pip install numpy`
 - To install NumPy, run the following command. `Python setup.py install`
    - To test whether NumPy module is properly installed, try to import it from Python prompt. `import numpy`
    - If it is not installed, the following error message will be displayed.

`Traceback (most recent call last): 
   File "<pyshell#0>", line 1, in <module> 
      import numpy 
ImportError: No module named 'numpy'`
  - Alternatively, NumPy package is imported using the following syntax − `import numpy as np`
  - an N-dimensional array type called ndarray. It describes the collection of items of the same type. Items in the collection can be accessed using a zero-based index.
  - an object of data-type object (called dtype).
  
|  Sr.No.|	Data Types & Description                                                       |
| ---    | ---                                                                             |
|    1   |	bool_                                                                          |   
|        |Boolean (True or False) stored as a byte                                         |
|    2   |	int_                                                                           |
|        |Default integer type (same as C long; normally either int64 or int32)            |
|    3   |	intc                                                                           |
|    3   |	intc                                                                           |
|        |Identical to C int (normally int32 or int64)                                     |
|    4   |	intp                                                                           |
|        |Integer used for indexing (same as C ssize_t; normally either int32 or int64)    |
|    5   |	int8                                                                           |
|        |Byte (-128 to 127)                                                               |
|    6   |	int16                                                                          |
|        |Integer (-32768 to 32767)                                                        |
|    7   |	int32                                                                          |
|        |Integer (-2147483648 to 2147483647)                                              |
|    8   |	int64                                                                          |
|        |Integer (-9223372036854775808 to 9223372036854775807)                            |
|    9   |	uint8                                                                          |
|        |Unsigned integer (0 to 255)                                                      |
|    10  |	uint16                                                                         |
|        |Unsigned integer (0 to 65535)                                                    |
|    11  |	uint32                                                                         |
|        |Unsigned integer (0 to 4294967295)                                               |
|    12  |	uint64                                                                         |
|        |Unsigned integer (0 to 18446744073709551615)                                     |
|    13  |	float_                                                                         |
|        |Shorthand for float64                                                            |
|    14  |	float16                                                                        |
|        |Half precision float: sign bit, 5 bits exponent, 10 bits mantissa                |
|    15  |	float32                                                                        |
|        |Single precision float: sign bit, 8 bits exponent, 23 bits mantissa              |
|    16  |	float64                                                                        |
|        |Double precision float: sign bit, 11 bits exponent, 52 bits mantissa             |
|    17  |	complex_                                                                       |
|        |Shorthand for complex128                                                         |
|    18  |	complex64                                                                      |
|        |Complex number, represented by two 32-bit floats (real and imaginary components) |
|    19  |	complex128                                                                     |
|        |Complex number, represented by two 64-bit floats (real and imaginary components) |

- Data Type Objects (dtype):
  - Type of data (integer, float or Python object) 
  - Size of data 
  - Byte order (little-endian or big-endian)
  - In case of structured type, the names of fields, data type of each field and part of the memory block taken by each field.
  - If data type is a subarray, its shape and data type
- A dtype object is constructed using the following syntax −`numpy.dtype(object, align, copy)`
  - Object − To be converted to data type object.
  - Align − If true, adds padding to the field to make it similar to C-struct.
  - Copy − Makes a new copy of dtype object. If false, the result is reference to builtin data type object
- Each built-in data type has a character code that uniquely identifies it.
  - 'b' − boolean
  - 'i' − (signed) integer
  - 'u' − unsigned integer
  - 'f' − floating-point
  - 'c' − complex-floating point
  - 'm' − timedelta
  - 'M' − datetime
  - 'O' − (Python) objects
  - 'S', 'a' − (byte-)string
  - 'U' − Unicode
  - 'V' − raw data (void)
