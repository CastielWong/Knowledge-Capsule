
Generator functions are a special kind of function that return a laze iterator.

For instance, when a file is opened, a generator would loop through each line
then yields each row, other than read all lines and return as a whole.
```py
# generator function
def csv_reader(file_name):
    for row in open(file_name, "r"):
        yield row

# generator expression
csv_gen = (row for row in open(file_name))
```

When the `yield` statement is hit, the program suspends function execution and returns the yielded value to the caller.
In contrast, `return` stops function execution completely.

When a function is suspended, the state of that function is saved.
This includes any variable bindings local to the generator, the instruction pointer,
the internal stack, and any exception handling.

`next()` is callable for generator object:
```py
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1

generator = infinite_sequence()
print(next(generator))
print(next(generator))

nums_list = [num ** 2 for num in range(5)]
nums_generator = (num ** 2 for num in range(5))
print(nums_list)        # [0, 1, 4, 9, 16]
print(nums_generator)   # <generator object ...>
```


Restart the same Generator: https://blog.finxter.com/how-to-iterate-over-a-generator-twice/
