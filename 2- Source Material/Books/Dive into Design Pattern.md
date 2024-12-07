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
#### 1. Abstraction
- Is a model of real-world object or phenomenon limited to specific context:
	- Represent relevant detail of that context
	- Omit all other
#### 2. Encapsulation
- Ability to hide all parts inside an object, only expose limited interfaces for the others to use
- For example: to start a car:
	- you only need to put the key in, then press a button
	- no need to care about how the wires/gears are connected
- -> That's why the interfaces only declare methods. not attributes
#### 3. Inheritance
- Is ability to build a class based on an existing one
- Main purpose is reusability
#### 4. Polymorphism
- Animals defined "make_sound" behavious, but "make_sound" of cat is different from "make_sound" of dog
- Polymorphism: ability to pretend to be another class
### Relation between Objects
#### 1. Dependency
- Key: <mark style="background: #BBFABBA6;">Changes -> Changes</mark>
- Most ==basic== and ==weakest== type of relation
- Dependency = If ==some classes' definition changed== => ==lead to other classes== modification 

> [!info] Definition includes:
> - Fields/methods name
> - Methods' required parameters list


- For example: when specify type for variables/parameters/methods return/...
- To reduce dependency => depend on abstract/interface classes
#### 2. Association
- Key: <mark style="background: #BBFABBA6;">Use/Interact</mark>
- When a class uses or interact with others
- 2-ways interacts are possible
- Representation of association:
	- Most general: ==A field contains== other object
	- A ==method that return== object
- ==Interfaces cannot be associated== with other interface <- interfaces have no fields
#### Example of Dependency and Association
```ts

class Professor:
	student: Student;

	teach(course: Course) {
		this.student.remember(course.getKnowledge());
	}

```
- If the Course's `getKnowledge()` signature changed => `teach()` method will break => `Professor` depends on `Course`
- Similar, `Professor` also depends on `Student`
- But student could be used in any method of `Professor` => `Student` also associate with `Professor`
#### 3. Aggregation
- Key: <mark style="background: #BBFABBA6;">Contain</mark>
- Is specialized type of association
- Represent =="one-to-many"==, =="many-to-many"== or =="whole-part"== relation
- An object serves as a container/collection that contain set of others objects
- Examples: 
	- company has employees
	- club has members, each member could belong to many clubs
	- car has tires
#### 4. Composition
- Is specific type of aggregation
- When an object are composed by others objects (components)
- Components only exist as a part of container
- Example:
	- Company includes departments
#### Overall picture
- Association = Dependency + Use/Interact
- Aggregation = Association + Contain
- Composition = Aggregation + Only a part of
![[Dive into Design Pattern 2024-12-02 21.39.16.excalidraw]]
# Introduction to Patterns
- Design pattern is a ==customizable blueprint== of solution for commonly problem
- Pattern is ==not copiable code==, but is a general ==concept of solving problem==
- Pattern vs Algorithm:
	- Algorithm contains specific steps to be take, Pattern is a high-level of description for solution
	- Algorithm is like recipe (need to follow each step) , Pattern is like blueprint (order of implement is not important)
## Components of a Design Pattern
- **Intent**: quick describe of both problem and solution
- **Motivation**: Further explain the problem and solution
- **Structure**: classes that be parts of pattern and how they are related
- **Code example**: using popular programing language
![[Dive into Design Pattern 2024-12-07 14.35.39.excalidraw]]
## Classification of Patterns
- Patterns could be differed by:
	- Complexity
	- Level of detail
	- Scale of applicability
	- Intent:
		- Creation Pattern: define object creation mechanism that increase the reusability and flexibility
		- Structural Pattern: explain how to assemble objects into larger structure
		- Behavioral Pattern: define the object communication and assign responsibility for objects
# Software design principles
## Features of good design
### Reusability
- Is the most common way to reduce development time
- What reduce code reuse?
	- Tight coupling
	- Dependency on concreated classes (instead of interface)
	- Hardcode
- 3 levels of code reuse
	- Level1: Classes reuse
		- Like libraries
		- Only reuse in specific programing language
	- Level 3: Framework
		- Pre-define all the abstraction things
		- Only need to sub-class somewhere to define custom behaviors
		- Most risk and effort to make
	- Level 2: Patterns
		- In the middle of those 2 levels
### Extensibility
- Changes are inevitable in programming
## Design Principles
### 1. Encapsulated what varied

> [!info] Identify what is the varied parts and separate them from the stable ones

- Main goal: minified the effect of changed part to the stable part
#### On method-level
- Origin `getOrderValue()`:
```js
function getOrderValue(order) {
	let total = order.lineItems.reduce((item) => item.value);
	
	if (order.country === "US") total *= 1.1;
	else if (order.country === "VI") total *= 1.05;

	return total;
}
```
- <mark style="background: #FFB8EBA6;">Problem</mark>: when want to change the way of tax rate retrieve (not the way  of calculating original value) => still need to update the function
- <mark style="background: #BBFABBA6;">Solution</mark>: encapsulate tax retrieve logic to a function
```js
function getOrderValue(order) {
	let total = order.lineItems.reduce((item) => item.value);
	
	total *= (1 + getTaxRate(order.country))

	return total;
}

function getTaxRate(country) {
	return {
		"US": 0.1,
		"VI": 0.05
	}[country]
}

```

#### On class-level
- Over time, when add more responsibility to a method => Need more helper fields and method for it => Blur the meaning of original one => It's time to separate it to classes
- Before:
	![[Pasted image 20241207164152.png]]
- After: tax calculate logic is hidden from Order
	![[Pasted image 20241207164212.png]]
### 2. Interface, not Implementation

> [!info] Program to an Interface, not an Implementation. Depends on abstractions, not concrete class

- Concrete vs Abstract:
	- Concrete class: class that could be directly create instances from it
	- Abstract class: class that only contain only defines methods and properties, not leave anything for child classes to implement
- How to? When make a class depend on another:
	- Define the ==exact thing== that the class 1 need from the other
	- Extract that exact thing to an abstract class/ interface
	- Let class 1 use the created abstract class/interface
	- Create a new class that implement that abstract class/interface
- Example:
![[Pasted image 20241207172418.png]]
- More example:
	- Before: Company is tightly coupled to Designer, Programmer and Tester
		![[Pasted image 20241207174000.png]]
	- Better: Polymorphism help to make Company only depend on the Employee -> Still not good enough, when create new company with other type of Employee -> need to rework on the logic
		![[Pasted image 20241207174037.png]]
	- After: make the `getEmployees()` as abstract
		![[Pasted image 20241207174923.png]]

### Composition over Inheritance
- Inheritance is the easiest wat to reuse code, but problem will appear when there are a lot of classes:
	- **Redundant code**: Sub class cannot reduce the interface of parent: still need define even if not use
	- **Risk of break when override**: When override method of child -> Need to ensure new thing compatible with existing ones (For example: when update what a cat `eat()` -> need make sure the cat  can `digest()` it)
	- **Encapsulation broke**: Inheritance break the encapsulation of parent (children still can access to props/methods of parent, and vice versa)
	- **Tightly coupled**: changes in parent may break the sub classes
	- Create parallel hierarchy when there're 2+ dimension
- Composition: "has a" (instead of "is a" of Inheritance)
- Also apply to aggregation (contain but not maintain the life cycle more relaxed way of composition)
- 



---