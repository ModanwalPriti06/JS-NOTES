# JavaScript-Notes
Basic Javascript notes for beginners
- callback queue can called task queue also

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
```
const arr = Array.of(5);  
console.log(arr); // [5] — Not [undefined, undefined, undefined, undefined, undefined]
```
- Array.from() – create arrays from array-like or iterable objects.
```
const str = "hello";
const arr = Array.from(str);
console.log(arr); // ['h', 'e', 'l', 'l', 'o']
```
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
- this keyword refer global obj module.export it is not refer same obj where arraow function called but normal function refer same obj where function is called.

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

## Rest Operater and Spread Operator:
- The rest operator collects multiple elements into a single array or object
- The spread operator expands an iterable (like an array or object) into individual elements. It's commonly used in function calls, array literals, and object literals.
Example:
#### Rest Operator example
```
function sum(...numbers) {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}
console.log(sum(1, 2, 3)); // Output: 6
```
#### spread Operator
```
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = [...arr1, ...arr2];
console.log(combined); // Output: [1, 2, 3, 4]
```
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
- In JavaScript, the nullish coalescing operator (??) is a logical operator that returns its right-hand operand when its left-hand operand is null or undefined; otherwise, it returns its left-hand operand.
- The null coalescing operator (??) in JavaScript is used to provide a default value when a variable is either null or undefined. It was introduced in ECMAScript 2020 (ES11) and is often used as a shorthand for ensuring a fallback value.

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
## Bind , Call and Apply

```

```

### 1. Bind
- Bind: In JavaScript, bind() is a method used to create a new function where the value of ```this``` is explicitly set to a specific object, and optionally, you can predefine some arguments for that function.
```
window.name = 'Global Name';
const person = {
  name:'priti'
}
function printName(){
  console.log(this.name);   // this is using that is binding define value of this object 
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
### 2. call():
- It immediately invokes the function, passing the this value as the first argument and the function's arguments after that. The arguments are passed one by one (not as an array).

### Apply: 
- The difference between call and apply in call, they have to pass parameter normally and in apply we send parameter in array.
- It immediately invokes the function, similar to call(), but the arguments are passed as an array or an array-like object.
```
const obj = { name: "Alice" };
function greet(age, country) {
  console.log(`Hello ${this.name}, you are ${age} years old and live in ${country}.`);
}

greet.apply(obj, [25, "USA"]); // Output: Hello Alice, you are 25 years old and live in USA.

```
```
function sum(...nums){
  return nums.reduce((acc,cur)=> acc+cur, 0)
  
}
const nums = [2,4,3,2,8];
console.log(sum.apply(null, nums));
console.log(sum.call(null,2,3,4,5))

```
## Summary
- bind() returns a new function with a fixed this value and pre-set arguments, which you can call later.
- call() immediately calls the function, with arguments passed one by one.
- apply() immediately calls the function, with arguments passed as an array.

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
<img width="887" alt="Screenshot 2025-05-17 at 7 06 17 PM" src="https://github.com/user-attachments/assets/0fa7ce83-95a0-49a8-81f5-1b95704ed8ac" />

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

### NPM Audit
checkout this and get to know about semantic - https://semver.org/  
Examplt : ^4.12.1 - (major.minor.patch)

## Cross Site Scripting Security Issue:
Cross-Site Scripting (XSS) is a type of security vulnerability in web applications where attackers inject malicious scripts (usually JavaScript) into web pages viewed by other users. This attack exploits vulnerabilities in input validation or output encoding to execute unauthorized scripts in the context of a trusted website.

### Types of XSS
#### 1. Stored XSS (Persistent XSS):
Malicious scripts are stored on the server (e.g., in a database).
Scripts are served to users when they view a compromised page.
Example: Posting a script as a comment on a blog, which then executes for all viewers.

#### 2. Reflected XSS:
Malicious scripts are included in the URL or query parameters.
The server reflects the input back in the response without proper validation.
Example: A search result page displaying unescaped user input.
alert(document.cookie);

#### 3. DOM-based XSS:
Occurs on the client side.
The browser modifies the page’s DOM based on malicious input, allowing scripts to execute.
Example: Direct manipulation of innerHTML or eval() without sanitization.

## Sanitize User input

checkout link - https://www.npmjs.com/package/sanitize-html
1. npm install sanitize-html
2. In package json add in script : "start" : 'snowpack dev'
Example: 
sanitizeHtml(query)

### Code is public 
Note: In html js css all code are publice anyone can inspect and see the code for this reason we use api key in backend
.gitignore file = .env
.env = add key  (keyname = 'werfwrjfbwrejf')
server.js = 1. require dotenv 2. const API_KEY = process.env.keyname

### Cookie
In JavaScript, a cookie is a small piece of data stored on the user's browser by a website. Cookies are commonly used to store information like user preferences, session IDs, or tracking data, which can be sent back to the server with each subsequent request to maintain state or personalize the user's experience.

In cookie inside is there Http and secure and which cookie api is only http that can access only server which api hit is secure and http that only can see data in frontend in key value pair.
#### Key Features of Cookies:
1. Data Storage: Cookies can store simple data as key-value pairs.
2. Persistence: Cookies can be either: 1) Session Cookies: Automatically deleted when the browser is closed. 2)Persistent Cookies: Stored until a specified expiration date.
5. HTTP Communication: Cookies are sent automatically with each HTTP request to the domain that set them.
6. Cookies are domain-specific and can be restricted to specific paths within a website.

## BlackBox, Cohesion and coupling 
A pure function is low coupling high cohesion everytime.
Black box: In JavaScript, the term "black box" can refer to different concepts depending on the context. Generally, it implies something whose internal workings are hidden or not directly visible to the user or developer

## Closure:

- A closure is the combination of a function bundled together (enclosed) where innerfunction can access outer scope function and variable.
- In other words, a closure gives a function access to its outer scope. 
- innerfunction able to access outside variable and function.
- A function bind with lexical environment (function along with local scope).
```
function print(variable) {
  let c = 3;
  return function func(variable2){
    console.log(variable);
    console.log(variable2);
    console.log(c);
  }
}

let a = print(1);
a(2);
```
- Here one namste js video example for closure 
```
function call(){
  for(var i =0; i<5;i++){
    setTimeout(function() {
      console.log(i)
    }, i*1000);
  }
  console.log('Nameste Javascript')
}
call();    // output will be 5 5 5 5 5 because of isuing var if use let then will be work fine but if you don't want to solve with let then use closure, closure can help you
```
- clousre help example without let
```
function call(){
  for(var i =0; i<5;i++){
    function close(i){
      setTimeout(function() {
        console.log(i)
      }, i*1000);
    }
    close(i);
  }
  console.log('Nameste Javascript')
}
call();
```

### NaN: Nan is not equal to anything
### Async and Defer
![Uploading Screenshot 2025-01-18 at 6.14.15 PM.png…]()

## Callback: 
- A callback is a function that you pass as an argument to another function, and it gets called (or "called back") later when some task is done.
- Think of it like this:
 You ask someone to do a task for you, and when they finish, they call you to tell you it’s done. That "call" they make is the callback.
- Simply just think a callback function a function which one you want to run after some criteria and based on requirement;
- example: settimeout one parameter is callback function which want to run after 2 parameter duration, same if we click button want to run async funstion in js on click event listner.

<img width="785" alt="Screenshot 2025-05-17 at 6 50 48 PM" src="https://github.com/user-attachments/assets/a791f46f-011e-43c5-b5c3-7afa337b2237" />

## Callback hell: inside callback funstion call another callback function
example: inside setTimeout we are calling another callback setInterval and so on.
```
setTimeout(()=>{
  console.log('inside')
  setTimeout(()=>{
    console.log('inside 1');
     setTimeout(()=>{
         console.log('inside 1')
      },100)
   },100)
},100)
```
```
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
// Main async function
async function runSequence() {
  await delay(100);
  console.log('inside');

  await delay(100);
  console.log('inside 1');

  await delay(100);
  console.log('inside 2');
}
runSequence();
```
# Splice and Slice
## Splice :
- The splice() method change the original array
- Removes, replaces, or adds elements at a specific index.
- Modifies the original array.
- Returns the removed elements.
Syntax: array.splice(startIndex, deleteCount, item1, item2, ...);
Exam: arr.splice(1,3,'apple');
```
let arr = [1, 2, 3, 4, 5];
let removed = arr.splice(1, 2); // Removes 2 elements from index 1
console.log(arr);      // [1, 4, 5]
console.log(removed);  // [2, 3] (Removed elements)
```

## Slice : 
- Extracts a portion of the array and returns a new array.
- Does NOT modify the original array.
Syntax:  array.slice(startIndex, endIndex);  // startIndex include and endIndex exclude
```
let arr = [1, 2, 3, 4, 5];
let newArr = arr.slice(1, 4); // Extracts elements from index 1 to 3
console.log(arr);    // [1, 2, 3, 4, 5] (Original remains unchanged)
console.log(newArr); // [2, 3, 4] (Extracted portion)
```
| Feature | splice() (Mutable)	 | slice() (Immutable)
| ------------ | ----------- | ------------- |
| Modifies original array? | 	✅ Yes	| ❌ No | 
| Returns removed elements?	| ✅ Yes	| ❌ No |
| Can add elements?	| ✅ Yes	| ❌ No | 
| Used for extraction?	| ❌ No	| ✅ Yes |
| Works with negative indices?	| ❌ No	| ✅ Yes | 

### toString() Method in JavaScript
- The toString() method is used to convert an object, array, or other data types into a string representation.
### Difference Between toString() and join()
- toString() uses a default comma as a separator.
- join() allows you to specify a custom separator.

## String function

| Method	| Description | 
| ------ | -------- | 
| length	| Get string length | 
| charAt(index) | 	Get character at index| 
| charCodeAt(index)	|  Get Unicode of character | 
| toUpperCase() / toLowerCase()	|  Convert case | 
| trim(), trimStart(), trimEnd()| 	Remove spaces | 
| slice(start, end) | 	Extract part of string | 
| substring(start, end)	|  Extract substring (no negatives) | 
| indexOf(substring)	| Find first occurrence | 
| lastIndexOf(substring)	 |  Find last occurrence | 
| includes(substring)	|  Check if string contains substring | 
| startsWith(substring), endsWith(substring) | 	Check start/end of string | 
| replace(old, new)	| Replace substring | 
| split(separator)	|  Convert string to array | 
| concat()	|  Concatenate strings | 
| Template Literals ( ) | 	Modern way to concatenate | 

## IIFE - ( Immediately Invoked Function Expression)
- An IIFE is a javascript function that run as soon as is defined.
- ✅ Notice the parentheses () at the end—this immediately invokes the function.
Syntax
```
(function() {
    console.log("I am an IIFE!");
})(); 

```
### UseCase
-  Avoid Global Scope 
-  Execute Code Immediately	
-  Create Private Variables	
-  Prevent Function Name Conflicts	
-  Async IIFE	
-  Pass Arguments	Allows 
-  Minification & Optimization:	Helps in reducing file size and improving performance.

### Array of();
- Array.of() is a built-in JavaScript method that creates a new array from the given arguments.
- If you have multiple single value you want to convert and put in single array.
```
console.log(Array.of(1, 2, 3));  // ✅ [1, 2, 3]
console.log(Array.of("a", "b", "c"));  // ✅ ["a", "b", "c"]
console.log(Array.of());  // ✅ [] (Empty array)
```
### Object.freeze() 
- Object.freeze() makes an object immutable, meaning:
- ❌ No new properties can be added
- ❌ Existing properties cannot be removed
- ❌ Existing properties cannot be changed
- ❌ Prototype cannot be modified

### 📌 What is a Singleton?
- A singleton is a design pattern that ensures only one instance of an object exists throughout the program.
- In JavaScript, an object singleton is simply an object that is created only once and reused whenever needed.

### flat() function
- The flat() method flattens nested arrays into a single array up to a given depth.
- It removes nested arrays and merges their elements into the parent array.
```
const arr = [1, 2, [3, 4, [5, 6]]];
console.log(arr.flat()); 
// [1, 2, 3, 4, [5, 6]] (Flattens only one level)

or
const arr = [1, 2, [3, 4, [5, 6, [7, 8]]]];
console.log(arr.flat(2)); 
// [1, 2, 3, 4, 5, 6, [7, 8]] (Flattens 2 levels)

or
console.log(arr.flat(infinity)); 
// [1, 2, 3, 4, 5, 6, 7, 8] (Flattens 2 levels)
```
### round, ceil, floor, min, max 
- Math.round(3.4) = 4,  Math.round(9.7) = 10,
-  Math.ceil(3.4) = 4,  Math.ceil(4.1) = 5
-  Math.floor(4.2) = 4
-  (Math.random()*10) + 1 



  
 ---

# JavaScript Asynchronus
## Promises
- In JavaScript, a Promise is an object that represents the eventual completion or failure of an asynchronous operation and its resulting value.
- A promise is a JavaScript object that is used to handle all the asynchronous data operations. While developing an application, you may encounter that you are using a lot of nested callback functions, which causes a problem of callback hell. Promises solve this problem of callback hell.
- A Promise can be in one of three states:
-- Pending: The initial state, indicating that the operation is still ongoing.
-- Fulfilled: The operation completed successfully, and a resulting value is available.
-- Rejected: The operation failed, and a reason for the failure is available.
```
function callPromiseFunc(duration){
  return new Promise((resolved, reject)=>{
    setTimeout(resolved, duration);
  })
}

// setTimeout(()=>{
//  console.log('running...')
// },1000)

const data = callPromiseFunc(250);
data.then((msg)=>{                  //then is working like a callback
  console.log("promise running...")
})
```
## Other example how promise use in optimize callback
```
setTimeout(()=>{
  console.log('1');
  setTimeout(()=>{
    console.log('2')
  },1000)
},1000)
```
this above code change in promise
```
function convertPromise((duration)=>{
  return new Promise((resolved, reject)=>{
    setTimeout(resolved, duration);
  })
}

1. callPromiseFunc(250).then((msg)=>{
  console.log('1');
  callPromiseFunc(250).then(()=>{
    console.log('2')
  })
})

or

2. callPromiseFunc(250).then(()=>{
  console.log('1');
  return callPromiseFunc(250);
}).then(()=>{
    console.log('2')
    return callPromiseFunc(250);
})
  
output: 1 2
```
## Async and Await
```
function setTimeoutPromise(delay) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`You waited ${delay} milliseconds`);
    }, delay);
  });
}


//here not handling try and catch when return reject promise then will be issue
async function doStuff(){
  const message1 = await setTimeoutPromise(250);
  console.log('message 1', message1);
  const message2 = await setTimeoutPromise(250);
  console.log('message2', message2);
}

doStuff();
```
```
function setTimeoutPromise(delay) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject('Error');
    }, delay);
  });
}

async function doStuff(){
  try{
    const message1 = await setTimeoutPromise(250);
    console.log('message 1', message1);
    const message2 = await setTimeoutPromise(250);
    console.log('message2', message2);
  }catch(err){
    console.error(err)
  }
}

doStuff();
```
### Promise concurrency
- Promise.all(): Fulfills when all of the promises fulfill; rejects when any of the promises rejects.
- Promise.allSettled(): Fulfills when all promises settle.
- Promise.any(): Fulfills when any of the promises fulfills; rejects when all of the promises reject.
- Promise.race(): Settles when any of the promises settles. In other words, fulfills when any of the promises fulfills; rejects when any of the promises rejects.
- Promise.reject(): Returns a new Promise object that is rejected with the given reason.
- Promise.resolve(): Returns a Promise object that is resolved with the given value. 
##### All these methods take an iterable of promises (thenables, to be exact) and return a new promise
```
new Promise((resolve, reject)=> resolve(obj)).then(msg=>console.log(msg);
```

## Event loop and Delegation
- The event loop in JavaScript is a mechanism that handles asynchronous operations. JavaScript is single-threaded, meaning it executes code sequentially in a single call stack.
- Everything in Javascript happened in execution context.
```
console.log("Start");
setTimeout(() => console.log("setTimeout"), 0);
setImmediate(() => console.log("setImmediate"));
process.nextTick(() => console.log("nextTick"));
console.log("End");   
```
output:
```
Start
End
nextTick
setImmediate
setTimeout
```
### process.nextTick() in Node.js
- process.nextTick() is a Node.js method that schedules a callback function to be executed immediately after the current operation completes, before the Event Loop continues to the next phase.

##### execution context
- A big box which divide in 2 category
1. Memory Component ( Variable environment) = all variable and function are store in key value pair.
2. Code Component (Thread of Execution) = Just like whole code executed in thread run **one line at the time** (means one time can run one line only) that's why js is synchronous single threaded code component. 

### How it works:
Check up whatsapp image - uploaded
- Call Stack: JavaScript executes synchronous code line by line, pushing and popping function calls from the stack. Every time bottom of the stack have Execution context, means whenever js program is run this callstack populate this global execution context (GEC).
- Call stack maintain the order of execution of execution context.
- Web APIs: Asynchronous tasks like setTimeout, fetch, or event listeners are handled by Web APIs.
- Callback Queue & Microtask Queue: Once asynchronous tasks are completed, their callbacks are placed in the queue.
- - Microtasks (Promises, process.nextTick in Node.js) are prioritized over macrotasks (setTimeout, setInterval).
-  Event Loop: It constantly checks if the call stack is empty and pushes queued callbacks for execution.
---
- JavaScript all code run in main thread
- In JavaScript, the event loop is a mechanism that allows the language to perform non-blocking operations, even though it has a single-threaded execution model. This means JavaScript can handle tasks like user interactions, network requests, and timers without waiting for each operation to complete before moving on to the next.

## Event Delegation:
-  Event delegation is a pattern where you add a single event listener to a parent element instead of adding individual listeners to each child element. The idea is to leverage the event bubbling mechanism to catch events on the parent and then handle them based on which child element was clicked.
- Event delegation is a technique that leverages the concept of event propagation (bubbling) to manage events efficiently.
  
Suppose you have a list of buttons inside a <div> and want to handle click events for each button:
```
<div id="buttonContainer">
  <button>Button 1</button>
  <button>Button 2</button>
  <button>Button 3</button>
</div>
```
Instead of adding a click event listener to each button, you can add a single event listener to the parent <div>:
```
document.getElementById('buttonContainer').addEventListener('click', function(event) {
  if (event.target.tagName === 'BUTTON') {
    console.log(event.target.textContent + ' was clicked');
  }
});
```
### Advantage
This approach has several advantages:
- Improved performance
- Dynamic Elements


### Difference between null and undefined

| **Feature**   | **Null**             | **undefined**      |
|-----------------|-------------------------|--------------------------------------------|
| Definition | Represents an intentional absence of value. | Represents a variable that has been declared but not assigned a value. |
| Type	 | object (typeof null returns "object")	| undefined (typeof undefined returns "undefined") |
| Usage | Used when we want to explicitly assign "no value" to a variable.	 | Default value for uninitialized variables, missing function parameters, or missing object properties. |
| Example | let x = null;	| let y; console.log(y); // undefined |

## What is the difference between synchronous and asynchronous JavaScript?
- Synchronous operations run line by line, blocking the execution of any subsequent code until the current task is completed. So, each operation waits for the previous one to finish before starting.
- Asynchronous operations allow code to run non-blocking, meaning the execution can continue with other tasks without waiting for the current task to finish. When the task is completed, it typically triggers a callback, promise, or event to handle the result.

## setTimeout() and setInterval() in JavaScript?
- setTimeout(): This is used to execute a function once after a specified delay (in milliseconds). After the delay, the function is invoked and it does not repeat.
- setInterval(): This is used to execute a function repeatedly at a specified interval (in milliseconds). It keeps calling the function after each interval until you clear it using clearInterval().

## What do you understand by the concept of "debouncing" in JavaScript?
- Debouncing is used to limit the rate at which a function is executed, typically to handle scenarios where the function is called repeatedly, like on user input events (e.g., typing in a search box).
- In the case of search functionality, for example, debouncing prevents an API request from being sent on every keystroke. Instead, it waits for the user to stop typing for a specified period of time before triggering the API call. This helps improve performance and reduces unnecessary calls.
```
let debounceTimeout;
function debounceSearch(query) {
  clearTimeout(debounceTimeout); // Clear the previous timeout
  debounceTimeout = setTimeout(() => {
    // Make API call after the user stops typing for 300ms
    console.log(`Searching for: ${query}`);
  }, 300);
}

```

## Can you explain the concept of "throttling" and how it differs from debouncing?
- Throttling is a technique used to limit the rate at which a function is invoked. Unlike debouncing, which waits for a pause in user input, throttling ensures that the function is called at most once within a specified time interval, no matter how many times the event occurs.

#### Difference between Debouncing and Throttling:
- Debouncing: Only invokes the function once the event has stopped being triggered for a specified time. (i.e., "Wait until the activity stops.")
- Throttling: Restricts the function to be executed at most once in a specified time interval, even if the event continues to be triggered. (i.e., "Limit how frequently the function can run.")
```
let throttleTimeout;
function throttleSearch(query) {
  if (!throttleTimeout) {
    throttleTimeout = setTimeout(() => {
      // Make API call or execute function
      console.log(`Searching for: ${query}`);
      throttleTimeout = null; // Reset after the specified interval
    }, 1000); // Call at most once every 1 second
  }
}
```
## What are JavaScript's "this" and how does it work in different contexts?
- In JavaScript, the this keyword refers to the context in which a function is called. It is a special variable that can point to different objects depending on how a function is invoked. Here's how this behaves in different contexts:
- In a browser, this refers to the window object. In Node.js, this refers to the global object.
- Global Context: this refers to the global object.
  ```
    console.log(this); // In a browser, it will log the window object.
  ```
- Method Context: this refers to the object the method is called on.
  ```
  function test() {
    console.log(this);
    }
    test(); // In non-strict mode, 'this' will refer to the global object.
  
    or
  
    const person = {
    name: "John",
    greet: function() {
      console.log(this.name); // 'this' refers to the 'person' object
    }
    };
    person.greet(); // Output: "John"
  ```
- Arrow Functions: this is inherited from the outer context.
```
  const obj = {
    name: "Alice",
    greet: () => {
      console.log(this.name); // 'this' does NOT refer to 'obj', instead it refers to the enclosing scope
    }
  };
  obj.greet(); // Output: undefined (because 'this' is inherited from the global context)
```
- Constructor Functions: this refers to the newly created instance.
```
  function Person(name) {
    this.name = name;
  }
  const john = new Person("John");
  console.log(john.name); // Output: "John"
```
- Explicit Binding: call, apply, and bind allow you to set this explicitly.
```
  function greet() {
    console.log(this.name);
  }
  const person = { name: "Alice" };
  greet.call(person); // Output: "Alice"
```
## What is the difference between localStorage and sessionStorage in JavaScript, and how do they differ in terms of lifespan and scope?
- localStorage: It stores data with no expiration time. The data will persist even after the browser is closed or the computer is restarted, until it is explicitly removed via JavaScript or the user clears their browser data.
- sessionStorage: It also stores data locally, but the data is only available for the duration of the page session. This means that the data is lost when the browser window or tab is closed, but it persists across page reloads within the same session.

So the key difference is the lifetime of the data:

- localStorage persists until removed manually.
- sessionStorage is cleared when the session ends (i.e., when the browser/tab is closed).

## What is Rest API:
- Rest API is a way of accessing web services in a simple and flexible way without having any processing. It's used to fetch or give some information from web services. All communication done via REST API uses only http request.
- A RESTful API is an architectural style for constructing web APIs. A key characteristic of a RESTful API is its statelessness, signifying that each request carries all the essential information for its completion.
- Example: Client Server Modal

#### HTTP Request:
- GET
- POST
- PUT
- DELETE
- PATCH

### Falsy Value in js:
- undefined, null, NAN, 0, "", false.

### 📌 What is TDZ (Temporal Dead Zone)?
- Temporal Dead Zone (TDZ) is the time between when a let or const variable is hoisted and when it is initialized in JavaScript.
- During this time, accessing the variable results in a ReferenceError.
- It exists only for let and const, NOT for var.
```
console.log(x); // ❌ ReferenceError: Cannot access 'x' before initialization
let x = 10;
console.log(x); // ✅ 10
```
### 📌 Pass by Value & Pass by Reference – What's the Difference?
- In JavaScript, how a variable is passed to a function depends on its data type:
- Primitive types (string, number, boolean, null, undefined, symbol, bigint) → Pass by Value
- Non-primitive types (object, array, function) → Pass by Reference

- Pass by Value:
- original array effected:  ❌ No
```
let a = 10;
function changeValue(num) {
    num = 20; // Changing the copy, not the original
}
changeValue(a);
console.log(a); // 10 (Unchanged)

```
-  Pass by Reference (Mutable Data Types)
-  original array effected:  ✅ Yes
```
let obj = { value: 10 };
function modify(objRef) {
    objRef.value = 20; // Modifying the original object
}
modify(obj);
console.log(obj.value); // 20 (Changed)
```
## 🍪 Cookies in JavaScript 🍪
- A cookie is a small piece of data stored in the user's browser to track user sessions, preferences, or authentication details.
#### 🔹 Key Features of Cookies:
- Stored as key-value pairs in the browser.
- Can have an expiration time.
- Sent with every HTTP request to the server.
- Used for session management, authentication, and tracking.

## Function
1. function statement: A Function Statement (also known as a Function Declaration)
```
   function functionName(parameters) {
    // Function body
  }
```
2. Function Expression: A Function Expression is when a function is assigned to a variable.
```
const functionName = function(parameters) {
    // Function body
};
```
3. Anonymous Function: An anonymous function is a function without a name.
 ```
   const variableName = function(parameters) {
    // Function body
};
 ```
4. Named function: A named function is a function that has a name when it is declared.
```
function functionName(parameters) {
    // Function body
}
```
5. Anonymous Function Expression: Anonymous Function Expression is a function without a name that is assigned to a variable
```
const variableName = function(parameters) {
    // Function body
};
```
6. What are First-Class Functions?
- In JavaScript, functions are treated as first-class citizens, meaning:
- ✅ Functions can be assigned to variables
- ✅ Functions can be passed as arguments to other functions
- ✅ Functions can be returned from other functions
```
const greet = function(name) {
    return "Hello, " + name;
};
console.log(greet("Alice")); // ✅ "Hello, Alice"
```

## Lexical ENvironment
- A lexical environment is the local memory along with lexical environment of this parent
- Lexical environment = Lexical Scope + ref of lexical environment of parent.

  ## TDZ (Temporal dead zone)
  ```
  console.log(a);

  let a = 10;
  ```
  - here from line no 1 to 3 before initializing the time space is called TDZ.
  












































      














