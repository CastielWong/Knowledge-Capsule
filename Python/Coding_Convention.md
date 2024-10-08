
This documentation is to suggest/recommend the good coding style in Python.

- [General](#general)
- [Naming Convention](#naming-convention)
- [Header](#header)
- [Importing](#importing)
- [Main Function](#main-function)
- [Type Hinting](#type-hinting)
- [Docstring](#docstring)
- [Practice](#practice)
  - [Docker](#docker)
  - [Pre-Commit](#pre-commit)
  - [Testing](#testing)
    - [Unit](#unit)
    - [Integration](#integration)
    - [System](#system)
- [Reference](#reference)



SemVer, which refers to __Semantic Versioning__, is the phrase describe how to version the system.

SemVer is a 3-component system in the format of "x.y.z" where:
- "x" stands for a __major__ version
- "y" stands for a __minor__ version
- "z" stands for a __patch__

Note that it should be considered as development phase when the version is before __1.0.0__.


## General
| Item | Detail |
| --- | --- |
| Indentation | 4 spaces, no tab |
| Blank Lines | 2 for top-level definitions, like between import statements and the first class/function definition |
| Blank Lines | 1 between method definitions |
| Blank Lines | 1 when it improves code readability |
| Type Hinting | Apply Type Hinting whenever defining a new function |
| Purely Functional | In case unexpected side effect, a function with return value(s) should not update any data structure inside |

## Naming Convention
| Type      | Pattern     | Example         |
|-----------|-------------|-----------------|
| Package   | Snake Case  | package_a       |
| Module    | Snake Case  | module_a        |
| Class     | Pascal Case | DemoClass       |
| Function  | Snake Case  | demo_function() |
| Constant  | Macro Case  | GLOBAL_CONSTANT |
| Variable  | Snake Case  | class_var       |
| Parameter | Snake Case  | function_param  |

Note that even though Python doesn't support private element like common OOP language as JAVA, it's highly recommended to add a leading "_" to any private element (function/variable) for clarification.


## Header
It's a good practice to put clarified header at the top of each python file. For instance:

```py
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```


## Importing
There are three levels imports: inbuilt, third-party, customized. For better readability, it's suggested to have the import statements to follow order as the example:

```py
import {inbuilt}

import {third-party}

import {customized}
```

And there are three kinds of import statements, it's suggested to import them like:

```py
from {package} import {module}
import {package_a}
import {package_b} as {pac}
```

Import statements under the same style are ordered alphabetically for sure.


## Main Function
There are four key best practices about `main()` in Python:
1. Put code that takes a long time to run or has other effects on the computer in a function or class, so you can control exactly when that code is executed
2. Use the different values of `__name__` to determine the context and change the behavior of your code with a conditional statement
3. Even though Python does not assign any special significance to a function named main(), it's highly recommended to name the entry point function `main()`
4. Define the logic in functions outside `main()` and call those functions within `main()`, which helps to improve the code reusability


## Type Hinting
It improves readability to have function annotation clarified as [PEP 484](https://www.python.org/dev/peps/pep-0484/) indicated. Below is examples for common use cases:

```py
from typing import Dict, List, Union


def demo_main() -> None:
    pass

def demo_func_a(arg1: str, arg2: Dict) -> List:
    pass

def demo_func_b(arg: Union[List, Dict]) -> int:
    pass
```


## Docstring
Use triple quotes and apply [Google Style](https://google.github.io/styleguide/pyguide.html) for Docstring.

```py
def demo_function(arg1: int, arg2: float) -> [str, int]:
    """
    This is a demo function.

    Args:
        arg1: argument 1
        arg2: argument 2

    Returns:
        An answer in string or interger
    """
    pass
```


## Practice
### Docker
For docker-compose, the configuration order structure is suggested to be:
- config related to container
- config for network
- config for volume
- config about orchestration

For instance,
```yaml
version: 3.5

volumes:
  vol_check_var:
    name: lab_xxx

services:
  xxx:
    restart: always
    container_name: ...
    image: ...
    environments:
      - ...=...
    command:
      - ...
    networks:
      - lab_xxx
    ports:
      - ...:...
    volumes:
      - vol_check_var:/opt/xxx/var
    depends_on:
      - ...

networks:
  lab_xxx:
    name: ...
    driver: bridge
    ipam:
      cofing:
        - subnet: a.b.c.d/..
```

### Pre-Commit
If a hook in pre-commit needs customization, it's advised to place such configuration inside a dedicated folder like "dev/".
The "pre-commit-config.yaml" needs to be able to locate the customized configuration file accordingly.

For instance:
```yaml
- repo: https://github.com/pre-commit/mirrors-pylint
  rev: v3.0.0.a5
  hooks:
  - id: pylint
    args:
    - --rcfile=dev/.pylintrc
```

### Testing
#### Unit
Here is the general cases to refer when developing unit tests:
- happy path:
  - parameter - single
  - parameter - multiple in order
  - parameter - multiple in disorder
  - parameter - all
- corner case:
  - parameter - null
  - parameter - missing
  - parameter - extra
  - parameter - different types

#### Integration
The Integration Testing is normally applied to components/systems connected testing.
Any dependent component/system should be created or mocked locally for such testing.


#### System
The System Testing is supposed to be involved with components/systems outside of current one.



## Reference
- Naming Convention: https://en.wikipedia.org/wiki/Naming_convention_(programming)
- The Meaning of Underscores: https://dbader.org/blog/meaning-of-underscores-in-python
- Functional Programming HOWTO: https://docs.python.org/3/howto/functional.html#introduction
- Defining Main Functions in Python: https://realpython.com/python-main-function/#summary-of-python-main-function-best-practices
- Google Python Style Guide: https://google.github.io/styleguide/pyguide.html#313-imports-formatting
- Python Code Quality - Tools & Best Practices: https://realpython.com/python-code-quality/
- The Big Ol' List of Rules: https://www.flake8rules.com/
- Main in Python: https://realpython.com/if-name-main-python/
