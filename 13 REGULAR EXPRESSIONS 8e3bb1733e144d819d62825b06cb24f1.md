# 13. REGULAR EXPRESSIONS

[Regular Expressions: Regexes in Python (Part 1) - Real Python](https://realpython.com/regex-python/)

[Python RegEx](https://www.w3schools.com/python/python_regex.asp)

[regex101: build, test, and debug regex](https://regex101.com/)

```python
import re
s = "search box ..."
"box" in s #this is the simpliest way to search inside a string

reg = re.search("box", s)   
reg.span()
reg.start()
reg.end()
reg.group()

pattern = re.compile("box")
pattern.search(s) # the search method: will return a MatchObject if something get found, otherwise it will return None
pattern.findall(s)
pattern.fullmatch(s)
pattern.match(s)
```

```python
# email_validator.py
pattern = re.compile(r"(^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$)")
s = "o@o.com"
match = pattern.search(s)
print(match)
```

```python
# password_validator.py

pattern = re.compile(r"[a-zA-Z0-9%$#@]{8,}") # r"[a-zA-Z0-9%$#@]{8,}\d$" or r"[a-zA-Z0-9%$#@]{8,}[0-9]$"
s = "secrett$9c"
match = pattern.search(s)
print(match)

# PS : r"" stands for raw string
```