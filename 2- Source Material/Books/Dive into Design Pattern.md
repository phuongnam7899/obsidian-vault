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
	- Create **parallel hierarchy** when there're 2+ dimension
		![[Pasted image 20241207184951.png]]
- Composition: "has a" (instead of "is a" of Inheritance)
- Also apply to aggregation (contain but not maintain the life cycle more relaxed way of composition)
- Example:
![[Pasted image 20241207185326.png]]
## SOLID Principles
- Principles to make software design flexible, understandable and maintainable

>[!warning] Don't use them mindlessly -> Cost of applying is make code more complex than it should

### 1. Single Responsibility

> [!info] A class should have only ONE reason to change

- When a class grow over time -> it become too hard to remember the detail -> need top scan over the class/file to find something
- When a class does many things -> need to change it even when you want to change only one thing -> risk of break other things
- Example:
	- Before: when the report printing format change -> need to update the Employee
		![[Pasted image 20241208151642.png]]
	- After: Move to other class
		![[Pasted image 20241208151657.png]]
### 2. Open-closing

> [!info] Classes should be open for extend but closed for modification

- Main idea: ==avoid breaking== when add new features
- Open = ==Extendable== = Can create subclass from it and add new fields/methods or override
- Closed = ==100% ready to be used== by the other -> avoid modify -> extend instead
- 
![[Dive into Design Pattern 2024-12-08 15.26.06.excalidraw]]

- A class ==could be both open== (for extend) ==and closed== (for modify) at ==the same time==
- <mark style="background: #FFB8EBA6;">DON'T apply</mark> this principle <mark style="background: #FFB8EBA6;">for bug fix</mark>
- Example:
	- Before: when new shipping type appear -> need to update the Order (not closed for modification) 
		![[Pasted image 20241208155034.png]]
	- After: apply Strategy pattern -> when new shipping apprear -> just add new class that extend Shipping -> open for extend
		![[Pasted image 20241208155245.png]]
### Liskov Substitution

> [!info] When extending a class, make sure that we can put the subclass in place of parent without any issue

- Subclass should only extend, not create many different things
- Specially important in developing libraries/framework because they're used in many place
- Checklist
	- 1. ==Parameter of methods== of subclass should be ==same or more abstract== than superclass
	- 2. ==Return type of methods== of subclass should be ==same or subtype== of those in superclass
	- 3. ==Type of exception== thrown by subclass should be ==same or subtype== of those  from superclass
	- 4. Subclass ==shouldn't strengthen the pre-condition==
		- For example: Parent say param be int, but subclass say it should be positive
	- 5. Subclass ==shouldn't weaken the post-condition==
		- For example: Parent close the connection before end method, subclass does not
	- 6. ==Invariants== of parent ==should be preserved==
		- Example: Cat's subclasses should be meow -able
	- 7. Subclass should ==not change private values of parent==
- Example:
	- Before: Violate 3,5 
		![[Pasted image 20241208204514.png]]
	- After:
		![[Pasted image 20241208204618.png]]

### Interface Segregation

> [!info] Clients shouldn't be forced to depend on methods they not use

- Example:
	- Before: some methods of `CloudProvider` are not implemented in `Dropbox`
		![[Pasted image 20241209164322.png]]
	- After:
		![[Pasted image 20241209164522.png]]
> [!warning] Do not overdo it, stop divide when the interface is specific enough

### Dependency Inversion

> [!info] High-level classes should not depend on low-level ones. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions

- Low-level classes: implement basic operation (working with file, disk, connecting to database, send requests,...)
- High-level classes: contain complex business logic -> use low-level classes
- Normally: Design low-level then High level classes -> high level tend to depend on the low-level
- This principle suggest change the direction:
	- First, describe ==interfaces== ==for low-level== operation in business term (`openReport` instead of `openFile` + `readBytes` + `closeFile`)
	- Then, ==make high-level classes== depend on interface -> softer than concrete low-level ones
	- Then, ==implement the low-level== classes that implement the interfaces
- Example:
	- Before: when low-level changed -> high-level might break
		![[Pasted image 20241209171013.png]]
	- After: Easily change/extend/create new the low-level classes -> Low-level classes depend on high-level abstractions
		![[Pasted image 20241209171115.png]]

# Catalog of Design Pattern

## Creational Patterns

> [!info] Patterns that provide object creation mechanism

### 1. Factory Method (Virtual Constructor)

> [!info] Provide interface for creating objects in a superclass. but allows subclass to alter the type of objects that created

#### Problem
![[Pasted image 20241210093907.png]]
- If many other parts of code coupled to `Truck` class, it will be hard to add `Ship` into the app
#### Solution
- Replace direct object construction calls with calls to Factory method

### 2. Abstract Factory

> [!!info] Let you produce families of related objects without specifying their concrete classes

### 3. Builder

> [!info] To construct complex object step by step. Allow produce diferrent types and representations of an object using the same construction code

### 4. Prototype

> [!info] Let you copy the existing objects without making code depend on their class

### 5. Singleton

> [!info] Make sure that a class has only one instance, and provide global access point to the instance















---