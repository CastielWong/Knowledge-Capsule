
- [Printing](#printing)
  - [Status Bar](#status-bar)
  - [Colorization](#colorization)
- [Literals](#literals)
  - [f-string](#f-string)
  - [r-string](#r-string)
  - [b-string](#b-string)
- [Operator](#operator)
  - [Basics](#basics)
  - [Logical](#logical)
  - [Walrus](#walrus)
- [String Manipulation](#string-manipulation)
  - [Basics](#basics-1)
  - [Loop](#loop)
  - [Sorting](#sorting)
  - [Assignment Expression](#assignment-expression)
- [Function](#function)
  - [Higher Order](#higher-order)
  - [Type Hinting](#type-hinting)
- [Copy](#copy)
- [Exception](#exception)
- [Reference](#reference)


-------------------------------------------------------------------------------
## Printing

### Status Bar
There are two ways to keep printing message overwrite within a line.
The fitted case for it will be monitoring jobs finished in different time.
Note that there will be IO issue in the `print` example code when `time.sleep()` applied.
So the example below use a larger number in iteration to demonstrate the effect.
```py
import sys

ITERATION = 2_000_000

print("start\t\t- `sys.stdout` way...")
for i in range(ITERATION):
    sys.stdout.write(f"\tprint out {i:<8,}\r")
print("complete\t- `sys.stdout` way.")

print("-" * 80)

print("start\t\t- `print` way...")
for i in range(ITERATION):
    print(f"\tprint out {i:<8,}", end="\r", flush=True)
print("complete\t- `print` way.")
```

Apply `sys.stdout` is more flexible for status bar:
```py
import sys
import time

for i in range(1, 21):
    # the new line must print ahead
    sys.stdout.write("\r")

    sys.stdout.write(f"[{'=' * i:<20}] {5 * i}%")
    # sys.stdout.write(f"print out {i:<5}")

    # sys.stdout.flush()  # would be necessary on some systems
    time.sleep(.2)
```

### Colorization

```py
from colorama import Fore, Back, Style

print(Fore.BLACK, end="")
print(Back.BLUE, end="")
print(Style.DIM, end="")

print(f"Text in red")
print(f"Background in blue")
print(f"Style in dim")

print(Style.RESET_ALL, end="")
print("Back to normal")
```


-------------------------------------------------------------------------------
## Literals
Literals are notations for constant values of some built-in types.

There are different types of string literals in Python:
- f-string: formatted
- r-string: raw
- b-string: byte
- u-string: unicode, a legacy literal

The u-string would normally used in Python2, whose strings are ASCII by default.
Using u-string would allow non-ASCII characters for the string in Python.

Note that it's possible to combine different string literals together, like 'rf', 'rb' etc.
However, the 'f' may be combined with 'r', but not with 'b' or 'u', therefore raw formatted
strings are possible, but formatted bytes literals are not.

### f-string
There are multiple ways to use f-string:
- starts with "f" for the string
- use `format()` function built for string type
- apply `format_map()` function to map the string explicitly

```py
text = "texting"

# format the output of actual text via f-strings
print(f"Here comes the text: {text}")
# format the output of actual text in format
print("Here comes the text: {}".format(text))
# format the output centrally
print(f" {text} ".center(30, "-"))

dictionary = {"a": 1, "b": 2, "c": 3}
# format dictionary variable: "a = 1, c = 3"
print("a = {a}, c = {c}".format_map(dictionary))
# output value with the key in dict
print("b = %(b)s" % dictionary) # "b = 2"

# format decimal numbers in string
a = 1.256
b = 2345
# format in f-string with rounding precision: "1.3"
print(f"{a:.2}")
# format in f-string with rounding precision in decimal: "1.26"
print(f"{a:.2f}")
# format in f-string with separator: "2,345"
print(f"{b:,}")
# format in f-string in string formatted with fixed size: "1.256    2345"
print(f"{str(a):8s} {str(b):2s}")
# format in f-strings with "=": "a = 1.256, b = 2345"
print(f"{a = }, {b = }")

# format number in different bases
binary_num = 0b_0101_1010_1111
print(f"{a}")       # default is in decimal: 1455
print(f"{a:_b}")     # binary: 101_1010_111
print(f"{a:_o}")     # octal: 2657
print(f"{a:_d}")     # decimal: 1_455
print(f"{a:_x}")     # hexadecimal: 5af
print(f"{a:#x}")     # hexadecimal: 0x5af

# left/right alignment
# format way
print("{str_1:<20} {str_2:>20}".format(str_1="left aligned", str_2="right aligned"))
# f-string way
print(f"{str_1:<20} {str_2:>20}")


# have string in representation mode
msg = "message"

print("`repr()` shows quotes: {!r}".format(msg))    # `repr()` shows quotes: 'message'
print("while `str()` doesn't: {!s}".format(msg))    # while `str()` doesn't: message
```

### r-string
```py
text = "\ttexting\n"

# output the raw text literally (with "\t", "\n" other than a new line)
print("%r" % text)  # "\ttexting\n"

print("\\a\nb")     # "\a" (new line) "b"
print(r"\a\nb")     # "\a\nb"
```

### b-string
```py
print("a" == "a")   # True
print("a" == b"a")  # false

byte_string = b"\x00\x10"   # 00000000 00010000
print(int.from_bytes(byte_string, byteorder="big"))     # 16    (00000000 00010000)
print(int.from_bytes(byte_string, byteorder="little"))  # 4096  (00010000 00000000)

# convert bytes type
a = b"a \tString"
print(a.decode("ascii"))    # a String
print(a.decode("utf-8"))    # a String

checking = b'\x00\x00\x01l\x05-\xcfA\x00\x00\x09key_09812\x00\x10value_123456789a'
print(int.from_bytes(checking[:8], byteorder="big"))    # 1563454984001
print(int.from_bytes(checking[8:9], byteorder="big"))   # 0
print(int.from_bytes(checking[9:11], byteorder="big"))  # 9
print(checking[11:11+9].decode("utf-8"))                # "key_09812"
print(int.from_bytes(checking[20:22], byteorder="big")) # 16
print(checking[22:22+16].decode("utf-8"))               # "value_123456789a"
```


-------------------------------------------------------------------------------
## Operator

### Basics
```py
a = 11 / 3      # 3.6666666666666665
a = 11 % 3      # 2
a = 11 // 3     # 3
a = 3 ** 2      # 9
a = 3 << 1      # 6
a = 3 ^ 6       # 5 (0011 & 0110 = 0101)
a = 100_000     # 100,000
a = 2.99e8      # 299,000,000.0
a = 4.2e-4      # 0.00042
a = 1.79e308    # approximate maximum float value
a = 5e-324      # approximate minimum float value
a = 1.8e308     # inf
a = 1e-325      # 0.0
a = 2 + 3j      # complex number

a = abs(1 - 3)  # 2
a = float("inf")    # infinite number
```

### Logical
```py
a = "a"
b = "b"

print(a and b)      # "b"
print(a and "")     # ""
print("" and a)     # ""

print(a or b)       # "a"
print(a or "")      # "a"
print("" or a)      # "a"

print(True is 1)    # False
print(True == 1)    # True

a = ["a", "b"]
b = ["a", "b"]
print(a is b)       # False
```

### Walrus
Walrus operator is used for _Assignment Expression_.
```py
with open(__file__, "r") as fr:
    # output content of current file
    while text := fr.readline():
        print(text.strip("\n"))
```


-------------------------------------------------------------------------------
## String Manipulation
### Basics
```py
s = "\tabc\nd\n"
print(s.strip())    # abc\nd
print(repr(s))      # "\tabc\nd\n"
print("\u2192 \N{rightwards arrow}")    # → → (unicode)

s = """this is a string
    This can
        be
            a long string
"""
# find the first occurrence of "is"
s.find("is")  # 2
# find the first occurrence of "is" since index 5
s.find("is", 5)  # 5
s.find("that")  # -1

s = "3"
s.isalpha()  # false
s.isdigit()  # true
s.isalnum()  # true
```

### Loop
```py
a_list = [i for i in range(3, 0, -1)]  # [3, 2, 1]

# (0, 3) -> (1, 2) -> (2, 1)
for index, number in enumerate(a_list):
    print(index, number)

# 1\n 2\n 3\n all done
for i in range(len(a_list) - 1, -1, -1):
    print(a_list[i])
else:   # won't print if the loop is broken
    print("all done")

n = 3
# 2\n 1\n 0\n loop exhausted
while n > 0:
    n -= 1
    print(n)
else:   # won't print if the loop is broken
    print("loop exhausted")

```

### Sorting
```py
a = [1, 5, 3, 2]

# sorted is copied
b = sorted(a, key=lambda x: -x)

print(a)  # [1, 5, 3, 2]

# sort is done in-place, so it would print nothing for the list
a.sort()  # None

print(a)  # [1, 2, 3, 5]
print(b)  # [5, 3, 2, 1]

# convert string to an array in reversed order
print(list(s.strip())[::-1])
```

### Assignment Expression
```py
if (n := len(s)) > 10:
    print(f"The string is too long ({n} elements, expected <= 10)")
```


-------------------------------------------------------------------------------
## Function

### Higher Order
A function is called __Higher Order Function__ if it contains other functions as a parameter or returns a function as an output.

```py
from typing import Callable, Dict

def decorator_func(func: Callable[[], None]):
    def inner(*args, **kwargs):
        print("Before the function is called")
        # unpacking both element and dictionary when pass to the function
        func(*args, **kwargs)
        print("After the function is called")

    return inner

def print_demo_normal(*args: str, **kwargs: Dict[str, str]):
    print("------------------------------------------")
    print("This is the function to decorate in normal")
    print(f"The elements are: {args}")
    print(f"The dictionary are: {kwargs}")
    print("------------------------------------------")

# apply decorator to decorate the function
@decorator_func
def print_demo_with_decorator():
    print("------------------------------------------")
    print("This is the function to decorate with decorator annotation")
    print("------------------------------------------")

demo = decorator_func(print_demo_normal)
# "Before ...\n" ... "This ... normal\n" ... "After ...\n"
demo(1, 2, 3, a="apple", b="banana")
print("========================================================")
# "Before ...\n" "This ... annotation\n" "After ...\n"
print_demo_with_decorator()
# inner
print(print_demo_with_decorator.__name__)
```

### Type Hinting
Other than ordinary Type Hinting, annotation can be applied to check the types of a function.

```py
from typing import List, Tuple

def convert_tuple_to_list(a_tuple: Tuple) -> List:
    return list(a_tuple)

class Book:
    def __init__(self, weight: int):
        self.weight = weight

    @classmethod
    def hardcover(cls, weight: int) -> "Book":
        return cls(weight + 10)

book1 = Book(10)
book2 = Book.hardcover(10)
print(book1.weight)
print(book2.weight)

print(Book.hardcover.__annotations__)
```


-------------------------------------------------------------------------------
## Copy
```py
# note that string and tuple have no copy() method
a = [1, 2, 3]   # [1, 2, 3]
b = a.copy()    # [1, 2, 3]
a[1] = 5        # a: [1, 5, 3], b: [1, 2, 3]

print(f"{a = }\n{b = }")
print(f"a - {id(a)}\nb - {id(b)}")
```


-------------------------------------------------------------------------------
## Exception
The syntax for Python's exception handling is shown below:
```py
try:
    # run the code
except:
    # execute when such exception happens
else:
    # execute when there is no exception
finally:
    # run always no matter what happens
```

Here comes an example illustrates the logic:
```py
checking = [
    "red:14.2",
    "yellow.band",
    "23",
    "purple:-3",
    "blue:0",
    "green: band",
]

valid = 0
value_error = 0
index_error = 0
pass_else = 0
processed = 0

for item in checking:
    try:
        l = item.split(":")
        value = 1 / int(l[1])
        valid += 1
    except ValueError:
        value_error += 1
    except IndexError:
        index_error += 1
    except Exception as ex:
        # catch ZeroDivisionError
        print(f"Other exception: {ex}")
        processed -= 1
    else:
        pass_else += 1
    finally:
        processed += 1

# valid = 1, value_error = 2, index_error = 2, pass_else = 1, processed = 5
print(
    f"{valid = }\n"
    f"{value_error = }, {index_error = }, {pass_else = }\n"
    f"{processed = }"
)
```


-------------------------------------------------------------------------------
## Reference
- String and Bytes literals: https://docs.python.org/3.6/reference/lexical_analysis.html#string-and-bytes-literals
- Format Specification Mini-Language: https://docs.python.org/3/library/string.html#format-specification-mini-language
- Python Type Checking: https://realpython.com/python-type-checking/#annotations
- What Are Python Asterisk and Slash Special Parameters For: https://realpython.com/python-asterisk-and-slash-special-parameters/
