2024-11-22 11:21

Tags: [[Typescript]]

---

# Basics
## Static Typing
```ts
const num: number = 1;
const str:string = "string";
```
## Type annotations
```ts
function func(field1:number, field2: string): boolean {
	return true
}
```
## Interface
```ts
interface Person {
	name: string;
	age: number;
}

const somePerson: Person = {
	name: "Nam",
	age: 25
} 
```
## Union type
- Type A or Type B
```ts
function printId(id: string | number): void { 
	console.log(`Your ID is: ${id}`); 
}
```
## Array/Tuple
```ts
// array
let colors: string[] = ["red", "green", "blue"];

// tuple
let personInfo: [string, number] = ["John", 25, 26, "Name"];
```
## Enums
```ts
enum Direction { 
	Up = 1, 
	Down, 
	Left, 
	Right 
};

let move: Direction = Direction.Up;
```
## Type 
- Give type new name
```ts
type StringOrNumber = string | number;
```
## Function overloading
- make 
```ts
function add(a: number, b: number): number; 
function add(a: string, b: string): string; 
function add(a: any, b: any): any {
	return a + b; 
}
```
## OOP support
```ts
class Animal {
  // access modifiers (private/public/protected)
  private name: string;

  constructor(name: string) {
    this.name = name;
  }

  getName(): string {
    return this.name;
  }
}

const dog = new Animal("Buddy");
console.log(dog.getName());  // "Buddy"

// Abstract class
abstract class Shape {
  abstract getArea(): number;
}

class Circle extends Shape {
  constructor(public radius: number) {
    super();
  }

  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
}


```
## Type Assertion
- Tell TS with is the variable type is
```ts
let someValue: any = "Hello, TypeScript!";
let strLength: number = (someValue as string).length; // Assert type as string
```
# Advanced
## Generics
- Dynamic types
```ts

function identity<T>(value: T): T {
  return value;
}

let stringValue = identity("Hello");  // T is inferred as string
let numberValue = identity(42);       // T is inferred as number


```
## Mapped Types
- Create new type from transform fields in existing type
``` ts
type ReadOnly<T> = {
  readonly [P in keyof T]: T[P];
};

interface Person {
  name: string;
  age: number;
}

const person: ReadOnly<Person> = {
  name: "Alice",
  age: 30
};

```
## Conditional Types
```ts
type IsString<T> = T extends string ? "Yes" : "No";

type Test1 = IsString<string>; // "Yes"
type Test2 = IsString<number>; // "No"

```
## Intersection Types
- Join 2 types
```ts
interface Person {
  name: string;
  age: number;
}

interface Contact {
  email: string;
  phone: string;
}

type PersonWithContact = Person & Contact;

const person: PersonWithContact = {
  name: "Alice",
  age: 30,
  email: "alice@example.com",
  phone: "123-456-7890"
};

```


---
# References