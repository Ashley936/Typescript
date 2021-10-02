# Typescript = Javascript + type system

> Typescript compiler changes ts to Js
> Ts analyze our code for errors

## Steps to set up ts

1. npm install -g typescript ts-node
2. We get access to 'tsc' command

### First small app (basic intro)

1. install axios
2. create an 'index.ts' file
3. make an axios request to jsonplaceholder api for fake data
4. to execute we have 2 ways: tsc index.ts and then node index.ts or ts-node index.ts
5. Now some ways to catch error using typescript:

```Javascript
// interface are used to define types
interface Todo {
    id: number;
    title: string;
    finished: boolean;
    isLogedin(): boolean;
}
const var = res.data as Todo; // makes var as a typescript interface i.e. defines a structure for var.
```

## Basic types in TS

types are labels to that are used to tell about it's methods and properties.

1. Primitive types

2. Object Types

## Type Annotations + Type Inference

> ### _Type Annotations_ : code **we** add to tell ts what type of value a var will refer to

### Syntax

1. primitive data types: const var_name: number;
2. Arrays:

```Javascript
const arr: string[] = []; //always attonate empty arrays
//2 D Arrays
const arr: string[][] = [];
// Flexible types
const arr: (string | Date)[] = []
```

3. Classes:

```Javascript
const data: Date = new Date();
```

4. Object literal:

```Javascript
    let obj: {key1: string; key2: number} = {key1: "hello", key2: 16};
    // OR   (DESTRUCTURING)
    const profile = {age: 18, name: "Harry"}
    const {age}: {age: number}=profile
    //OR    
    const {coords: {lat, lon}}: {coords:{lat: number, long: number}} = location
```

5. Fuctions: Type inference can work out the return type but as best practices we shouldn't use it.

```Javascript
    const function = (arg: number) => void = (arg: number) => {/* Code */}
    //OR
    const function = (arg: number, arg2: string): void => {/* Code */}
    //OR
    function fun(arg: number): number{/* code with return num; */}
    //OR
    function fun(): never{new throw error()};
    //OR    (DESTRUCTURING)
    funtion fun({a, b}: {a: number, b: string}): void{/* code */}
```

> ### _Type Inference_ : **Ts** tries to figure out what type of value a variable has
>
> > If declaration and initialization are in the same place typescript will figure out the type for us

We should use type annotations when:

1. A function return type "any"
   example: with JSON.parse()
   solution: 
            const res:{user: string; age: number}  = JSON.parse(json);

2. when we declare and initialize var in the different place
   example: const var_name: number;

3. Variable whose type cannot be inferred
    exapmle: const favBooks = newBook === "Fantasy" ? newBook : null;
    solution: const favBooks: null | string

## TUPLES

An array like structure with elements in fixed order

```Javascript
    type Drink = [number, boolean, string];
    const cola: Drink = [18, true, "cola"];
```

## INTERFACES

Creates a new type, describe the properties and value types of an object.
An obj can be of an interface type if it satisfies the interface structure and it does not matter if it has more properties.
We can use a single interface to classify very different objects and then use it in some generic function as arguments.
Thus making the function and interfaces reusable. 

## Classes

Blueprint to create an object with some fields(values) and methods(functions) to represents a 'thing'


Interface is used to check an already created object or while creating an object
Class is used to make an object with the same values and methods inside the class