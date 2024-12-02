Source link: 

Status: #source-eating 

---

# Introduction to OOP
## Basics of OOP
- Is a paramigm
- Based on concept of wrapping pieces of data and behaviors related to those data into 1 thing called Object
![[Dive into Design Pattern 2024-12-01 15.57.03.excalidraw]]
- Objects are constructed from a set of blueprints called Classes
![[Dive into Design Pattern 2024-12-01 20.22.20.excalidraw]]
### Objects & Classes
- A class can be used to create multiple object
- Example: Cat class could be blueprints for Tom cat, Garfield cat, they both have:
	- Attributes (States): name, gender, age, weight,..
	- Behaviours (Methods): Eat, run, meow,...
![[Dive into Design Pattern 2024-12-01 20.38.48.excalidraw]]
### Classes hierarchies
- When 2 or more ==classes== have some ==same attributes/methods==, we can define a parent class (called ==super class==) and it has children (==sub classes==) only need to define things that differ
![[Dive into Design Pattern 2024-12-01 20.44.28.excalidraw]]
- A class:
	- will have all attributes/methods of its descendants
	- can override the attributes/methods of its descendants
### Pillars of OOP
#### Abstraction
- Is a model of real-world object or phenomenon limited to specific context:
	- Represent relevant detail of that context
	- Omit all other
#### Encapsulation
- Ability to hide all parts inside an object, only expose limited interfaces for the others to use
- For example: to start a car:
	- you only need to put the key in, then press a button
	- no need to care about how the wires/gears are connected
- -> That's why the interfaces only declare methods. not attributes
#### Inheritance
- Is ability to build a class based on an existing one
- Main purpose is reusability
#### Polymorphism
- Animals defined "make_sound" behavious, but "make_sound" of cat is different from "make_sound" of dog
- Polymorphism: ability to pretend to be another class
### Relation between Objects

---