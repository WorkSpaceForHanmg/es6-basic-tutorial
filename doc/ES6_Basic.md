### 1. var vs let
* **var - function scope,  let - block scope** 
```js
function foo() {
  var a = 'hello';
  if (true) {
    var a = 'bye';
    console.log(a); // bye
  }
  console.log(a); // bye
}
foo();

function foo_let() {
  var a = 'hello';
  if (true) {
    let a = 'bye';
    console.log(a); // bye
  }
  console.log(a); // hello
}
foo_let();
```

### 2. template literals
* **You can use string interpolation using template literals**
```js
let fName = "Derek";
let lName = "Banas";
console.log(`${fName} ${lName}`);

// Calculation in output using template literals
let num1 = 10
let num2 = 5
console.log(`10 * 5 = ${num1 * num2}`);
```

### 3. Object Literal
```js
let name = 'ReactJS';
let age = 30;
const obj1 = {"name":name, "age":age};
console.log(obj1);

const obj2 = {name, age};
console.log(obj2);

let myName = "name";
const obj11 = {[myName]:name};
console.log(obj11);
```

### 4. Spread Operator (...) 펼침연산자
```js
const odd = [1, 3, 5];
const nums = [2 ,4, 6].concat(odd);
console.log(nums);

const nums2 = [2, ...odd, 4, 6];
console.log(nums2);

const arr = [1, 2, 3, 4];
const arr2 = arr.slice();
console.log(arr);
console.log(arr2);
const arr3 = [...arr];
console.log(arr3);

//bad 
const arr4 = arr;
arr4.push(10);
console.log(arr4);
console.log(arr);

//good 
const arr5 = [...arr];
arr5.push(20);
console.log(arr5);
console.log(arr);
```

* **You can use tagged template literals to modify output using a function**
```js
function doMath(strings, ...values) {
  if (strings[0] == 'Add') {
    console.log(`${values[0]} + ${values[1]} = ${values[0] + values[1]}`);
  } else if (strings[0] == 'Sub'){
    console.log(`${values[0]} - ${values[1]} = ${values[0] - values[1]}`);
  }
}
 
doMath`Add${10} ${20}`;
doMath`Sub${10} ${20}`;
```

### 5. for-of 
* **for-in, for-of, forEach**
[mdn: for...of](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...of)

```js
const msgs = ['java','python','kotlin'];

for(let i=0; i < msgs.length; i++) {
  console.log(msgs[i]);
}

for(let idx in msgs){
  console.log(`${idx} 값은 : ${msgs[idx]}`);
}

for(let msg of msgs) {
  console.log(`값은 ${msg}`);
}

msgs.forEach(msg => console.log(msg));
```

### 6. ARRAYS
[mdn: Array.from()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
```js
// Array.of() is used to create arrays instead of the array
// constructor
let array1 = Array.of(1,2,3);
 
// Create an object into an array
let array2 = Array.from("word");
 
// You can use Array.from to manipulate values
let array3 = Array.from(array1, (value) => value * 2);
 
// Iterate over values
for (let val of array3) console.log(`Array Val : ${val}`);
```

### 7. Arrow Function 
[mdn: Arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

```js
function add(n1,n2) {
  return n1 + n2;
}
const result = add(10,20);
console.log(result);

const result2 = (n1,n2) => (n1 + n2);
console.log(result2(30,40));

const result3 = (n1,n2) => {
  const temp = n1 + 10;
  return temp + n2;
}
console.log(result3(30,40));
```

* **using arrow function : forEach()**
[mdn: Array.prototype.forEach()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
```js
const myArr = [10,30,50,60];
//forEach(consumer) val => void
myArr.forEach(val => console.log(val));
```

* **using arrow function : map(), filter(), reduce()**
[mdn: Array.prototype.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)   
[mdn: Array.prototype.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)   
[mdn: Array.prototype.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)   

```js
const myArr = [10,33,50,60];
//map(function) t => r
const result = myArr.map(val => val + 30);
console.log(result);

//filter(predicate) t => boolean
let evenValue = myArr.filter(item => item % 2 == 0);
console.log(evenValue);

//reduce(operator) (t1,t2) => t3
const sum = myArr.reduce((prev,curr) => prev + curr);
console.log(sum);
```

* **Arrow function this**
```js
function BlackDog() {
  this.name = '흰둥이';
  return {
    name:'검둥이',
    bark() {
      console.log(this.name + ' 멍멍!');
    },
    bark2: () => {
      console.log(this.name + ' 멍멍!');
    } 
  }; 
}
const blackDog = new BlackDog();
blackDog.bark(); // 검둥이 멍멍!
blackDog.bark2(); //흰둥이 멍멍!
```

### 8. String util function 
[mdn: Array.prototype.startsWith()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)   
[mdn: Array.prototype.endsWith()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)   

```js
// Repeat a string
console.log("Hello ".repeat(3));

let fName = "Derek";
// Does a string start with a value
console.log(fName.startsWith("De"));

// Does it end with
console.log(fName.endsWith("ek"));
 
// Does it include
console.log(fName.includes("ere"));
```

### 9. Default Parameter Values 
* **Default values are defined next to parameters**
```js
function getSum(num1 = 1, num2 = 2){
  console.log(`${num1} + ${num2} = ${num1+num2}`);
 
  // arguments[] only receives the value passed
  console.log(`${arguments[0]} + ${arguments[1]}`)
}
getSum(3);
```

### 10. Destructuring Assignment

* **Array의 Destructuring Assignment**
```js
// You can destructor arrays as well
let favNums = [2.718, .5772, 4.6692];
let [,,chaos] = favNums;
console.log(`Chaos : ${chaos}`);

// You can use rest items to grab part of an array
let [, ...last2] = favNums;
console.log(last2);
console.log(`2nd Num : ${last2[0]} ${last2[1]}`);

let [...rest] = favNums;
console.log(rest);
console.log(rest[0], rest[1]);

let [n1,n2,n3] = favNums;
console.log(n1 + " " + n2 + " " + n3);

// This can be used to switch values
let val1 = 1, val2 = 2;
[val1,val2] = [val2,val1];
console.log(`Val2 : ${val2}`);
```
* **Object의 Destructuring Assignment**
```js
const {a,b,...z} = {a:100,b:200,c:300,d:400};
console.log(a);
console.log(b);
console.log(z);
console.log(z.c);
console.log(z.d);

let obj = {p: 42, q: true};
console.log(obj.p);
console.log(obj.q);

let {p,q} = {p: 42, q: true};
console.log(p);
console.log(q);

let person = {
  name:'React', 
  addr:{home:'Seoul', office:'Gyeonggi'}
};
let {name,addr} = person;
console.log(name);
console.log(addr);
let {home,office} = addr;
console.log(home);
console.log(office);

// let {name,addr:{home,office}} = person;
// console.log(name);
// console.log(home);
// console.log(office); 
```

```js
let person = {
  name:'React', 
  addr:{home:'Seoul', office:'Gyeonggi'},
  phone:{mobile:{
    phone1:'010-1234',
    phone2:'010-5678'
  }}
};

let {name,
     addr:{home,office}, 
     phone:{mobile:{phone1,phone2}}} = person;
console.log(name);
console.log(home);
console.log(office); 
console.log(phone1);
console.log(phone2);
```
### 11. OBJECTS
```js
// You create object literals like this
function createAnimal(name, owner){
  return {
    // Properties
    name,
    owner,
    // Create a method
    getInfo(){
      return `${this.name} is owned by ${this.owner}`
    },
    // Objects can contain other objects
    address: {
     street: '123 Main St',
     city: 'Pittsburgh'
    }
  };
}
 
var spot = createAnimal("Spot", "Doug");
 
// Execute method
console.log(`${spot.getInfo()}`);
 
// Access object in the object
console.log(`${spot.name} is at ${spot.address.street}`);
 
// Get properties and methods of object
console.log(`${Object.getOwnPropertyNames(spot).join(" ")}`);
 
// You can store values from Objects with destructoring
let { name, owner } = spot;
console.log(`Name : ${name}, Owner : ${owner}`);
 
// Get the inner class value
let { address } = spot
console.log(`Address : ${address.street}`);

let { address: {street, city}} = spot;
console.log(`Street : ${street}`);
console.log(`City : ${city}`);
```

### 12. CLASSES
* **Class Definition**
```js
class Mammal{
  constructor(name){
    this._name = name;
  }
 
  // Getter
  get name() {
    return this._name;
  }
 
  // Setter
  set name(name){
    this._name = name;
  }
 
  // Static Mammal creator
  static makeMammal(name){
    return new Mammal(name);
  }
 
  getInfo(){
    return `${this.name} is a mammal`;
  }

  getInfo2() {
    return {
      name:'Whale',
      namef: function() {
        console.log(`${this.name} is a mammal`);
      },
      namef2: () => {
        console.log(`${this.name} is a mammal`);
      }
    };
  } 
};
```

* **Create an object**
```js
// Mammal 객체생성
let monkey = new Mammal("Fred");
console.log(monkey.getInfo());

// Change name - Call setter
monkey.name = "Mark";
 
// Call getter
console.log(`Mammal : ${monkey.name}`);
 
// Create Mammal using static function
let chipmunk = Mammal.makeMammal("Chipper");
console.log(`Mammal 2 : ${chipmunk.name}`);

chipmunk.getInfo2().namef();
chipmunk.getInfo2().namef2();
```

* **Inheritance : You can inherit properties and methods with extends**
```js
//Marsupial - 유대류는 포유류의 한 갈래
class Marsupial extends Mammal{
  constructor(name, hasPouch){
    // Call the super class constructor
    super(name);
    this._hasPouch = hasPouch;
  }
 
  get hasPouch() {
    return this._hasPouch;
  }
 
  set hasPouch(hasPouch){
    this._hasPouch = hasPouch;
  }
 
  // You can override methods
  getInfo(){
    return `${super.name} is a marsupial`;
  }
 
}

// Marsupial 객체생성
let kangaroo = new Marsupial("Paul", true);
console.log(`It is ${kangaroo.hasPouch} that ${kangaroo.name} has a pouch`);

// Test overridden method
console.log(`${chipmunk.getInfo()}`);
console.log(`${kangaroo.getInfo()}`);
```

* **You can dynamically inherit from Classes**
```js
function getClass(classType){
  if (classType == 1) {
    return Mammal;
  } else {
    return Marsupial;
  }
}
 
class Koala extends getClass(2){
  constructor(name){
    super(name);
  }
}
 
let carl = new Koala("Carl");
console.log(`${carl.getInfo()}`);
```

* **private member**
```js
class Person {
  //생성자
  constructor(name) {
    let _name = name;
    this.setName = function(name){
      _name = name;
    }
    this.getName = function() {
      return _name;
    }
  }
  // getter
  get name() {
    return this.getName();
  }
  set name(name){
    if(name.startsWith('A')){
      this.setName(name);
    }
  }
}

// Person 객체생성
let person1 = new Person("aaa");
console.log(person1.getName());
console.log(person1.name);
```

### 13. SETS
* **A Set is a list of values with no duplicates**   
[mdn: Set()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/Set)
```js
var randSet = new Set();
randSet.add(10);
randSet.add("Hello");
randSet.add("Word");
 
// Check to see if set contains a value
console.log(`Has 10 : ${randSet.has(10)}`);
 
// Get size of Set
console.log(`Set Size : ${randSet.size}`);
 
// Delete item from list
randSet.delete(10);
 
// Iterate a Set
for (let val of randSet) console.log(`Set Val : ${val}`);
```

### 14. MAPS
* **A Map is a collection of key/value pairs**
```js
var randMap = new Map();
randMap.set("key1", "Random String");
randMap.set("key2", 10);
 
// Get values
console.log(`key1 : ${randMap.get("key1")}`);
console.log(`key2 : ${randMap.get("key2")}`);
 
// Get size
console.log(`Map Size : ${randMap.size}`);
 
// Iterate Map
randMap.forEach(function(value, key){
  console.log(`${key} : ${value}`);
});
```

### 15. PROMISES
* Promises define code that is to be executed later
* Promises either succeed or fail once
* They either are fulfilled, rejected, pending, or settled

```js 
// A Promise that is handled immediately
var p1 = Promise.resolve('Resolve Me');
 
// then takes 2 optional arguments being first a callback
// for a success and another for failure
p1.then((res) => console.log(`${res}`));
 
// Create a promise that executes after 2 seconds
var p2 = new Promise(function(resolve, reject){
  setTimeout(() => resolve('2Seconds Resolve Me'), 2000);
});
 
p2.then((res) => console.log(`${res}`));
 
// Here I demonstrate how then is used if a promise is
// fulfilled or rejected
let randVal = 6;
 
var p3 = new Promise(function(resolve, reject){
  if (randVal == 18){
    resolve("Good Value");
  } else {
    reject("Bad Value");
  }
});
 
p3.then((val) => console.log(`${val}`),
        (err) => console.log(`${err}`));

// You should add catch to a chain to handle errors
 
var p4 = new Promise((resolve, reject) => {
  if (randVal <= 17){
    throw new Error("Can't Vote"); // Same as a Reject
  } else {
    resolve("Can Vote");
  }
});
 
p4.then((val) => console.log(`${val}`))
  .catch((err) => console.log(`${err.message}`));
```  

### 16. Modules
* export or import statement in a module to export or import variables, functions, classes 

* **export**
```js
let greet = "Hello World!";
const PI = 3.14; 

function multiplyNumbers(a, b) {
    return a * b;
}

// Exporting variables and functions
export { greet, PI, multiplyNumbers };
```  
* **import**
```js
import { greet, PI, multiplyNumbers } from './main.js';

alert(greet); // Hello World!
alert(PI); // 3.14
alert(multiplyNumbers(6, 15)); // 90
``` 

