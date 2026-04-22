# Modules and Packages

## Simple Explanation (Hinglish)
Jab code bohot bada ho jata hai, toh hum saara code ek hi dookaan (file) mein nahi rakhte. Hum alag-alag departments (files) bana dete hain. In alag files ko **Modules** bolte hain. 
Aur jab bahot saare modules ko ek properly organized folder mein dalte hain, toh us folder ko **Package** bolte hain. Kisi dusri file se variables ya functions mangwane ke liye hum `import` ka use karte hain.

## Theory (Clear + Structured)
- **Module**: A simple `.py` file containing Python code (functions, classes, variables).
- **Package**: A directory that contains a collection of modules. It usually includes a special file called `__init__.py` (required in older Python versions) which tells Python that this directory is a package.
- **Import Statements**: Used to bring code from one module into another.

## Syntax
```python
import module_name
from module_name import function_name
```

## Examples

```python
# Assuming we have a file named "math_ops.py" with a function add(a, b):

# Example 1: Basic Import
import math_ops

result = math_ops.add(5, 10)
print(result)

# Example 2: Importing specific function
from math_ops import add

result = add(5, 10)  # Direct use without module name prefix
print(result)

# Example 3: Aliasing (Giving a nickname)
import math_ops as m

print(m.add(5, 10))
```

## Dry Run / Explanation
* `import math_ops`: Python dekhega ki kya `math_ops.py` naam ki koi file aas-paas (ya library path mein) hai? Agar hai toh usko load kar lega. Usko use krne k liye module ka naam dot `.` lagana padta hai (`math_ops.add()`).
* `from math_ops import add`: Is syntax se aap seedha function utha lete ho. Fayda yeh hai ki baar baar `math_ops.` likhne ki mehnat nahi lagti.

## Common Mistakes
1.  **Circular Imports**: File A imports File B, and File B imports File A. This causes Python to crash with a confusing Import error.
2.  **Naming conflicts**: Naming your python file the same as a built-in module (e.g., naming your file `random.py` will break Python's actual `random` library if you try to import it).

## Interview Notes
1. **`__main__` block**: Interviewers often ask about `if __name__ == "__main__":`. It is used to ensure that a piece of code runs ONLY if the file is run directly, and NOT if it is imported into another file.
2. What does `__init__.py` do? It treats the directory as a package and allows you to run initialization code.

## Practice Questions

**Easy:**
1. Import Python's built-in `math` module and use it to print the square root of 16.
2. Import datetime module and print current date and time.
3. Use `from random import randint` to generate random number between 1-100.
4. Import specific function from module: `from math import pi, sqrt`.
5. Create alias while importing: `import numpy as np` (practice with any module).
6. Import all functions from a module using `*` (not recommended but practice).
7. Use `sys` module to get Python version and command line arguments.
8. Import `os` module and print current working directory.
9. Use `collections` module to create Counter from list.
10. Import `json` module and parse a JSON string to dictionary.

**Medium:**
1. Create a file `greetings.py` with a function `say_hello()`. Create a second file `main.py` and import that function from the first file.
2. Create package structure: mypkg/__init__.py, mypkg/module1.py, mypkg/module2.py.
3. Implement relative imports within a package (from .module1 import func).
4. Create custom module with multiple functions, import selectively in another file.
5. Use `if __name__ == "__main__":` to make module executable and importable.
6. Create package with __all__ to control what gets exported with `from pkg import *`.
7. Handle circular import issue by restructuring code or using local imports.
8. Create utility module with helper functions, use across multiple project files.
9. Import class from one module and inherit in another module.
10. Create subpackage structure: pkg/subpkg/module.py with proper imports.

**Hard:**
1. Explain practically how `if __name__ == "__main__":` prevents code from executing during an import by making two files and demonstrating it.
2. Design large-scale package structure for web application with blueprints.
3. Implement lazy loading of modules using importlib for performance optimization.
4. Create dynamic imports based on configuration using importlib.import_module().
5. Build plugin system that discovers and loads modules from directory automatically.
6. Handle version conflicts when importing same package with different versions.
7. Create namespace package (PEP 420) without __init__.py files.
8. Implement hot-reloading: reload modified modules without restarting application.
9. Design monorepo structure with shared packages and proper import paths.
10. Create distribution package with setup.py, publish to PyPI (theoretical + structure).
