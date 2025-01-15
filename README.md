# JavaScript-Notes
Basic Javascript notes for beginners


# Pipe and debouncng and generator

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

## JavaScript Prototypal Inheritance
JavaScript doesn’t use classical inheritance. Instead, it uses prototypal inheritance.In prototypal inheritance, an object “inherits” properties from another object via the prototype linkage.
- Inheritance allows an object to use the properties and methods of another object without duplicating the code.

```
let person = {
    name: "John Doe",
    greet: function () {
        return "Hi, I'm " + this.name;
    }
};
let teacher = {}
teacher.__proto__ = person;
console.log(teacher.greet());
```
## this keyword
In JavaScript, you can use the this keyword in the global and function contexts. Moreover, the behavior of the  this keyword changes between strict and non-strict modes.

### Global context
In the global context, the this references the global object, which is the window object on the web browser or global object on Node.js.
```
this.color= 'Red';
console.log(window.color); // 'Red'
```
### Function context

- Function invocation
- Method invocation
- Constructor invocation
- Indirect invocation

 #### 1) Simple function invocation
non-strict mode: 
```
function show() {
   console.log(this === window); // true
}

show();
```
strict mode:
```
"use strict";

function show() {
    console.log(this === undefined); //true
}

show();
```
#### 2) Method invocation
when you call a method without specifying its object, JavaScript sets this to the global object in non-strict mode and undefined in the strict mode.
```
let car = {
    brand: 'Honda',
    getBrand: function () {
        return this.brand;
    }
}

console.log(car.getBrand()); // Honda

```
```
let brand = car.getBrand;
```
```
console.log(brand()); // undefined
```
To fix this issue, you use the bind() method of the Function.prototype object. The bind() method creates a new function whose the this keyword is set to a specified value.
```
let brand = car.getBrand.bind(car);
console.log(brand()); // Honda

```
### 3) Constructor invocation
### 4) Indirect Invocation
In JavaScript, functions are first-class citizens. In other words, functions are objects, which are instances of the Function type.
The Function type has two methods: call() and apply() . These methods allow you to set the this value when calling a function.
```
function getBrand(prefix) {
    console.log(prefix + this.brand);
}

let honda = {
    brand: 'Honda'
};
let audi = {
    brand: 'Audi'
};

getBrand.call(honda, "It's a ");
getBrand.call(audi, "It's an ");
```
```
getBrand.apply(honda, ["It's a "]); // "It's a Honda"
getBrand.apply(audi, ["It's an "]); // "It's a Audi"
```
## Arrow Function
In arrow functions, JavaScript sets the this lexically.It means the arrow function does not create its own execution context but inherits the this from the outer function where the arrow function is defined. See the following example:
- Lexical scope: access variables and declarations inside function but not access any variable and declaration code outside which is define inside function.

## Global This
- In web browsers, the global object is window or frames.
- In Node.js, the global object is global.
- Use the globalThis object to reference the global object to make the code work across environments.

## JavaScript Object Properties
- JavaScript objects have two types of properties: data properties and accessor properties.
- JavaScript uses internal attributes denoted [[...]] to describe the characteristics of properties such as [[Configurable]], [[Enumerable]], [[Writable]], and  [[Value]], [[Get]], and [[Set]].
- The method Object.getOwnPropertyDescriptor() return a property descriptor of a property in an object.

## for__in loop
Enumerability: refers to whether a property of an object will be iterated over by certain operations.
- The for...in loop over the enumerable properties that are keyed by strings of an object. Note that a property can be keyed by a string or a symbol.
- The for...in  allows you to access each property and value of an object without knowing the specific name of the property. For example:
```
var person = {
    firstName: 'John',
    lastName: 'Doe',
    ssn: '299-24-2351'
};

for(var prop in person) {
    console.log(prop + ':' + person[prop]);
}

```
- We accessed the value of each property using the following syntax:
**object[property];**
- If you want to enumerate only the own properties of an object, you use the hasOwnProperty() method:

## Enumerable properties
- Enumerable properties are iterated using the for...in loop or Objects.keys() method.
- obj.propertyIsEnumerable() determines whether or not a property is enumerable.
- Example: console.log(person.propertyIsEnumerable('firstName')); // => true
console.log(person.propertyIsEnumerable('lastName')); // => true

## Own Property
- A property that is directly defined on an object is an own property.
- The obj.hasOwnProperty() method determines whether or not a property is own.
```
console.log(employee.hasOwnProperty('job')); // => true
console.log(employee.hasOwnProperty('firstName'));
```
## Factory Function
A factory function is a function that returns a new object. The following creates a person object named person1:
suppose same property and method u have to create 50 person object so define separatily we define below like that where createPerson function return new Object.
```
function createPerson(firstName, lastName) {
  return {
    firstName: firstName,
    lastName: lastName,
    getFullName() {
      return firstName + ' ' + lastName;
    },
  };
}

let person1 = createPerson('John', 'Doe');
let person2 = createPerson('Jane', 'Doe');
......for 50 peerson

console.log(person1.getFullName());
console.log(person2.getFullName());
```
### Object.create() method
- The Object.create() method creates a new object using an existing object as the prototype of the new object.
- Use Object.create() to create an object using an existing object as a prototype.

```
Object.create(proto, [propertiesObject])
```
## Sorting
### Bubble Sort
1. Compare two adjcent element and keep max element in last index until array is not sorted.

Time complexity: 
   Worst Case : O(n²)
   Average Case : O(n²)
   Best Case : O(n)
Space Complexity: O(1)
```
let array = [2,4,1,8,40,35];
let n = array.length
for(let i=0; i<n; i++){
  for(let j=0; j<n-i-1; j++){
    if (array[j] > array[j+1]){
      [array[j], array[j+1]] = [array[j+1], array[j]]
    }
  }
  
}
console.log(array);
```
### Selection Sort
1. Selection sort is a sorting algorithm that selects the smallest element from an unsorted part in each iteration and places that element at the beginning of the unsorted part.
   Time complexity: Worst case, Average case, and best case is O(n²).
   Space complexity: O(1)
   
```
let arr = [64, 34, 25, 10, 22, 11, 90]
let n= arr.length;
for(let i=0;i<n; i++){
    let minIndex = i;
  for(let j= i+1; j<n;j++){
    if(arr[j]<arr[minIndex]){
      minIndex = j;
    }
  }
  
  if(minIndex !== i){
    [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
  }
}
console.log(arr)
```
### Insertion Sort
Note: This algorithm works like organizing cards in your hand during a card game.

1. Insertion sort, each element is picked from the unsorted part and placed into its correct position within the sorted portion, gradually sorting the entire array.
Time complexity: 
   Worst Case : O(n²)
   Average Case : O(n²)
   Best Case : O(n)
Space complexity: O(1)
```
let arr = [64, 34, 25, 10, 22, 11, 90];
let n= arr.length;
for(let i=1; i<n; i++){
  let key = arr[i];
  let j= i-1;
  while(j>=0 && arr[j]>key){
    arr[j+1]=arr[j];
    j--;
  }
  arr[j+1]=key;
  
}
console.log(arr)
```
### Merge Sort
In Merge Sort, a recursive function is used to divide an array into multiple subarrays, and a merge function is used to combine those independent subarrays.
  Time Complexity: O(n logn)
  Space Complexity: O(n)
```
let arr = [12, 11, 13, 10, 20, 6, 5];

// Merge function for merge divided array
function merge(arr, start, mid, end) {
    let leftSize = mid - start + 1;
    let rightSize = end - mid;

    let leftArray = [];
    let rightArray = [];

    for (let i = 0; i < leftSize; i++) {
        leftArray[i] = arr[start + i];
    }
    for (let i = 0; i < rightSize; i++) {
        rightArray[i] = arr[mid + 1 + i];
    }

    let i = 0, j = 0, k = start;

    while (i < leftSize && j < rightSize) {
        if (leftArray[i] <= rightArray[j]) {
            arr[k++] = leftArray[i++];
        } else {
            arr[k++] = rightArray[j++];
        }
    }

    while (i < leftSize) {
        arr[k++] = leftArray[i++];
    }
    while (j < rightSize) {
        arr[k++] = rightArray[j++];
    }
}

// Recursive function for divide an Array
function mergeSort(arr, start, end) {
    if (start >= end) {
        return;
    }
    let mid = start + Math.floor((end - start) / 2);
    mergeSort(arr, start, mid);
    mergeSort(arr, mid + 1, end);
    merge(arr, start, mid, end);
}

mergeSort(arr, 0, arr.length - 1);
console.log(arr); 
```

### Quick Sort

1. Quick Sort is a highly efficient, comparison-based sorting algorithm that uses the divide-and-conquer approach. It works by selecting a "pivot" element, partitioning the array into two subarrays—elements smaller than the pivot and elements larger than or equal to it—and then recursively sorting these subarrays.
   Time complexity :
     Best Case Time Complexity: O(nlog⁡n)
     Average Case Time Complexity: O(nlog⁡n)
     Worst Case Time Complexity: O(n²)
   Space Comolexity :  O(log⁡n)
```
let arr = [10, 7, 8, 9, 1, 5]

function partion(arr, start, end){
  const pivot = arr[end];
  
  let i = start-1;
  
  for(let j=start; j<end; j++){
    if(arr[j]<= pivot){
      i++;
      [arr[i], arr[j]] =  [arr[j], arr[i]]
      
    }
  }
  // Place pivot in its correct position
    [arr[i + 1], arr[end]] = [arr[end], arr[i + 1]];
    return i + 1; 
}

function quickSort(arr,start,end){
  if(start< end){
  let partionIndex = partion(arr,start,end);
  quickSort(arr,start, partionIndex-1);
  quickSort(arr,partionIndex+1, end);
  }
}

quickSort(arr,0,arr.length-1);
console.log(arr);
```
## Counting Sort

Counting Sort is a simple sorting algorithm that sorts an array by counting the occurrences of each unique element and using those counts to determine their correct positions. It is efficient for datasets with a limited range of values and does not rely on comparisons to sort.

Time Complexity : O(n+k)
Space Complexity : O(n+k)
```
// let max_val = 9;
let arr = [1, 3, 2, 4, 5, 3, 2, 9]
let max_val = Math.max(...arr);

// Step 2: Initialize the count array of size max_val + 1, all elements set to 0
let count = new Array(max_val + 1).fill(0);
// console.log(count)

// Step 3: Count the occurrences of each element in the arr array
for (let num of arr) {
    count[num]++;
}
for (let i = 1; i <= max_val; i++) {
    count[i] += count[i - 1];
}
// Create the output array to store the sorted values
let output = new Array(arr.length);

// Step 5: Build the output array by placing elements at the correct positions
for (let i = arr.length - 1; i >= 0; i--) {
    let num = arr[i];
    output[count[num] - 1] = num;  // Place the element at the correct index in output
    count[num]--;  // Decrease the count for the current element
}

// Step 6: Copy the sorted elements from the output array back to the original array
for (let i = 0; i < arr.length; i++) {
    arr[i] = output[i];  // Copy the sorted values back to arr
}
console.log(arr)
```
## Notes: Quick Understand of Quick Sort
Step 1: Choose a Pivot
Step 2: Partition the Array
Step 3: Recursively Apply Quick Sort
Step 4: Base Case

1. Quick Sort Function
    Base Case
    Recursive Case
       Partition the array:
       Recursively Sort the Left Partition
       Recursively Sort the Right Partition
   
2.  Partition Function:
  Choose a Pivot
  Rearrange the Array
  Place the Pivot in the Correct Position
  Return Pivot Index
---
# LinkedList

Linked list store data in node, node is a object that have two things contain value (store data) and pointer( point to next node next-> null).

```
{ head:
 {
  value : 4,
   next: {
     value : 4,
        next: {
           value : 4,
                next: {
                   value : 4,
                      next: null
                    }
              }
    
        }
   }
}

```
Operation | LinkedList | Array
push  | O(1) | O(1)
pop | O(n) | O(1)
shift | O(1) | O(n)
unshift | O(1) | O(n)
insert | O(n) | O(n) 
delete | O(n) | O(n) 
lookup by index | O(n) | O(1)
lookup by valuw | O(n)  | O(n) 

## Example Define Linkedlist
```
class Node {
  constructor(value){
    this.value = value
    this.next = null
  }
}

class LinkedList {
  constructor(value){
    const newNode = new Node(value);
    this.head = newNode;
    this.tail = this.head;
    this.length = 1
  }
}

let ll = new LinkedList(4);
console.log(ll);
```
### Push Element (Add element in last)
```
class Node {
  constructor(value){
    this.value = value
    this.next = null
  }
}

class LinkedList {
  constructor(value){
    const newNode = new Node(value);
    this.head = newNode;
    this.tail = this.head;
    this.length = 1
  }
  
  push(value){
  const newNode = new Node(value);
  if(!this.head){
      this.head = newNode;
    this.tail = newNode;
    
  } else{
    this.tail.next = newNode;
    this.tail = newNode;
  }
  this.length++;
  return this;    //returning all LinkedList
}
}

let ll = new LinkedList(4);
ll.push(2);
console.log(ll)
```
### Pop Element (Remove element from last)

```
pop(){
    // If we have no item
    if (!this.head) return undefined;

    // If we have too many item and remove 
    let temp = this.head;
    let pre = this.head;

    while (this.temp) {
        pre = temp
        temp = temp.next
    }
    this.tail = pre;
    this.tail.next = null;
    this.length--;

    // if we have only one item
    if (this.length === 0) {
        this.head = null
        this.tail = null
    }
    return temp;
  }
}
```

### unshift() (Add element in front)

```
unshift(value){
  const newNode = new Node(value);

  if(this.head){
    this.head = newNode;
    this.tail = newNode;
    
  }
  else{
    newNode.next = this.head;
    this.head = newNode;
  }
   this.length++;
return this;
}
```
### shift (Remove element into the end)
```
shift(){
  let temp = this.head;
  if(!this.head) return undefined   //empty LinkedList
  this.temp = this.head;            // multiple node in LinkedList
  this.head = this.temp.next;
  temp.next = null
  this.length--;
  
  if(this.length === 0){      //when have only 1 item
    this.tail == null
  }
return temp;
}
```
### get (Get data from linkedlist)

```
get(index){
  if(index < 0 || index >= this.length){
    return undefined;
  }
  
  let temp = this.head;
  for(let i=0; i<index ; i++){
    temp = temp.next;
  }
  return temp;
}
```

### set (Set data into linkedlist)
```
set(index, value){
  if(index < 0 || index >= this.length ) 
    return undefined;
  
  let temp = this.get(index);
  if(temp){
    temp.value = value;
    return true;
  }
  return false;
}
```
### insert (add element anywhere in linkedlist)
```
insert(index , value){
  if(index === 0) return this.unshift(value);
  if(index === this.length) return this.push(value);
  if(index === 0 || index >= this.length) return false;
  
  const newNode = new Node(value);
  let temp = this.get(index-1);
  
  newNode.next = temp.next;
  temp.next = newNode;
  this.length++;
  return true;
}
```
### remove (delete element from anywhere)
```
remove(index){
  if(index === 0) return this.shift();
  if(index === this.length-1) return this.pop();
  
  if(index >0 || index >= this.length){
    return false;
  }
  
  let prev = this.get(index-1);
  let temp =  prev.next();
  
  prev.next = temp.next;
  temp.next = null;
  this.length--;
  return temp;
}
```
### reverse ( reverse the linkedlist)
```
reverse(){
  let temp = this.head;
  this.head = this.tail;
  this.tail = temp;
  let next = temp.next;
  let prev = null;
  
  for(let i=0; i<this.length; i++){
    next = temp.next;
    temp.next = prev;
    prev = temp;
    temp = next
  }
  return this
}
```
---
# Advance Topic
## DOM Manipulation

1. append
2. appendChild
3. innerText
4. textContent
5. innerHTML
6. remove(parameter)
7. removeChild(parameter)
8. getAttribute = return the value of attribute
9. setAttribute('key','value');
10. removeAttribute('id);
11. data-xyz attribute
12. classList.add('parameter') = add one move value of class
13. classList.revome('classValue') = remove that class value
14. classList.toggle('parameter') = if class value exist then remove if not then add          or  classList.toggle('paramert', true/false)
15. style.attributStyleName

textContent Vs innertText:
```
index.html
<div>
        <span data-test = "This is my test" id='id1' data-longer-name="other dataser value">Hello</span>
        <span style="display: none">Bye</span>
</div>
```
```
index.js
const div  = document.querySelector('div');
const span = document.getElementById('id1');

console.log(div.innerText);   
console.log(div.textContent);

console.log(span.dataset.test); // run and see in console
console.log(span.dataset.longer-name); // run and see in console

```
Here tetxContent =  hello , Bye. But innerText give output only which is visible on browser -  hello 
---
## Destructure
1. Object Destructure = const {name, age, address} = obj
2. Array Destructure = const [a,b,c] = arr
3. object inside obje destructure = const {address : {street, pincode, disct} } = obj
4. Default Destructure also we can = const {address : {street, pincode, disct, zipeer = 'xyz'} } = obj

## Rest Operater and Spread Operator
```
index.js

const divs = document.querySelectorAll("div");
console.log(divs)   // nodeList

;[...divs].map(div=>{
  console.log(div);
})
```
or
```
const divs = [...document.querySelectorAll("div")];
console.log(divs)

divs.map(div=>{
  console.log(div);
})
```

## Object Enhancement
```
const firstName = 'priti'
const lastName = 'modanwal'

const person = {
  firstName,
  lastName
}

or

const firstName = 'priti'
const lastName = 'modanwal'
const name = 'name'

const person = {
  firstName,
  lastName,
  [name]:firstName + " "+ lastName,    //add key and value in object
  sayHi(){
    console.log(hii)
  }
}


const age = 23
const index = 1;

const person = {
  [`age${index}`]: 23,
}
console.log(person)   // {firstName: 'priti', lastName: 'modanwal'}
```

## Null Coalescing
The null coalescing operator (??) in JavaScript is used to provide a default value when a variable is either null or undefined. It was introduced in ECMAScript 2020 (ES11) and is often used as a shorthand for ensuring a fallback value.

Note : If you are using this ?? operation take care can only compare between 2 operand (1 ?? 2)
```
let value = 0;
let defaultValue = 10;

console.log(value || defaultValue); // Output: 10 (because 0 is falsy)
console.log(value ?? defaultValue); // Output: 0 (because 0 is not null or undefined)

```
## Optional chaining 
Optional chaining (?.) in JavaScript allows you to safely access deeply nested properties of an object without explicitly checking if each property in the chain exists. It prevents runtime errors when trying to access properties on null or undefined.
Exam:
```
const obj = {
  name: 'priti',
  age:22
}

function per(person){
  console.log(person?.hobbies?.[0])
  console.log(person?.sayHi?.())
}
per(obj)
```
## Iterate Over the Object Vs map
```
let obj = {
  1: 'a',
  2: 'b',
  3: 'c'
}
Object.entries(obj).forEach(([key,val])=>
{
  console.log(key,val)
})

// Map
const map = new Map([
  [ 1 , 'a' ] ,
  [ 2 , 'b' ] ,
  [ 3 , 'c' ]
  ]);

map.forEach((key,val)=> {
  console.log(key,val)
})
```
#### Map 
In JavaScript, a Map is a built-in data structure that allows you to store key-value pairs where keys can be of any type, including objects, functions, or primitive types.

1. const map = new Map()
2. size of map = map.size
3. get value = map.get(key);
4. map.set(key,value)
5. check value is exist = map.has(key);  // return true or false
6. delete key value  = map.delete(key);de
7. clear map = map.clear();

#### Set
In JavaScript, a Set is a built-in data structure that allows you to store unique values of any type, including primitive types or object references.
1. const set = new Set([2,3,5,6,7,2,4,6])
2. includes() function
3. add element in set = set.add(2), set.add(90)
4. iterate over the set: set.has(element)
5. set.forEach( (val ) => console.log(val)
6. delete element = set.delete(element);
7. clear set = set.clear();

```
function setArray(arr){
  return [...new Set(arr)];
}
console.log(setArray([2,3,2,5,6,4,56,7,6]))
```
#### Symbole
Symbol is always consider unique value, if value is same but type is simple that is not equal same.
Symbol is a unique and immutable primitive data type primarily used to create unique property keys or identifiers. Symbols are often useful in scenarios where you need to avoid property name collisions or create hidden properties in objects.
```
const name = Symbol('Name');
const obj = {
  [name] : 'priti',
  age: 22
}

Object.entries(obj).forEach(([key,value])=>
 { 
   console.log(key,value)    // here age only will come age and don't come symbol because name is symbol type
 }
)

// get symbol type object key value also
console.log(Object.getOwnPropertySymbols(obj))
console.log(obj[name]);
```
#### generator and iterator
generator: A generator is a function where declare with '*' symbol and inplace of using return keyword in generator using yield. when a generator function call it can call like that( genFunc().next()). Here this is return one object which have 2 property = {value: 1, done: false}. Here in obj key name [value] and value is return what is yield returning and done false means generator not end.

Usecase:
Just want to do something and wait and doing next thing. If you want to create someting infinite loop
```
function* genFunc(){
  yield 1;
  yield 2;
  
}
const gen = genFunc();
console.log(gen.next()) // { value: 1, done: false }
console.log(gen.next().value)  // 2
console.log(gen.next().value)  // { value: undefined, done: true }
```
###### Fibonacci Series in generator
```
function* fibonacci(){
  let prev1 = 0;
  let prev2 = 1;
  
  
  yield 0;
  yield 1;
   while(true){
     const res = prev1+ prev2;
     yield res;
     prev1 = prev2;
     prev2 = res;
   }
  
}
const gen = fibonacci();
console.log(gen.next()) 
console.log(gen.next()) 
console.log(gen.next()) 
... n more
```
NOTE: console.log(gen.return()) // generator end (after calling this is you call any generator with next() function it will come generator is end value is undefined

### Object Getter and Setter

```
const person={
  firstName:'kyle',
  lastName:'doe',
  get fullName(){
    return (`${this.firstName} ${this.lastName}`)
  },
  set fullName(value){
    [this.firstName, this.lastName] = value.split(' ');
  }
}
person.fullName = 'priti modanwal'
console.log(person.fullName)
```
Note : If You see in js _propertyname like that key that means it is internal object property. prototype
```
const person={
  age : 24,
  get birthYear(){
    const date = new Date()
    return date.getFullYear() - this.age
  },
 
}

console.log(person.birthYear)
```
### Bind , Call and Apply

Bind: In JavaScript, bind() is a method used to create a new function where the value of this is explicitly set to a specific object, and optionally, you can predefine some arguments for that function.
```
window.name = 'Global Name';
const person = {
  name:'priti'
}
function printName(){
  console.log(this.name);
}

const res = printName.bind(person);
console.log(res())

OR

function sum(a,b){
  return a+b;
}
let sumOtherBind = sum.bind(null,4);
console.log(sumOtherBind(2));

OR

function prod(a,b){
  return a*b;
}

const nums = [2,4,5,3,8];
const res = nums.map(prod.bind(null, 2));
console.log(res)

```
Apply: The difference between call and apply in call they have to pass parameter normally and in apply we send parameter in array
```
function sum(...nums){
  return nums.reduce((acc,cur)=> acc+cur, 0)
  
}
const nums = [2,4,3,2,8];
console.log(sum.apply(null, nums));
console.log(sum.call(null,2,3,4,5))

```

Project - Simplify Quation Project

#### Polyfill:
In JavaScript, a polyfill is a piece of code (usually JavaScript) that provides modern functionality on older browsers that do not natively support it. Polyfills allow developers to use newer features of JavaScript or the web platform without breaking compatibility with older environments.

##### Why Use Polyfills?
Web standards evolve over time, introducing new features like Promise, fetch, or Array.prototype.includes. Older browsers may not support these features. A polyfill fills in this gap by adding the missing functionality.

### Transpile & Babel
Babel : It is javascript compiler
```
https://babeljs.io/
Try it out
```
#### Snowpack - The faster frontend build tool
#### rollup.js

## What is functional programming
Functional programming (FP) in JavaScript is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing state or mutable data. It's centered around pure functions, immutability, and the use of higher-order functions to build more predictable, testable, and modular code.

### Pure function
###### Characteristics of Pure Functions:
1. Output depends only on input: The function's behavior is entirely predictable based on its inputs.
2. No modification of external state: The function does not change variables, data, or state outside its own scope.
```
// Pure function: Adds two numbers
function add(a, b) {
    return a + b;
}
console.log(add(2, 3)); // Always returns 5

OR

const array = [1,2,3,4];
function pureFunc(arr,ele){
  return [...arr,ele]
}
let array2 = pureFunc(array,5);
console.log(array);
console.log(array2)          //This is pure function because array is not modify
```
```
// Impure function: Modifies external state
let counter = 0;
function incrementCounter() {
    counter++; // Modifies external variable
    return counter;
}
console.log(incrementCounter());          // Depends on external state

OR

const array = [1,2,3,4];
function pureFunc(ele){
array.push(ele);
}
pureFunc(5);
console.log(array); // this is impure function because actual array got modified
```
### Immutable Function

1. Object and array is declare const still they can change the value that thing is mutable but normal define variable as a const is immutable.
2. So making object immutable we can use Object.freeze(obj).
3.  The Object.freeze() method in JavaScript is used to make an object immutable. Once an object is frozen:
No new properties can be added to the object.
Existing properties cannot be removed or altered (values cannot be changed).
The prototype of the object cannot be changed.
```
const person = {
    name: "John",
    age: 30
};
Object.freeze(person);

person.age = 35;               // Will not work, silently fails in non-strict mode
person.city = "New York";     // Adding new properties is not allowed

console.log(person);         // Output: { name: "John", age: 30 }
```
#### Strict Mode Behavior
If you're in strict mode, attempting to modify a frozen object will throw a TypeError.
```
"use strict";

const person = Object.freeze({
    name: "John",
    age: 30
});
try {
    person.age = 35;              // Throws a TypeError in strict mode
} catch (error) {
    console.error(error.message); // Output: "Cannot assign to read-only property 'age' of object"
}
```
### High Order Function
A higher-order function is a function in programming that does one or both of the following:
1. Takes another function as an argument.
2. Returns a function as its output.

### NOTE: Map, filter and Reduce is HOF.

#### Function Composition

Function Composition in JavaScript refers to the process of combining multiple functions into a single function, where the output of one function becomes the input of the next
```
const array = [1,2,3,4,5];
function double(ele){
  return ele*2;
}

function addOne(ele){
  return ele+1;
}

function doubleAndAddOne(ele){
  return addOne(double(ele))
}

const res = array.map(doubleAndAddOne)
console.log(res);
```
## Currying
Currying is a functional programming technique where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument. Instead of providing all arguments at once, the function can be called incrementally, with each invocation returning a new function that accepts the next argument, until all arguments are provided and the final result is computed.

#### Key Concepts of Currying
1. Partial Application:
  Currying breaks a function with multiple arguments into multiple functions that take one argument at a time.
2. Flexibility:
  Currying enables you to reuse and partially apply functions for specific use cases.

Example: A function with multiple argument
```
function add(a, b) {
    return a + b;
}
console.log(add(2, 3)); // Output: 5
```
Example: A Currying function
```
function sum(a){
  return function(b) {
    return a+b
  }
}
console.log(sum(10)(2))
or
const addTwo = sum(2); // Partially apply the first argument
console.log(addTwo(3)); // Output: 12
```

## Debugger: A debugger is a software tool that helps developers identify and fix bugs (errors) in their code.
NOTE: In js use debugger keyword and run code then u will see on browser debugger
1. console.log()
2. console.error();
3. console.time();
4. console.timeEnd();
5. console.table();
6. console.trace();

### JEST Learn got to repo 
https://github.com/ModanwalPriti06/JESTtesting/tree/master

### Type of Tests
1. Unit Testing
2. Integration Testing
3. End to End testing

### Jest with ES6 checkout MathSolver Repo 
https://github.com/ModanwalPriti06/SImplifyEquationCalculatorJS-Project





































      














