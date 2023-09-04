## Collections in Python

- We've seen how we represent numbers, text, and True/False as well as the idea of variables. What happens if we want to represent a collection in Python? The data types we will use most often for that are **lists**, **tuples**, and **dictionaries**. Additional specialized data types can be found in the [documentation](https://docs.python.org/3/library/datatypes.html).

---

- **Lists** are useful for demonstrating collections of items and are enclosed in square brackets `[]`. Lists are similar to arrays in JS. They can be items of the same type or different types. Can you have a list of lists? Sure. Lists, as all other data types, can be assigned as values to variables. For example:

```py
	# list of strings represented by the variable, `flavors`
	flavors = ["chocolate", "Cherry Garcia", "vanilla"]
	# list of tuples represented by the variable `scores`
	scores = [("UNC", 98), ("Duke", 89)]
	# list of dictionaries represented by the variable `bands`
	bands = [
	{"Foo Fighters": {
		"Dave Grohl": ("guitar", "lead vocals"),
		"Pat Smear": "guitar",
		"Chris Shiflett": ("guitar", "backing vocals"),
		"Nate Mendel": "bass",
		"Taylor Hawkins": ("drums", "percussion", "backing vocals"),
		"Rami Jaffee": ("keyboard", "piano"),
		}
	},
	{"Nickelback": {
		"Chad Kroeger": ("lead vocals", "lead guitar"),
		"Ryan Peake": ("rhythm guitar", "backing vocals", "keyboard"),
		"Mike Kroeger": "bass",
		"Daniel Adair": ("drums", "percussion", "backing vocals"),
		}
	}]
	# list of various types of objects
	various = ["A WORD", 6, False, -25.0, ("a", "tuple")]
```

---

Lists are ordered, that is, every item has its place in line, called its **index**,
like picking a number at the deli or the DMV. The numbers start at 0, the far left item in the list.

```py
	animals = ["zebra", "pika", "octopus", "black bear"]
        #             ↑	      ↑        ↑            ↑
	# index	      0       1        2            3
```

We can retrieve items from a list using its _index_, like this:

```py
	> animals[2]
	> "octopus"

```

We can also _slice_ a list, obtaining a segment of the list with indexes, `[start:stop]`, which is non-inclusive, meaning we get the item right before the stop index, but not the one at the stop index. If no start is given, the default value is 0. If no stop is given, the default value is the length of the list (the last index position + 1).

```py
	> animals[1:3]
	>['pika', 'octopus']

```

We can change the value at a given index like this:

```py
   animals[3] = "orangutan"
   # now look at the list
   > animals
   > ["zebra", "pika", "octopus", "orangutan"]
```

---

Python provides a number of **built-in methods for lists**. Using the following list
as an example, let's look at several of the methods we will use most often:

### The `len()` function tells us the length of an object and works on lists as well as every other data type.

This is like array.length in JS

```py
>>> len(["apples", "peaches", "pumpkin pie"])
>>> 3
```

### `append()` adds an item to the end of a list

This is like `push` in JS.

```py
>>> nerf_guns.append('Jolt')
>>> nerf_guns
['Rampage', 'Shockwave RD-15', 'Mediator', 'Jolt']
```

### `pop()` removes the last item from the end

```py
>>> nerf_guns.pop() # this returns the item you popped off the list, and alters the list
'Jolt'
>>> nerf_guns
['Rampage', 'Shockwave RD-15', 'Mediator']
```

### `remove()` deletes a specified item

```py
>>> nerf_guns.remove('Mediator') # this does not return the thing you removed, but it does change the list
>>> nerf_guns
['Rampage', 'Shockwave RD-15']
```

#### The rest of the `list` methods can be found in the [Python docs](https://docs.python.org/3/tutorial/datastructures.html).

---

**Tuples**, which rhyme with "pupils" or "couples", depending on who you ask, are similar to lists and are enclosed in parentheses `()`. Tuples are _iterable_, like lists, meaning they have items in an indexed order that can be iterated (looped) through. The major difference between tuples and lists is that tuples are _immutable_, cannot be changed.

You can obtain items from a tuple by its index, as we did with lists:

```py
> colors_tuple = ("red", "green", "blue", "purple", "orange")
> colors_tuple[3] = "purple"
```

#### But we can't reassign values because tuples cannot be changed.

## Unpack tuples by assigning each value to a variable

```py
>>> length, width, height = (2, 4, 10)
# assign values to variables all at once
>>> length
2
>>> width
4
>>> height
10
```

---

**Dictionaries** are key: value pairs, Python's version of the concept of _hash tables_. As with Webster's Dictionary, where you look up definitions by the word, you can look up values by their keys in Python dictionaries. Dictionaries in Python are similar to objects in JS. Keys and values can be almost any data type, except: _keys can only appear once in a dictionary, and keys must be of an immutable type (no lists or dictionaries)_. Values can repeat any number of times in a dictionary and can be of any type. Note that dictionaries _do not_ have indexes. They do (as of version 3.6) retain the order that items were inserted, but we don't use indexes to retrieve or update information.

```py
	foo_fighters = {
		"Dave Grohl": ("guitar", "lead vocals"),
		"Pat Smear": "guitar",
		"Chris Shiflett": ("guitar", "backing vocals"),
		"Nate Mendel": "bass",
		"Taylor Hawkins": ("drums", "percussion", "backing vocals"),
		"Rami Jaffee": ("keyboard", "piano"),
		}
# to obtain what Dave Grohl plays in Foo Fighters (now, not the first album where he played everything), we can use the key to find the value.
> foo_fighters["Dave Grohl"]
> ('guitar', 'lead vocals')
# if we want to update a dictionary, as in the case where the young drumming prodigy Nandi Bushell, who owned Dave Grohl in an Internet drum battle, joins the band as another drummer, we add key:value pairs to a dictionary by assigning a value to the new key.
> foo_fighters["Nandi Bushell"] = "more awesome drums"
# our dictionary has been updated
> foo_fighters
> {
	"Dave Grohl": ("guitar", "lead vocals"),
	"Pat Smear": "guitar",
	"Chris Shiflett": ("guitar", "backing vocals"),
	"Nate Mendel": "bass",
	"Taylor Hawkins": ("drums", "percussion", "backing vocals"),
	"Rami Jaffee": ("keyboard", "piano"),
	"Nandi Bushell": "more awesome drums",
}
# Let's say it's a magical world where Taylor Hawkins lives out a long and luxurious retirement and Nandi takes over for him entirely:
> foo_fighters["Taylor Hawkins"] = "retired"
# Now our dictionary shows his new status
> foo_fighters
> {
	"Dave Grohl": ("guitar", "lead vocals"),
	"Pat Smear": "guitar",
	"Chris Shiflett": ("guitar", "backing vocals"),
	"Nate Mendel": "bass",
	"Taylor Hawkins": "retired",
	"Rami Jaffee": ("keyboard", "piano"),
	"Nandi Bushell": "more awesome drums",
}
```

---

## Obtain values by their keys, NOT their position

You have to use square brackets enclosing a string to retrieve values by their key. Dot notation will not work like it does in JS.

```py
>>> fruit_amounts = {
'apples': 3,
'peaches': 6
'pears': 2
}

>>> fruit_amounts['apples']
3
>>> fruit_amounts.apples # ⛔ NOPE! This won't work!
```

### You can also obtain a value from a dictionary using `get()

```py
fruit_amounts.get('apples') = 3
# get() will return a default value if it can't find the key it's looking for, whereas the [] notation will just error if it can't find the key. Unless you specify otherwise, that default value is None
fruit_amounts.get('mango') = None
```

---

Lists, dictionaries, and tuples are **iterable**, meaning we can loop through them, performing tasks on each item one at a time. If we are looping through a dictionary, we have to decide whether we want to loop through the `keys()`, `values()`, or `items()`. The `if` statement will catch the member of the group who does not play an instrument anymore. `items()` gives us each key:value pair as a tuple, and we can access the items in that tuple by index.

```py
	for person in foo_fighters.items():
		if person[1] != "retired":
			print(f'{person[0]} plays {person[1]}')
```

---
