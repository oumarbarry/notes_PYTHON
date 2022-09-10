# 12. FILE IO

[Working With Files in Python - Real Python](https://realpython.com/working-with-files-in-python/)

## Working with Files in Python

```python
# MODERN WAY: the better way to work with file in python is by using the built-in 'with' statement
with open('test.txt', mode='r') as my_file:
	print(my_file.readlines())

# CLASSIC WAY
my_file = open('test.txt')
print( my_file.read() ) #--> return all the file content
print( my_file.seek(0) ) #--> allow us to set the position of the cursor in the file
print( my_file.readline )
print( my_file.readlines() ) #--> returns a list where each item correspond to one line of the file
my_file.close()
```

<aside>
💡 mode='r': read mode, the default open mode, places the cursor at the beginning of the file
mode='w': write mode creates a new file if it doesn't exist or delete and replace the existing one
mode='a': append mode, for adding data to the end of the file
mode='r+': for reading and writing at the same time

</aside>

## File Paths

- ABSOLUTE vs RELATIVE paths
- Windows vs Unix paths

<aside>
💡 **pathlib**: a built-in module to manage both windows and unix filesystem paths

[pathlib - Object-oriented filesystem paths - Python 3.10.5 documentation](https://docs.python.org/3/library/pathlib.html)

</aside>

## File IO Errors

```python
try:
	with open('test.txt', mode='r') as my_file:
		print(my_file.readlines())
except FileNotFoundError as err:
	print("file does not exist")
	raise err
except IOError as err:
	print("IOError usually occurs when the computer has some issue for reading or writing or doing any sort of IO operation on the file")
	raise err
```

## Create a file translator

[translate](https://pypi.org/project/translate/)

```python
from translate import Translator

translator = Translator(to_lang="ja")

try:
	with open("original.txt", mode="r") as original:
		translation = translator.translate( original.read() )
		with open("translate_in_japanese.txt", mode="w") as trans:
			trans.write(translation)
except FileNotFoundError as e:
	print("file does not exist, check the file path")

```