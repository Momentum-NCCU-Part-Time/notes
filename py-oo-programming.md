# Object Oriented Programming with Python - 

## Representing real world objects, behavior, and interactions with code
---
# Principles of Object Oriented Programming

- Abstraction: internal implementation details hidden
- Encapsulation: related data and behaviors grouped together
- Inheritance: class inherits attributes and behavior from parent class
- Polymorphism: it can assume many forms!

---

Classes in Python (nouns)

```py
class Pet:
    def __init__(self, name, species):
	# attributes represent qualities & characteristics
        self.name = name
        self.species = species 

nutmeg = Pet(name='Nutmeg', species='dog') 	
pet_data = [("Derbs", "cat"), ("Zeke", "dog"), ("Valvano", "dog")]
pets = []
for name, species in pet_data:
    new_pet = Pet(name=name, species=species)
    pets.append(new_pet)

```
Methods (verbs)

```py
# behaviors of the class
def call(self):
    print(f'Come here, {self.name}')
```	
