# Python List Comprehensions

The pattern of looping through a list, transforming each item, and appending each item to a new list is so common that Python has a cool built-in way to handle it, called *list comprehensions*

Making a new list:

```py
names = ['Shawna', 'Jamie', 'Ambar']

names_upper = []

for name in names:
	names_upper.append(name.upper())

names_upper = ['SHAWNA', 'JAMIE', 'AMBAR']

```
---
# Refactored with List Comprehension

```py

names = ['Shawna', 'Jamie', 'Ambar']
# the transformation and creation of a new array is one step
names_upper = [name.upper() for name in names]

names_upper = ['SHAWNA', 'JAMIE', 'AMBAR']
```
