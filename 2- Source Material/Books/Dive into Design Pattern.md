Source link: 

Status: #source-eating 

---

# Introduction to OOP
## Basics of OOP
- Is a paradigm
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
- Polymorphism: give an object the ability to pretend to be another class (its parent or abstract/interface)
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

### 3. Composition over Inheritance
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

> [!i] Patterns that provide object creation mechanism

### 1. Factory Method (Virtual Constructor)
![[Pasted image 20241228111018.png]]

> [!info] Provide interface for creating objects in a superclass. but allows subclass to alter the type of objects that created

#### Problem
![[Pasted image 20241210093907.png]]
- If many other parts of code coupled to `Truck` class, it will be hard to add `Ship` into the app
#### Solution
- Replace direct object construction calls with calls to Factory method
![[Pasted image 20241210104632.png]]
- -> Allow subclass to override the `createTransport()`

- Limitation: subclasses may return different types of product only if the products have common base class/interface
![[Pasted image 20241210111212.png]]
- Client (the code that use the product created by factory) will only know that there is a method `deliver()` but not need to know the logic of `deliver()` 
#### Structure

![[Pasted image 20241210112342.png]]
- **Product**: ==interface== that ==common to all object created== by the creator (and its subclasses)
- **Concrete products**: ==different== ==implementation== of Product
- **Creator**: ==contain the factory method== that return new Product
	- Return type of factory method should match the product interface
	- Could declare the factory method to be abstract, or return default value
	- Creator could also contain other logic related to the products
- **Concrete Creator**: ==override the factory method== of superclass
	- Factory method doesn't need to create new instance all time, it could return existing object also
#### Applicability
- When ==don't know beforehand== the exact ==types and dependencies== of the objects that the code should work with
- When want to ==provide== ==library/framework users== with ==a way to extend== the internal components
- When want to save resource by ==reusing existing objects== instead of rebuild
#### How to Implement
1. Make ==all  products== ==follow a interface== (that make sense to every product)
2. Add empty factory method to creator class -> return type match the interface created in (1)
3. Replace all product constructor of Creator by the factory method calls (can ==add a temp param== to control the type of returned product)
4. ==Create a set of subclasses== for each type of product created in (3) -> override the factory methods
5. (Optional) If there're too many product types -> reuse the control param created in (3)
6. After all, if the factory method:
	1. become empty -> make it abstract
	2. still has something left -> make it default behavior
#### Pros & Cons
- Pros:
	- <mark style="background: #BBFABBA6;">Avoid tight coupling</mark> between creator and thew concrete products 
	- Applied <mark style="background: #BBFABBA6;">Single Responsibility</mark> Principle (creation code moved to one place)
	- <mark style="background: #BBFABBA6;">Open/Closed</mark> principle: open to extend new product types
- Cons:
	- There might be <mark style="background: #FFB8EBA6;">a lot of subclasses</mark> (of product and creator) -> more complicated code
#### Relation with other Patterns
- Factory method can ==evolve== to ==Abstract Factory, Prototype or Builder==
- Can ==use== Factory Method ==along with== ==Iterator== -> let collection subclasses return different iterator types that compatible with collection
- Factory method may ==serve as a step== in ==Template Method==

### 2. Abstract Factory
![[Pasted image 20241228111100.png]]

> [!!info] Let you produce families of related objects without specifying their concrete classes

#### Problem
- You have a **set of related objects** (family) that have **multiple themes/variants**
![[Pasted image 20241211115857.png]]
- You don't want to update code when adding new product or new theme  
#### Solution
- Step 1: Explicitly ==declare interface== for each product of family -> ==make all variants== of product following that interface
![[Pasted image 20241221085754.png]]
- Step 2: Declare the Abstract factory - ==interface with list of creation methods== for products. The return of those methods must be the abstract declared in step 1
- Step 3: For each variant, create a class that implement the  Abstract Factory 
![[Pasted image 20241221090508.png]]
#### Structure
![[Pasted image 20241221091826.png]]
Example:
![[Pasted image 20241228101419.png]]
#### Applicability
- When you have ==multiple families== of ==related products==
- When you have class that have ==many factory method==
#### How to Implement
![[Pasted image 20241221091826.png]]
- ==Map out the product types and variants==
- Declare ==interface for all product types== -> make ==concrete classes== implement those interfaces
- Declare the ==interface of Abstract factory== that have factory methods that create each product types
- Declare the ==concrete factories for each variant== that implement the Abstract Factory (only different at the return type of the factory methods)
- ==Use the concrete factory== in the code
#### Pros & Cons
- Pros:
	- Make sure all product created from a (concrete) factory is of same family/variant
	- Avoid tightly coupling between concrete product with client code
	- Single responsibility: extracted all products creation to 1 place
	- Open/Closed: Can create new variants without breaking client code
- Cons:
	- Code become more complicated
#### Relation with other Patterns
- Many design start with Factory Methods -> Evolve to Abstract Factory
- Abstract factory might be used as alternative for Facade when only want to hide the subsystem creation code
- Abstract factory might use along with Bridge (useful when some abstraction define by Bridge can only work with some specific implementation)
- Abstract Factory can be implemented as Singleton

### 3. Builder
![[Pasted image 20241228111118.png]]

> [!info] To construct complex object step by step. Allow produce diferrent types and representations of an object using the same construction code

#### Problem
- When you have objects that contain many fields, and even nested objects, there're 2 approach common used:
	- Create a based class then extend when you want to add new fields
		![[Pasted image 20241228141152.png]]
		- Create many classes
		- What if you want more than 1 fields added to the based class?
	- Create a huge class with many fields
		![[Pasted image 20241228141029.png]]
		- The constructor might be very complex
		- No all fields will need in all construct
#### Solution
- Builder pattern suggest to move all construction parts to a separate object called *builder* 
![[Pasted image 20241228144536.png]]
- Not necessary to call all steps, only call what you need
- Can create other builder to create different implementation of each step
	![[Pasted image 20241228155906.png]]
- Can even go further by extract the steps to another class called ==Director==
	- Director help us to store the construction routine
	 ![[Pasted image 20241228155950.png]]
#### Structure
![[Pasted image 20241228160150.png]]
- `Builder` declare all construction steps that are common for all builders
- `Concrete Builder` implement the `Builder` and may produce the products differently
- `Product` is result of  `Concrete Builder`, products from  different `COncrete Builder` do not need to belong to same origin
- `Director`: Contain the call order of steps in the building phase
- Client need to assign a builder to the Director (usually the Director only stick with one Builder, but it could be changed)
#### Applicability
- Use `Builder` to ==get rid of "telescoping constructor"== (overload the constructor of class to allow different ways to call the constructor)
- When want to create different representation of product that have same construction steps (like beef pizza and shrimp pizza)
- Use `Builder` to construct `Composite Tree` or other complex objects
#### How to Implement
- Clearly list down the steps need to take to build an object
- Create `Builder` interface that contain the ==definition of all possible steps==
- Create `Concrete Builder` from the `Builder` ==for each representation of product== and define logic in each step
> [!info] Remember to create method to get the final result of construction process (this method is not included in the `Builder` interface because different Concrete Builder might return different Product)
- Create Director class to hold all the call order of steps
- In client, create both Director and Concrete Builder -> Assign a Builder to a Director -> Start the build process
- Get the final result from Director (if all product follow same interface) or the Concrete Builder
#### Pros & Cons
- Pros:
	- ==Flexible in calling== the construct steps (step-by step, defer some steps or call recursively)
	- ==Reusable construction code== when create different representation
	- Single responsibility: the construction code from business logic
- Cons:
	- Create more classes -> Overall code complexity is increase
#### Relation with other Patterns
- Factory Method can evolve to Builder
- Builder is used to create complex `Composite Tree`
- Can combine Builder with Bridge: Director can play the role of abstraction, and different builders act as implementation
- Builder could be implemented as Singleton
### 4. Prototype
![[Pasted image 20241231090811.png]]

> [!info] Let you copy the existing objects without making code depend on their class

#### Problem
- You have an object, and want to create exact copy of it
- You might need to create a new object of same class -> get all properties of the root to copy to new one
> [!error] Problem
> - Not all objects could be copied that way (copy from outside) because some fields might be private
> - Your code is depend on the class (because you  need to know which class it is)
> - Sometimes you only know the interface, not the concrete class
 
#### Solution
- `Prototype` delegate the cloning process of an object
- It declare interface for all object that support cloning
- Usually only contain `clone` method
- Analogy: division of a cell
	- It's ==not process of copy from outside==
	- The origin cell is the one that clone itself
#### Structure
![[Pasted image 20241230095301.png]]
- Prototype interface, in most case, only declare the `clone()` method
- `Concrete Protorype` implement the clone methods + handle edge cases ()
- `Prototype Registry` provide easy way to access frequency used Prototype
![[Pasted image 20241230101353.png]]

#### Applicability
- Use when you don't want code depend on the concrete class when clone (only know that the class has `clone` method)
- When you want to ==reduce number of sub-classes with the only different in the initialization== of respective object
#### How to Implement
- Create a prototype interface with `clone()` inside
- Prototype should have an overload of constructor (beside normal one) to create new object with value of another instance
- Clone method usually only contain 1 line of `new` with all fields of `this`
	- Every class need to override the clone method to use its class name after `new`
- (Optional) Create a Prototype Registry to store catalog of frequently used prototype
#### Pros & Cons
- Pros:
	- Can clone <mark style="background: #BBFABBA6;">without depend on concrete</mark> class
	- <mark style="background: #BBFABBA6;">Get rid of repeated initialization code</mark> in favor of clone prebuilt prototype
	- Produce complex object faster
	- Could be <mark style="background: #BBFABBA6;">alternative way of inheritance</mark> when you want to have preset config for objects
- Cons:
	- Clone object with <mark style="background: #FFB8EBA6;">circular reference </mark>might be tricky
#### Relation with other Patterns
- Factory Method might evolve to Prototype
- Abstract factory often based on set of factory method , but also could use Prototype to compose the method
```python
class PrototypeShapeFactory(ShapeFactory):
    def __init__(self, circle_prototype, rectangle_prototype):
        self.circle_prototype = circle_prototype
        self.rectangle_prototype = rectangle_prototype

    def create_circle(self):
        return self.circle_prototype.clone()

    def create_rectangle(self):
        return self.rectangle_prototype.clone()
```
- Could be used top save copies of `Command` into history
- Design that use may of `Comnposite` and `Decorator` might benefit from `Prototype` (it helps quickly create objects)
- Sometimes 
### 5. Singleton

> [!info] Make sure that a class has only one instance, and provide global access point to the instance

![[Pasted image 20241231095530.png]]

#### Problem
- Ensure a class has only 1 instance: Why to control the number of instances? Most common reason is to ==control access for shared resources== (like files for databases)
- ==Provide a global access== point for that instance, and ==protect it from being overwritten==
#### Solution
- Make the constructor private -> prevent others to call it
- Create static creation method to:
	- act as constructor
	- use that  private constructor
	- save created object to a static field
	- Return cached object when called again
- Analogy: Government - one country only has one, anywhere, anyone when wan to refer to will reach it
#### Structure
![[Pasted image 20241231101608.png]]
- Singleton class contains:
	- static field for the instance
	- static `getInstance` method for instance creation/retrieve

>[!info] You can always change the limit of instance number if want

#### Applicability
- When there should be only one instance in application
- When want to strictly control the global variables

#### How to Implement
- Add static field in class to store the instance
- Make the constructor private
- Add static creation method:
	- Create new instance in first call -> save to static field in last step
	- Return created instance from the 2nd call
- Go to all client codes -> Change the constructor calls to static method created in last step
#### Pros & Cons
- Pros:
	- Make sure class has only one instance -> easy to manage
	- Make the instance globally accessible
- Cons:
	- Violates SRP: class serve 2 goals
	- Required special treatment in multi-thread 
	- Difficult to do unit test
#### Relation with other Patterns
- `Facade` could be transformed into Singleton (since in most case, a single Facade object is enough)
- `Flyweight` could be resemble to Singleton if you manage to reduce all shared state objects to one object. But 2 fundamental different:
	- Flyweight could have more than 1 instance
	- Singleton object could be mutable, Flyweight is not
- `Abstract Factory`, `Builder` and `Prototype` could be implemented as Singleton
## Structural Patterns

> [!i] Structural pattern explain how to assemble objects into larger structure
### 1. Adapter

![[Pasted image 20250102093132.png]]

> [!i] Allow object with incompatible interface to colaborate

#### Problem
- You are creating a stock analysis application
	- Data provider sends data in XML format and your core classes also use XML
	- One day you want to use an external library but it only accept JSON format
![[Pasted image 20250103133651.png]]
#### Solution
- Create an Adapter - an object that convert interface of other object so that others object can use/understand it
![[Pasted image 20250103134438.png]]
- Analogy: Wire adapter for laptop
![[Pasted image 20250103134659.png]]
#### Structure
##### Object Adapter
![[Pasted image 20250103134801.png]]
- Client Interface: Describe protocol that other classes must follow
- Service: class that do some helpful things (usually 3-party libs/ legacy code)
- Adapter: receive calls from client and translate it to calls to wrapped service
> [!i] Client code does not coupled to the concrete Adapter because it is working with Client Interface => You can create new types of Adapter without breaking existing code
##### Class Adapter
- Adapter inherits interfaces from both objects at the same time
> [!w] Only do-able in languages that support multi-inheritance
- It override the method of the class that Client is calling
![[Pasted image 20250103135836.png]]

#### Applicability
- When you want to use existing class but the interface is not compatible with your code => Adapter works as a translator
- When you want to reuse several subclasses but they do not have same functionality so that cannot be added into superclass, for example
```ts
// Step 1: Define a common interface
interface PaymentProcessor {
  processPayment(amount: number): void;
}

// Step 2: Create Adapter classes for each payment gateway
class PayPalAdapter implements PaymentProcessor {
  private paypal: PayPal;

  constructor(paypal: PayPal) {
    this.paypal = paypal;
  }

  processPayment(amount: number): void {
    this.paypal.makePayment(amount); // Adapts PayPal's method
  }
}

class StripeAdapter implements PaymentProcessor {
  private stripe: Stripe;

  constructor(stripe: Stripe) {
    this.stripe = stripe;
  }

  processPayment(amount: number): void {
    this.stripe.charge(amount); // Adapts Stripe's method
  }
}

class SquareAdapter implements PaymentProcessor {
  private square: Square;

  constructor(square: Square) {
    this.square = square;
  }

  processPayment(amount: number): void {
    this.square.pay(amount); // Adapts Square's method
  }
}

// Step 3: Existing payment gateway classes
class PayPal {
  makePayment(amount: number): void {
    console.log(`Paid $${amount} using PayPal.`);
  }
}

class Stripe {
  charge(amount: number): void {
    console.log(`Charged $${amount} using Stripe.`);
  }
}

class Square {
  pay(amount: number): void {
    console.log(`Processed $${amount} through Square.`);
  }
}

// Step 4: Usage
const paypal = new PayPalAdapter(new PayPal());
const stripe = new StripeAdapter(new Stripe());
const square = new SquareAdapter(new Square());

paypal.processPayment(100); // Output: Paid $100 using PayPal.
stripe.processPayment(200); // Output: Charged $200 using Stripe.
square

```
#### How to Implement
- Make sure you have different classes that interfaces are not compatible
	- 1 useful service class that you cannot or don't want to change
	- One or more client class that benefit from the service class
- Declare the client interface that define how client communicate with service
- Create adapter class that follow the client interface, leave the implementation empty now
- Add a field in adapter that contain the object of service object (the value might passes through constructor or when the method called)
- Implement all methods of the interface (focus on the conversion, not the real logic of service)
- Client use the adapter via Client interface
#### Pros & Cons
- Pros
	- SRP: the conversion code is isolated
	- OCP: can add new adapter without breaking client code
- Cons: Overall complexity is increased
#### Relation with other Patterns
- `Bridge` is designed up-front, Adapter is used with existing code
- Adapter create completely different interface, `Decorator` let it stay the same or extended, `Proxy` interface is the same
- `Facade`tries to define new interface,`Adapter` tries to make current interface usable
### 2. Bridge
![[Pasted image 20250103144347.png]]

> [!i] Let you split a large class or set of closely related class into 2 separate hierarchies: abstraction and implementation which can be developed independently from each other

#### Problem
- When add new Shape or Color -> create many classes
![[Pasted image 20250103151220.png]]
- => Problem happens when you want to scale the class in 2 different dimension (Form and color) (Often happen with inheritance)
#### Solution
- Switch from inheritance to composition: 
	- split one of dimension into another class hierarchy
	- the origin class will refer to it instead of all states and behaviors in 1 class
![[Pasted image 20250104094117.png]]

> [!i] Abstraction (interface) is a high-level control layer of an entity. It doesn't do any real work, just to delegate the work of implementation layer

![[Pasted image 20250104095010.png]]

#### Structure
![[Pasted image 20250104095340.png]]
- `Abstraction` provide ==high level control logic==, rely on the Implement to do real work
- `Implementation` provide ==common interface== for all concrete implementation (the Abstraction can only communicate with implement object method that declared here)
- `Concrete Implementation` contain ==platform specific== code
- `Refined abstraction` used to create different ==variants of control logic==
- `Client` usually ==call the Abstraction== only, but client need to ==link== between ==abstraction and implementation==
![[Pasted image 20250104103201.png]]
- Example:
	- 
![[Pasted image 20250104101031.png]]
#### Applicability
- When you want to ==divide== monolith class that has ==several variants of functionality== 
- When you  want to extend a class in several independent dimension (each dimension is separated into different class hierarchy)
- When you want to switch implementation at runtime
#### How to Implement
- Find out the independent dimensions, it could be:
	- Abstraction/platform
	- Domain/Infra
	- Front-end/Back-end
	- Interface/Implementation
- Define the base abstraction class with the operations that clients need
- Declare  operation that required in all platform -> Put it in a general implementation interface
- Create concrete implementation for each platform
- Inside abstraction class, define a field to refer the implementation
- (Optional) Create refined abstraction if you have variants of high level logic
- Client code should pass a implementation object to the abstraction to create association => After that, client only work with abstraction object
#### Pros & Cons
- Pros
	- Can create platform-independent classes/apps
	- Clients only work with high-level abstraction, no need to care about the implementation
	- Open/Closed: can create more abstraction or implementation without break current code
	- Single Responsibility: abstraction and implementation are separated
- Cons
	- Complicated code
#### Relation with other Patterns
- Bridge is created upfront, Adapter created to work with existing classes
- Bridge, State and Strategy have similar structure because they are all based on composition, but solve different problem
- Can use Abstract Factory along with Bridge. It's useful when some abstraction of Bridge only work with specific implementation
- Can combine Builder with Bridge: director class play the role of abstraction, while different builder are implementation
### 3. Composite (Object Tree)
![[Pasted image 20250105140247.png]]
> [!i] Let you compose objects into tree structures and then work with these structure as individual objects

#### Problem
- When you have an object which could be represented as a tree, and you want to do something related to multiple elements of it
![[Pasted image 20250105140711.png]]
- For example: when want to calculate total value of all item, it is not simple as do a loop
#### Solution
- Work with `Box` and `Product` with the same interface which declare method to calculate price => Run a behavior recursively over all components of the tree
![[Pasted image 20250105142013.png]]
- The benefit is that you won't need to care that a component is Box or Product, but still can treat them the same way
- Analogy: Military hierarchy
#### Structure
![[Pasted image 20250105142801.png]]
- The `Component` is interface that contains all common methods that could be used by both simple and complex elements in tree
- `Leaf` is the simple element, do not contain any sub element
- `Composite` (or Container): is element that contains sub element
- Client work with elements through `Component` interface
- Example:
![[Pasted image 20250105143352.png]]
#### Applicability
- When you have tree-like object structures
- When you want client treat simple and complex object similarly
#### How to Implement
- Declare the component interface that contains methods that simple and complex elements both have
- Create leaf classes for simple elements
- Create container class to represent complex elements:
	- Has array field to contain reference to sub items
	- Should be able to contain both leaf and other containers
	- Has methods to add and remove child elements

>[!i] The add/remove operation could be declared in the component interface (even if it break the Interface Segregation Principle)

#### Pros & Cons
- Pros:
	- Can work with complex tree structures more effectively: make use of polymorphism and recursion
	- OCP: Can create more elements types without breaking current code
- Cons:
	- Difficult to find common interface for classes. In some scenarios, you might need to over-generalize the interface -> harder to comprehend
#### Relation with other Patterns
- Can use Builder to create complex Composite tree because you can make the construction step recursively
```ts

const builder = new FileSystemBuilderImpl("root");

const fileSystem = builder
  .buildFolder("Documents")
    .buildFile("Resume.docx", 120)
    .buildFile("CoverLetter.docx", 90)
    .endFolder()
  .buildFolder("Pictures")
    .buildFolder("Vacation")
      .buildFile("Beach.png", 2048)
      .buildFile("Sunset.png", 1024)
      .endFolder()
    .endFolder()
  .buildFile("notes.txt", 45)
  .getResult();

fileSystem.display("");

```
- `Chain of Responsibility` is often used in conjunction with Composite: When a leaf get the request, it will pass through the parent -> down to the root
- Can use `Iteration` to traverse (travel through) the Composite tree
- Can use `Visitor` to do operation over the tree
- Can implement shared leaf node of composite tree as `Flyweights` to save some RAM
- Composite and Decorator have similar structure because both rely on the recursive composition
	- Decorator is composite with 1 child only
	- Decorator add responsibility to objects, while Composite just "sum up" its children results
- Design with heavy use of Composite gets benefit from Prototype to clone complex object without recreate it
### 4. Decorator
![[Pasted image 20250105152614.png]]
> [!i] Let you add more behaviors to an object by place it inside a special wrapper object that contains new behaviors

#### Problem
- Imagine working on notification library like this
![[Pasted image 20250108140754.png]]
- At  some point, you want to add more type of sender like email, slack,... You might update like this
![[Pasted image 20250108141327.png]]
- But what if you need to send through multiple channels at once? It should not be like this:
![[Pasted image 20250108141631.png]]
> [!w] Some points to aware about inheritance:
> - Inheritance is static - cannot alter the behavior of an object in runtime -> only be able to replace the object with another
> - Subclass can only have 1 parent class
#### Solution
#### Structure
#### Applicability
#### How to Implement
#### Pros & Cons
#### Relation with other Patterns
### 5. Facade
#### Problem
#### Solution
#### Structure
#### Applicability
#### How to Implement
#### Pros & Cons
#### Relation with other Patterns
### 6. Flyweight
#### Problem
#### Solution
#### Structure
#### Applicability
#### How to Implement
#### Pros & Cons
#### Relation with other Patterns
### 7. Proxy
#### Problem
#### Solution
#### Structure
#### Applicability
#### How to Implement
#### Pros & Cons
#### Relation with other Patterns


















---