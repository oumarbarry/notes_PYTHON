# 10. MODULES IN PYTHON

[Python Modules and Packages - An Introduction - Real Python](https://realpython.com/python-modules-packages/)

## Modules

<aside>
⚙ **each .py file is a module**

MODULE NAME CONVENTION :  **snake_case** too (like variables & functions)

</aside>

### **__pycache__**

<aside>
💡 It’s a folder that is created the first time we run a file (module) **with import statement.**

Inside is created compiled **cpython file(s)** that cache all imported modules (for optimization : speed improvements).

</aside>

## __name__

<aside>
💡 A module can either be imported or directly executed:

- if directly executed: **__name__ = '__main__'**
- if imported: __name__ = “<name of the module / package path until module location>”
</aside>

```python
# this dunder variable is commonly use to test the entire module or a piece of code when directly executed

if __name__ = '__main__':
	#do_something

#this is a good way to check how our modules are being used whether imported or run
```

## Packages

<aside>
💡 A package is simply **a folder** that contains modules and maybe also other packages.

One of the rules of a python package is that you must have an __**init__.py** file on his root (that's the way the interpreter recognizes a folder as a python package).

</aside>

```python
# packages/modules can be imported in different ways
# so the recommandation is to always be explicit

import ... (as) ...
from ... import ...
from ... import ... (as) ...

# PS : when we import something, when the interpreter finds the module, it runs its code and so adds this code to memory (because we're going to use it)
```

<aside>
💡 how to organize your code ? well with functions, classes, modules & packages

how to divide code in module ? similarly to class or function, we want divide up the code into chunks that make sense

</aside>

## The Power of Python

### The Standard Library (Python Built-in Modules)

```python
# when you import a module / a library that you don't know what it does, a key thing is to run in the REPL:
help(module_name)
dir(module_name)
```

```python
# example.py

import random
random.random()
random.randint(1, 10)
random.choice(iterable)
random.shuffle(sequence)
```

### Third Party-Packages

[PyPI · The Python Package Index](https://pypi.org/)

<aside>
💡 a common good practice is to check, if researched module already exists in the python built-in modules before looking at pypi.org

</aside>

```python
pip install <package>==<version>
pip install pyjokes==0.4.0 # tfixed version

pip install <package>
pip install pyjokes # this will automatically install the lastest version of the package
				
# usage.py
import pyjokes
print( pyjokes.get_joke('en') )
```

<aside>
💡 T**he true power of Python comes from the COMMUNITY.**

</aside>

> there's so many modules out there, so the best way to learn many of them is to just keep coding
> 

## Useful Built-in Modules

```python
#   some specialized data types
from collections import Counter, defaultdict, OrderedDict

# counter class create counter object from an iterable
# counter object format: { listitem: occurence_in_the_iterable }
li = [3,1,3,4,2,3,3]
print( Counter(li) ) #-> output: {3:4,1:1,2:1,4:1}

# defaultdict: with these objects, you can specify a default value for all unexisting key
# variable = defaultdict(callabe_function_or_none, normal_dictionnary)

# first argument must be a callabe function or None, if it's None it will raise KeyError like normal dictionnary
dd = defaultdict(lambda: 'DOES NOT EXIST', {'a':1, 'b':2} )
dd['y'] #-> will output: DOES NOT EXIST

#OrderedDict: an OrderedDict retains the order that you insert item into it
do = OrderedDict()
do['a'] = 1

from time import time

import datetime
datetime.date.today()

from array import array
# array(typecode, seqence)
arr = array('i', [1,2,3])
```

<aside>
💡 **Difference between list and array**

- list are dynamic, anytime we need we can incrementally increase a list and fill up memory
- where with array
    - when we create one, it sets how much memory we can use in our machine (arrays so take up less memory and perform faster)
    - so when we don't want to use generators and we have a massive list, this is a quick easy way to optimize code
</aside>

## Virtual Environments

Virtual Envs **answers the question of how can we have multiple versions of any package on the same machine and so have different projects using different versions.**

```bash
# tools to spin up a virtual environment : **the built-in venv, pipenv, conda, virtualenv**

python -m venv <virtual_env_name>
```

## Semantic Versionning

```python
# format: **first_num:second_num:third_num** (like v1.4.3)

- first_num: is usually about breaking changes (major versions)
- second_num: new releases (maybe some added features)
- third_num: usually used for bug fixes (by incrementing it)
```

[Semantic Versioning 2.0.0](https://semver.org/)

## *Dev. Fundamentals 6:* Pros and cons of librairies

<aside>
💡 1. Out there, we can have really good packages but also really bad packages, so be careful of using any library. So as developer we have to develop that skill to recognize “hey this package is really popular with the community, this package is being maintained”, so most likely it's a good package to use.

2. Remember that adding more and more library to our code, means adding more & more code, so more and more bytes of data, so projects can get heavier and heavier. So Before importing a library, ask yourself, could I just write it myself ? If writing it yourself will be really time consuming or you don't have expertise on that area, then **choose importing.**

1. Learn to read library documentation well.
</aside>