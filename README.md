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
#### At first get true
```composer log
var a = 3;
a && conlose.log('Ok');
```
#### At first get false
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


# 6. Hosting 

```composer log
/*at first run function declaration
then call */

add (3, 4);
function(a, b){
    return a+b;
}
```






