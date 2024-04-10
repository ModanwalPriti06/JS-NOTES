# JavaScript-Notes
Basic Javascript notes for beginners


# Pipe aand debouncng and generator

## How to Start
1. Create new repo and add README file.
2. click on code button code > codespace > click
3. take sometime then click file > view > command Plette.
4. search container then click > first Add Dev Container and configuration.
5. crete new configuration click
6. then again search nodejs for javascript and click on and do all few step.
7. Rebuild and m/n will start again wait few min.

## String Interpolation: 
The ability to substitute part of the string for the values of variables or expressions. This feature is also called string interpolation.
## HTML escaping:
The ability to transform a string so that it is safe to include in HTML.
## JavaScript Computed Property
ES6 allows you to use an expression in brackets []. It’ll then use the result of the expression as the property name of an object. For example:
```
let propName = 'c';
const rank = {
  a: 1,
  b: 2,
  [propName]: 3,
};
console.log(rank.c); // 3
```
### When You Should Not Use Arrow Functions
An arrow function doesn’t have its own this value and the arguments object. Therefore, you should not use it as an event handler, a method of an object literal, a prototype method, or when you have a function that uses the arguments object.

### for.. of VS for.. in Loop
```
// Array Iteration

const arr = [4,5,6,7,8];

for(let i of arr){
  console.log("of loop",i)
}
for(let i in arr){
  console.log("in loop",arr[i])
}

// Object Iteration

const person = {
  name: 'john doe',
  age: 24,
  Id: 101123
}

for (let [key,value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}

for (let key of Object.keys(person)) {
  console.log(`${key}: ${person[key]}`);
}

for (let [key,value] of Object.values(person)) {
  console.log(`Value is: ${value}`);
} 


for (let res in person){
    console.log("key is: ",res);
    console.log("value is: ",person[res]);
    console.log(`${res}: ${person[res]}`)
}
```
## JavaScript Generators
In JavaScript, a regular function is executed based on the run-to-completion model. It cannot pause midway and then continues from where it paused.
A generator can pause midway and then continues from where it paused. For example:

```
function* generate() {
    console.log('invoked 1st time');
    yield 1;
    console.log('invoked 2nd time');
    yield 2;
}
let gen = generate();
console.log(gen);

o/p:  Object [Generator] {}
```
- First, you see the asterisk (*) after the function keyword. The asterisk denotes that the generate() is a generator, not a normal function.
- Second, the yield statement returns a value and pauses the execution of the function.

So, a generator returns a Generator object without executing its body when it is invoked.
The Generator object returns another object with two properties: done and value. In other words, a Generator object is iterable.
The following calls the next() method on the Generator object:
```
let result = gen.next();
console.log(result);
```
- Generators are created by the generator function function* f(){}.
- Generators do not execute its body immediately when they are invoked.
- Generators can pause midway and resumes their executions where they were paused. The yield statement pauses the execution of a generator and returns a value.
- Generators are iterable so you can use them with the for...of loop.

## Array extensions
- Array.of() – improve array creation.
- Array.from() – create arrays from array-like or iterable objects.
- Array find() – find an element in an array
- Array findIndex() – find the index of an element in an array.

when you pass a number to the Array constructor, JavaScript creates an array whose length equals the number. For example:
```
let numbers = new Array(2);
console.log(numbers.length); // 2
console.log(numbers[0]); // undefined
```
owever, when you pass to the Array constructor a value that is not a number, JavaScript creates an array that contains one element with that value. For example:
```
numbers = new Array("2");
console.log(numbers.length); // 1
console.log(numbers[0]); // "2"
```
### Array.of()
  the Array.of() method always creates an array that contains the values that you pass to it regardless of the types or the number of arguments.
  ```
  let numbers = Array.of(3);
  console.log(numbers.length); // 1
  console.log(numbers[0]); // 3
  ```
  ```
  let chars = Array.of('A', 'B', 'C');
  console.log(chars.length); // 3
  console.log(chars); // ['A','B','C']
  ```
### Array.from()
Array.from() method that creates a new instance of the Array from an array-like or iterable object. The following illustrates the syntax of the Array.from() method:
```Array.from(target [, mapFn[, thisArg]])```
- target is an array-like or iterable object to convert to an array.
- mapFn is the map function to call on every element of the array
- thisArg is the this value when executing the mapFn function.
  
The Array.from() returns a new instance of Array that contains all elements of the target object.
```
function arrayFromArgs() {
    return Array.from(arguments);
}
console.log(arrayFromArgs(1, 'A'));
```
# JAVASCRIPT FUNCTION
## JavaScript Functions are First-Class Citizens
- Storing functions in variables is first class citizen. In other words, you can treat functions like values of other types.
  ```
  function add(a, b) {
    return a + b;
  }
  let sum = add; 
```

# JAVASCRIPT OBJECTS
## Object Method:
- When a function is a property of an object, it becomes a method.
## JavaScript Constructor Function
- JavaScript constructor function is a regular function used to create multiple similar objects.
- The name of a constructor function starts with a capital letter like Person.
- A constructor function should be called only with the new operator.
- you can call a constructor function like a regular function without using the new keyword.
- If return is called with an object, the constructor function returns that object instead of this.
- If return is called with a value other than an object, it is ignored.
      
 ```
function Person(name, age) {
    this.name = name;
    this.age = age;
    
    // If return is called with an object, it returns that object
    if (age < 18) {
        return { isMinor: true }; // Returning an object
    }

    // If return is called with a value other than an object, it is ignored
    return age; // This return statement is ignored
}

const p1 = new Person('John', 25);
console.log(p1); // Output: Person { name: 'John', age: 25 }

const p2 = new Person('Alice', 16);
console.log(p2); // Output: { isMinor: true }

```
## JavaScript Prototype
- In JavaScript, objects can inherit features from one another via prototypes. Every object has its own property called a prototype.
- The Object() function has a property called prototype that references a Object.prototype object.
- The Object.prototype object has all properties and methods which are available in all objects such as toString() and valueOf()
- However, if you access a property that doesn’t exist in an object, the JavaScript engine will search in the prototype of the object.

### JavaScript prototype illustration
- JavaScript has the built-in Object() function. The typeof operator returns 'function' if you pass the Object function to it.
  ``` typeof(Object) //output: 'function' ```
<span style="color:red"> Please note that Object() is a function, not an object. <span>
   
### Getting prototype linkage
- The __proto__ is pronounced as dunder proto. The __proto__ is an accessor property of the Object.prototype object.
- Every function has a prototype object. This prototype object references the Object.prototype object via [[prototype]] linkage or __proto__ property.

### Shadowing
In JavaScript, "shadowing" refers to the situation where a variable declared in a local scope has the same name as a variable in an outer scope. This.








