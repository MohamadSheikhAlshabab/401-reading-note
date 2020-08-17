## Files :
- made up from three parts :                                         
  - 1 Header: metadata about the contents of the file.
  - 2 Data: Contains of file.
  - 3 End of file(EOF): special character indicates to the end of file.
                                                       
                                   
    <img src="https://files.realpython.com/media/FileFormat.02335d06829d.png">
    
 - File Paths: is a string indicates to the location of the file.
   - made up from three parts:
   - 1 Folder path: the location of the folder in the file system contents that file. 
   - 2 file path: the name of the file.
   - 3 extension: the end of file path with a period used to indicate the file type.
   
- > /
- > │
- > ├── path/
- > |   │
- > │   ├── to/
- > │   │   └── cats.gif
- > │   │
- > │   └── dog_breeds.txt
- > |
- > └── animals.csv

 
 - double-dot: used to traverse multiple directories above the current.
 - Line Endings:
   - ASA standard states that line endings should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n).
   - The ISO standard however allowed for either the CR+LF characters or just the LF character.
   -  > file in windows system :
   - > Pug\r\n
   - > Jack Russell Terrier\r\n
   - > English Springer Spaniel\r\n
   - > German Shepherd\r\n
   - > Staffordshire Bull Terrier\r\n
   - > Cavalier King Charles Spaniel\r\n
   - > Golden Retriever\r\n
   - > West Highland White Terrier\r\n
   - > Boxer\r\n
   - > Border Terrier\r\n
  
  - same file in Unix device:
  - > Pug\r
  - > \n
  - > Jack Russell Terrier\r
  - > \n
  - > English Springer Spaniel\r
  - > \n
  - > German Shepherd\r
  - > \n
  - > Staffordshire Bull Terrier\r
  - > \n
  - > Cavalier King Charles Spaniel\r
  - > \n
  - > Golden Retriever\r
  - > \n
  - > West Highland White Terrier\r
  - > \n
  - > Boxer\r
  - > \n
  - > Border Terrier\r
  - > \n
 
- Opening and Closing a File in Python: 
 - open: open() bulit-in function 
 - <code>file = open('dog_breeds.txt')</code>
 - to ensure to close the file safely, there are two ways:
 - 1 -  <code>reader = open('dog_breeds.txt')</code>
     - <code>try:</code>
     - <code> # Further file processing goes here</code>
     - <code>finally:</code>
     - <code>reader.close()</code>
    
  - 2 - <code>with open('dog_breeds.txt') as reader:</code>
      - <code> # Further file processing goes here</code>
      
  - 
| Character |	Meaning                                                    |
| ----------| -----------------------------------------------------------|
| 'r'     	| Open for reading (default)                                 |
| ----------| -----------------------------------------------------------|
| 'w'	      | Open for writing, truncating (overwriting) the file first  |
| ----------| -----------------------------------------------------------|
| 'rb'      | or 'wb'	Open in binary mode (read/write using byte data)   |
| ----------| -----------------------------------------------------------|

- Text File Types: 
   - > open('abc.txt')

   - > open('abc.txt', 'r')

   - > open('abc.txt', 'w')
   
 - Buffered Binary File Types:
    - > open('abc.txt', 'rb')

   - > open('abc.txt', 'wb')
   
 - Raw File Types :
  - > “generally used as a low-level building-block for binary and text streams.”
  - > open('abc.txt', 'rb', buffering=0)
- Reading and Writing Opened Files:


| Method             |	What It Does                                                                                                                              |
| --------           | --------------                                                                                                                             |
| .read(size=-1)	   | This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.|
| .readline(size=-1) |	This reads at most size number of characters from the line.                                                                               |
|                    |   This continues to the end of the line and then wraps back around.                                                                        |
|                    |   If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.                                    |
| .readlines()       |	This reads the remaining lines from the file object and returns them as a list.                                                           |

- Iterating Over Each Line in the File:
> - <code> with open('dog_breeds.txt', 'r') as reader:</code> 
> - <code>    # Read and print the entire file line by line</code> 
> - <code>    line = reader.readline()</code> 
> - <code>    while line != '':  # The EOF char is an empty string</code> 
> - <code>        print(line, end='')</code> 
> - <code>        line = reader.readline()</code>  
> -  Pug
> -  Jack Russell Terrier
> - English Springer Spaniel
> - German Shepherd
> -  Staffordshire Bull Terrier
> -  Cavalier King Charles Spaniel
> -  Golden Retriever
> - West Highland White Terrier
> - Boxer
> -  Border Terrier


- Working With Bytes:
<img src="https://files.realpython.com/media/jack_russell.92348cb14537.png">
| Value | 	Interpretation                                             |
| ----  | ---                                                          |
| 0x89	| A “magic” number to indicate that this is the start of a PNG |
| 0x50  | 0x4E 0x47	PNG in ASCII                                       |
| 0x0D  | 0x0A	A DOS style line ending \r\n                           |
| 0x1A	| A DOS style EOF character                                    |
| 0x0A	| A Unix style line ending \n                                  |

  - open the file and read these bytes individually
  >>> with open('jack_russell.png', 'rb') as byte_reader:
  >>>  -   print(byte_reader.read(1))
  >>>  -   print(byte_reader.read(3))
  >>>  -   print(byte_reader.read(2))
  >>>  -   print(byte_reader.read(1))
  >>>  -   print(byte_reader.read(1))
>  - b'\x89'
>  - b'PNG'
>  - b'\r\n'
>  - b'\x1a'
>  - b'\n'

- The try and except Block: Handling Exceptions:
- <img src="https://files.realpython.com/media/try_except.c94eabed2c59.png">
- The else Clause:
- <img src="https://files.realpython.com/media/try_except_else.703aaeeb63d3.png">
- Cleaning Up After Using finally:
- <img src="https://files.realpython.com/media/try_except_else_finally.a7fac6c36c55.png">
- raise allows you to throw an exception at any time.
- assert enables you to verify if a certain condition is met and throw an exception if it isn’t.
- In the try clause, all statements are executed until an exception is encountered.
- except is used to catch and handle the exception(s) that are encountered in the try clause.
- else lets you code sections that should run only when no exceptions are encountered in the try clause.
- finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.
