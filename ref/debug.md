---
layout: home
title: 🐛&nbsp;&nbsp; Debugging 
parent: References
nav_order: 3
seo:
  type: Resource
  name: Debugging scenarios and solutions
---

!['A cartoon of a fuzzy round monster face showing 10 different emotions experienced during the process of debugging code. The progression goes from (1) “I got this” - looking determined and optimistic; (2) “Huh. Really thought that was it.” - looking a bit baffled; (3) “...” - looking up at the ceiling in thought; (4) “Fine. Restarting.” - looking a bit annoyed; (5) “OH WTF.” Looking very frazzled and frustrated; (6) “Zombie meltdown.” - looking like a full meltdown; (7) (blank) - sleeping; (8) “A NEW HOPE!” - a happy looking monster with a lightbulb above; (9) “insert awesome theme song” - looking determined and typing away; (10) “I love coding” - arms raised in victory with a big smile, with confetti falling.'](https://github.com/allisonhorst/stats-illustrations/blob/master/other-stats-artwork/debugging.jpg?raw=true "Faces of debugging")
Artwork by `@allison_horst`
{: .fs-2 }

# 🐛 Debugging scenarios and solutions
{:.no_toc}

## Quick debugging tips
1. Read the error message and look at the line that it refers to.
    1. Sometimes the issue is at the line just **above** the line that was listed in the error.
    1. If enabled, pay close attention to the **syntax highlighting** in your editor, which can point at where the error might be happening.
1. Use `print()` statements to display the type and value of your variable.
1. Go back to the instructions and carefully re-read them.
1. Use [Python Tutor to visualize your code](https://pythontutor.com/visualize.html#mode=edit).
1. Use the [Rubber Duck Debugging](https://rubberduckdebugging.com) to walk yourself through the logic of your code.

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## `SyntaxError: unexpected EOF while parsing`

*   **Cause**:  Missing a closing parenthesis `)`.
*   Example erroneous code:
```py
print('Hello, World'
```
*   Corrected line of code: 
```py
print("Hello, World")
```

---

## `SyntaxError: invalid syntax`

This is a general error that occurs when the syntax is not correct and a "Python sentence" is broken.
    If enabled, pay close attention to the syntax highlighting, which can point at where the error might be happening.

Below are sample Python syntax rules:
1. A function call must start and end with a parenthesis; the number of open and closed parentheses must match.
1. The literal text has to be enclosed within the quotation marks.
1. Variables must first be defined (created) before being used.

<br/>

*   **Cause**:   Missing **opening** quotation mark or **opening** parenthesis or quotations around the text.
*   Example erroneous code:
```py
print(Hello World')
print'Hello World  
print(Hello World) # see also NameError
```

---

## `SyntaxError: unmatched ')'`
*   **Cause**:  an extra **closing** parenthesis `)` that does not have a matching **opening** paren `(`.
*   Example erroneous code:
```py
print('Hello, World'))
```

---

## `EOL while scanning string literal`

*   **Cause**:   Missing a **closing** quotation mark or a mismatched quotation mark (incorrectly placed quotation can also cause it).
*   Example erroneous code:
```py
print('Hello, World) # missing a quotation mark
```
or
```py
print('Hello, World") # mismatched quotation marks
```


---

## `NameError: name '...' is not defined`

Python would replace the ellipsis `...` with the name of the variable that it's unable to find.
*   **Cause**:   Generally, this error happens when a function name or a variable name 
    * is misspelled 
    * has not been properly defined first

For example:

`NameError: name 'Print' is not defined`
* Example erroneous code:
```py
Print('Hello, World')
```
*   **Cause**:   In this case, the function name is "misspelled" - an accidentally capitalized name of the function makes Python look for a variable called `Print`.    


This error can also be caused if there is a **single word** (or comma-separated words) inside the `print()` that needed to be displayed as the literal text but does not include quotation marks around it (similar to the `SyntaxError: invalid syntax`).

*   Example erroneous code: 
```
print(Hello)
print(Hello, World)
```
generates the same error (`NameError: name 'Hello' is not defined`), since Python is now looking for a variable called `Hello` - it doesn’t know that we just forgot to put quotation marks around the text.

---

### `NameError` with a dictionary

*   `NameError: name 'A' is not defined`
*   Example erroneous code:
```py
dict1 = {"A":1, "B":2, "C":3}
print(dict1[A])
```
*   **Cause**:  Missing quotation marks (`" "`) when indexing a key from the dictionary.

*   Correct code: 
```py
dict1 = {"A":1, "B":2, "C":3}
print(dict1["A"])
```

---

### Output printing None

* None is printed even though you don't want it to be there 
* Example erroneous code: 
```py
def print_hello():
  print("hello")
if __name__ == '__main__':
  print(print_hello())
```

* **Cause**: The function print_hello() does not return anything (it has no return statement) so when you call print(print_hello()) you are printing the return value which is None. 

* Correct code: 
```py
def print_hello():
  print("hello")
if __name__ == '__main__':
  print_hello()
```

---

### Positional Arguments Error

* Let's first look at the case where too many arguments were provided in the function call
* `print_name takes 0 positional arguments but 1 was given`
* Example erroneous code: 
```py
def print_name():
  print("Sam")
if __name__ == '__main__':
  print_name("Sam")
```
* **Cause**: The function print_name() does not take any parameters but when calling the function one parameter is being passed. This error signifies that there is a mismatch between the number of parameteres in the function defintion and the number of arguments in the function call. 

* Correct code: 
```py
def print_name():
  print("Sam")
if __name__ == '__main__':
  print_name()
```
* This also works the other way around if you are missing arguments in the function call
* `get_largest() missing 1 required positional argument: 'y'`
* Example erroneous code: 
```py
def get_largest(x,y):
    return max(x,y)
if __name__ == '__main__':
  x = int(input())
  y = int(input())
  print(get_largest(x))
```
* **Cause**: The function get_largest takes in two parameters but when calling the function one is passed in. This error likewise signifies that there is a mismatch between the number of parameteres in the function defintion and the number of arguments in the function call. 

* Correct code: 
```py
def get_largest(x,y):
    return max(x,y)
if __name__ == '__main__':
  x = int(input())
  y = int(input())
  print(get_largest(x,y))
  
```

---

### Logic Errors
* Sometimes, we get a logic error, when the output does not match what we expect.
* Example erroneous code: 
```py
def get_largest(x,y):
    if x > y: 
      return y
    else: 
      return x
```
* **Cause**: Although the syntax of this function is correct and the function will produce no results while compiling, the result will be incorrect. This is simply due to a logical error. 

* Correct code: 
```py
def get_largest(x,y):
    if x > y: 
      return x
    else: 
      return y
```

---

### Address getting printed
*   Function Address gets printed - `<function function_name at 0x....> `
*   Example erroneous code:
```py
def area(radius):
    return 3.14 * radius**2
if __name__ == '__main__':   
  radius = float(input())
  print(f"Circle has area {area} inches squared.")
```
*   **Cause**:  Calling the function improperly without passing in a parameter 
*   Correct code: 
```py
def area(radius):
    return 3.14 * radius**2
if __name__ == '__main__': 
  radius = float(input())
  print(f"Circle has area {area(radius)} inches squared.")
```  
---

### Indentation Error
* `IndentationError: unexpected indent`
*   Example erroneous code:
```py
print("Hello world!")
    print("What a nice day!")
```
*   **Cause**:   Indented even though it is not necessary. 
*   Correct code: 
```py
print("Hello world!")
print("What a nice day!")
```

---
### Type Error
* `TypeError`
* Example erroneous code:
```py
num = 6
print("I would like " + num + " tacos please.")
```
*   **Cause**:    You can only concatenate a string, not an interger type with a string. 
* Correct code: 
```py
num = 6
print("I would like", num, "tacos please.")
```
or 
```py
num = 6
print("I would like " + str(num) + " tacos please.")
```

---
### Value Error
*   `ValueError: invalid literal for int() with base 10: '1792.99'`
*   Example erroneous code:
```py
current_year = '1792.99'
current_year = int(current_year)
print(current_year)
```
*   **Cause**:   If you do want to pass a string representation of a float to an int,  you need to convert to a float first, then to an integer.
*   Correct code: 
```py
current_year = '1792.99'
current_year = float(current_year)
current_year = int(current_year)
print(current_year)
```
## Acknowledgement

Developed by Yekaterina Kharitonova with assistance from students and course mentors.
{: .fs-2 }

Special thanks to Liu Kurafeeva for creating the initial formatting of this page.
{: .fs-2 }
