
[[PYTHON/Plurasight Core Python/getting started/_ 0 Getting Started | getting started]]


# Exceptions
#python/errors_and_exceptions 
>[!definition] exception handling
>machanism for interrupting normal program flow and continuing in surrounding context
>

## Key concepts
1. **Raising** an exception - the event of interrupting normal flow
2. **handling** an exception - in some enclosing context, the raised exception must be handled upon which control flow is transferred to the exception handler
3. **unhandled** exceptions - cause the program to terminate
4. An exception **object** contains information about where and why an exceptional event occurred is transported from the point at which the exception was raise to the exception handler

## Exceptions and Control Flow
![[python_exceptions.excalidraw| 700]]

You can also  write:
```python
except (KeyError, TypeError):
  x = -1
```


## Exceptions and Programmer Errors
Exceptions resulting from programmer errors:
- `IndentationError`
- `SyntaxError`
- `NameError`

These should almost never be caught

### Accessing Exception Objects
```python
import sys

DIGIT_MAP = ...

def convert(s):
  try:
    number=''
    for token in s:
      number+ DIGIT_MAP[token]
    return int(number)
  except (KeyError, TypeError) as e: # 'e' is an exception object
    # stderr standard error
    print(f"Conversion error: {e!r}", file=sys.stderr) 

	return -1
```


## Re-raising exceptions
Instead of returning an un-Pythonic error code, we can simply omit error message and re-raise the exception object we're currently handling (change `return -1` into `raise` - without parameter `raise`  simply re-raises the exception that is being currently handled)


## Exceptions Are Part of the API

### Use standard exception types:
>[!important] **standard types**
>Python provides standard exceptions types for signalling common errors

>[!important] **invalid argument values**
>Use `ValueError` for arguments of the right type but with an invalid value

> [!important] **exception constructors**
> Use raise `ValueError()` to raise an new ValueError

### Example
```python
import sys

def sqrt(x):
"""
 Compute square roots using the methd of Heron of Alexandria
	Args:
	 x: The number for which the square root is to be computed
    Returns:
     the square root of x
    Raises:
     ValueError: if x is negativ 
"""
	
	if x < 0:
		raise ValueError( "Cannot compute square root of" 
		f"negative number {x}")

	guess = x
	i = 0
	while guess *guess !=x i < 20:
		guess=(guess + x / gueass) / 2.0
		i += 1
	return guess

def main():
 try:
  print(sqrt(9))
  print(sqrt(2))
  print(sqrt(-1))
 exception ValueError as e:
  print(e, file=sys.stderr)

print("Program executed without exception")
   
```

## Exception  and Protocols

- e.g. : Sequences shoul raise `IndexError` for out-of-bounds indexing
- exceptions must be implemented and documented correctrly
- Existing built-in exceptions are often the right ones to use (choose rather built-in types od exception)

>[!rule] Follow existing patterns
> The more your code follows established patterns, the easier it will be for others to use.


### Common Exception Types
#### IndexError
an integer index is out of range

#### ValueError
an object is of the correct type but has an inappropriate value

#### KeyError
a lookup in a mapping failed


## Python philosophy
>[!important] Avoid catching `TypeError`
> - increase function reusability
> - let `TypeErrors` arise on their own

>[!important]  EAFP
> It's Easier to Ask Forgiveness then Permission
>
Python prefers EAFP

>[!important] LBYL
>Look before you leap


### example:
```python
# process file: LBYL
import os

p = '/path/to/datafile.dat'

if os.path.exists(p):
  process_file(p)
else:
 print(f"No such file as {p}"")
```
some problems:
- a file exists but has incorrect content
- the path exists but it is a folder path 
- after check another process deleted this file

```python
# Process file: EAFP

p = '/path/to/datafile.dat'

try:
  process_file(f)
except OSError as e:
  print(f'Error: {e}')
  
```

### EAFP plus Exceptions
1. Exceptions are not easily ignored
2. Error codes are silent by default
3. Exceptions plus EAFP makes it hard for problems to be silently ignored






























