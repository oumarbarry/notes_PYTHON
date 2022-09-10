# 08. ERROR HANDLING

<aside>
💡 Error are unavoidable in programming, so as dev, our job is to **be able to anticipate these errors**, these bugs, these exceptions  and **handle them properly/gracefully** in our programs

</aside>

## Errors in Python

<aside>
⚙ In Python, an error is called “**exception”.**

Python raises these exceptions whenever the interpreter says “hey I have no idea about what  you’re doing, something is wrong, I don't know what to do do anymore, so I'm going to stop whatever I'm doing and give you an output”.

</aside>

## Built-in Exceptions

[Built-in Exceptions in Python - GeeksforGeeks](https://www.geeksforgeeks.org/built-exceptions-python/)

<aside>
⚙ Some Python Built-in Exceptions

- SyntaxError
- ZeroDivisionError
- ValueError
- NameError: raised when a variable or a function is undefined in the code
- IndexError: raised when the index of a list doesn't exist
- KeyError : raised when the key of the dictionary doesn't exist
</aside>

## Error Handling

<aside>
💡 Error handling allows us to let the python script continue running even if there are errors

</aside>

```python
# FORMAT
try:
	# code_to_test
except <NameOfError> as error:
	# do something when the specified NameOfError get caught like : print(error)
except <AnotherErrorName>:
	# if an error is caught only one except block is run, like with if..elif
except:
	# do something for all other kind of errors
else:
	# do something when there is no raised error
finally:
	# do something if there is error or not
	# this part will **always** run at the end of the try,except,else block statement
```

```python
# example.py
while True:
	try:
		age = int(input("what's your age ? "))
		raise Exception('boo boo something badly wrong happens')
	except ValueError:
		print("numbers are required")
	else:
		print(age)
		break
	finally:
		print('even with break statement in the else block, the finally block will runs after')
	
def divider(num1, num2):
	try:
		return num1/num2
	except (TypeError, ZeroDivisionError) as err:
		print(err)
```

### raise

[Python Exceptions: An Introduction - Real Python](https://realpython.com/python-exceptions/)