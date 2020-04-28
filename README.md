# 1. Number

#### Process object 

```composer log
console.log(process.argv)

cmd : node fileName arg1 agr2
```

# 2. String
#### Type of String
```composer log
a. " " : Duble code
b. ' ' : Single code
c. ` ` : Tail Operator
// We can use varriable into tail opt, Exm: `hello ${varriableName}`;
```
#### String Property

```composer log
var a  = "Hello";
a.charAt(0); // output : H
a.charCodeAt(0) // output : H er ask code number show
a.indexOf(H) // output : show position number in this string
a.match('He') // output : show array ['He'] what if find or not null return
a.replace('H', 'h') // output: 1st which will be replace, what by replace
a.lenth // output : show lenth
a.toUpperCase();
a.toLowerCase();
a.trim(); // output trim extra space befor and after string
```

# 3. Value and operator 
#### Data type
```composer log
6 types of data type 

a. Number
b. String
c. Boolean;
d. function();
e. object();
d. undefined
```

#### Operator
```composer log
3 types of operator

a. Binary operator
b. Unery operator
c. Ternary operator
```

# 4. Boolean
#### False 
```composer log
a. null
b. undefined
c. '' // empty string
d. 0 // zero
e. NaN
f. false
```

#### True
```composer log
a. "sddsfds " // any string
b. any number -1 or + number, except 0
c. []
d. {}
e. ' ' // Space string
```

## Short circuit evaluator
#### `for &&`As long as get true until then go next expression
```composer log
var a = 3;
a && conlose.log('Ok');
```
#### `for ||`As long as get false until then go next expression
```composer log
var a = false
a || console.log('Hellow world');
```

# 5. [IIFE] Immediate invoke function expression
```composer log
(function(){
let x = 3;
console.log(x);
})();

!function(){
let x = 3;
console.log(x);
}();

+function(){
let x = 3;
console.log(x);
}();
```


# 6. Hoisting 

```composer log
/*at first run function declaration
then call, where if you write a function*/
exm:
add (3, 4);
function(a, b){
    return a+b;
}

exception:
add(5,7); // it's occurded error
var add = function(a, b){
    return a+b;
}
//But if you call function after function declaration, then it's ok 
```
# 7. Conditional statement

```composer log
var msg = document.querySelector("#message");
var btn = document.querySelector("#interact");
var result = document.querySelector("#answer");

btn.addEventListener("click", function() {
  let c = msg.value.toLowerCase();
  let reply = "";
  if (c.match("hello")) {
    reply = "hello there!";
  } else if (c.match("sing for me")) {
    reply = "Ami banglay gan gai";
  } else if (c.match("tomar nam ki")) {
    reply = "Amar nam Kuddus Bot";
  } else {
    reply = "Bujhi nai";
  }
  result.innerHTML = reply;
  var kotha = new SpeechSynthesisUtterance(reply);
  window.speechSynthesis.speak(kotha);
});
```

# 8. Arrow Function

```composer log
var add = function(a, b){
    return a + b;
}

var add = (a, b) => {return a + b};

console.log(add(4, 6));

```

# 9. Closure Function
```composer log
function makeFunc(){
    var name = 'Hi';
    function displayName(){
        console.log(name)
    }
    return displayName;
}

var myFunc = makeFunc();
myFunc()
```

# 10. Pure Function
```composer log
function add(a, b){
    let r = c + d;
    c = 10;
    return r;
}

let c = 20;
let d = 10;
console.log(add()); // 30
console.log(c); // 10
console.log(d); // 10
```

# 11. Function property
```composer log
function add(a, b)
{
    console.log('This is a function call ...');
    console.log(this);
    console.log(a);
    console.log(b);
}



var d = add.bind(2);

d(34, 55);

add.call('dd',3,5);

add.apply('man', [2, 3]);
```

# 12. High order function 
```composer log
function generator(type){
    if('plus' === type){
        return (a, b) => a + b;
    }else if('minus' === type){
        return (a, b) => a - b;
    }
}

var onOff = generator('minus');
console.log(onOff(23, 12));
```

# 13.  Prototype
```composer log
var father = {
    b:55,
    c:"Hello",
    d:function(){
    console.log('hi')
    }
}

var chield = Object.create(father);
chield.b = 45;
console.log(chield.hasOwnProperty('b'));
```

# 14. Object produce

#### Factory pattern
```composer log
function CreateHuman(name, age, gender){
  return {
    name, 
    age, 
    gender
  }
}

var a = CreateHuman('Khayrul', 28, 'Male');
var b = CreateHuman('Mehedi', 23, 'Male');
console.log(a);
console.log(b);
```
#### Constructor pattern
```composer log
function CreateHuman(name, age, gender){
    this.name = name, 
    this.age = age, 
    this.gender = gender
}

var a = new CreateHuman('Khayrul', 28, 'Male');
var b = new CreateHuman('Mehedi', 23, 'Male');
console.log(a);
console.log(b);
```

# 15. Class
```composer log
//constructor function
function Animal(type, live){
  this.type = type,
  this.live = live
}

class Human extends Animal{
  constructor(name){ // need constructor method
    super('Khayrul', true); // init construct method's arguments
    this.name = name // add new property
  }  
}

var man = new Human('Apple');
console.log(man.type);
console.log(man.live);
console.log(man.name);
```

# 16. For In
```composer log
var man = {
    name : 'Khayrul',
    age  : 43,
    addr : 'Manikgonj'   
}

for(let item in man){
    console.log(`my ${item} is ${man[item]}`);
}
```

# 17. Array Function
#### forEach
```composer log
var man = ['Khayurl', 'Riad', 'Rana', 'Labib', 'Dip'];

var newMan = [];
man.forEach(item=>{
newMan.push(item+ ' mantion');
});

console.log(newMan); //["Khayurl mantion","Riad mantion","Rana mantion","Labib mantion","Dip mantion"]
```
#### map
```composer log
var man = ['Khayurl', 'Riad', 'Rana', 'Labib', 'Dip'];

var newMan = man.map(item=>{
    return item + ' hi';
});

console.log(newMan); //["Khayurl hi","Riad hi","Rana hi","Labib hi","Dip hi"]
```

#### reverse
```composer log
var myString = "Khayrul Hasan";

let myArr = myString.split("");
let reverseArr = myArr.reverse();
let result = reverseArr.join("");
console.log(result); // "nasaH luryahK"

```
#### sort
```composer log
let number = [2, 3, 10, 30, 49, 2];

let result = number.sort((a, b)=>{
  return a-b;
});

console.log(result); //[2,2,3,10,30,49]
```
#### concat
```composer log
let array = [1, 3, 5];
let anotherArray = [3, 4, 6];
let result = array.concat(anotherArray);
console.log(result); //[1,3,5,3,4,6]
```

#### slice
```composer log
var myArray = [1, 3, 4, 56, 43, 10];
var newArray = myArray.slice(2,5);
console.log(newArray); //[4,56,43]
```

#### every
```composer log
//Check every element for a specific condition
var myArray = [6, 4, 56, 4, 10];

var evenNumber = function(num){
  let remainder = num%2;
  if(remainder === 0 ) return true ;
  return false;
}

let check = myArray.every(evenNumber);
console.log(check); //true
```

#### some
```composer log
//Check at least one element for a specific condition
var myArray = [6, 4, 56, 4, 10];

var evenNumber = function(num){
  let remainder = num%2;
  if(remainder === 0 ) return true ;
  return false;
}

let check = myArray.some(evenNumber);
console.log(check); // true
```

#### filter
```composer log
// Filter element from array and create a new array
var myArray = [6, 4, 56, 4, 10, 5, 2, 9];

var evenNumber = function(num){
  let remainder = num%2;
  if(remainder === 0 ) return true ;
  return false;
}

let check = myArray.filter(evenNumber);
console.log(check); //[6,4,56,4,10,2]
```
#### splice
```composer log
/*
***first param = starting splice
***second param= how many element delete
***next params add to array
***it is mutator function, that is mean origin array will be change
*/
var myArray = [6, 4, 56, 4, 10, 5, 2, 9];
myArray.splice(2, 3, 67, 'kj', 'kam');
console.log(myArray); // [6,4,67,"kj","kam",5,2,9]
```

#### reduce
```composer log
/*
*** first iteration : get given 0 value as 'a' and take first element from array as 'b'
*** second iteration : get return value of first iteration as 'a' and take second element from array as 'b'  
*/
var myArray = [6, 4, 56, 4, 10, 5, 2, 9];

var newVal = myArray.reduce((a,b)=>{
  return a+b;
},0); // given value 0

console.log(newVal); //96
```

# 18. Date
```composer log
var d = new Date();
console.log(d);// "2020-04-28T21:05:44.701Z"
console.log(d.toDateString()); // "Wed Apr 29 2020"
console.log(d.toTimeString()); // "03:07:42 GMT+0600 (Bangladesh Standard Time)"

```

