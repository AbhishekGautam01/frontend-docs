# variables 
* defined using : **let, const, var**
* let is used to define **block level** and only available in the block 
* const allows us to declare variables whose values never change. It is also available in **block** in which it is declared. 
>? 	__NOTE:__ Like other programming language js variables don’t have a block scope they have function scope which means they are available in the function which they are defined in. But in ECMA2015 – let & const allows us to define the block scoped variable 

# Scopes 
* It tells how long a variable lives before it dies. 
* Any variable defined outside any block is **global**, another way to define is to add it to **global property (window.moo = 1)** -> moo becomes a global variable
* IN **NODE** the global is **global** not window
* **Function Scope**: Variable declared with var defined within a function will only live in that function. 
* **Block Scope**: In ES6 let and const came to create block scope; var is not block scoped it is global scope. 
```
//BLOCK SCOPE 
{
  var a = "block"
  let b = "block 2"
}
console.log(a); //block
console.log(b); //undefined
```

## Variable Hoisting
* Variables and functions will get hoisted to top of scope. 
```
console.log(someVar);
var someVar = 1; // JS will split it into 2 line as shown below 
---------------------------------------------
var someVar; //moved to top of scope // top of file || or top of function
console.log(someVar); //undefined
someVar = 1;
``` 

## Scope Chain
* A function scope can live within nested function scope 
* When a function need a variable then it will look into it's own scope to get it if can't get it then it will keep going outer and outer till it reach global scope. 
* Scope chain is **defined the way program is written**. Scope chain is defined lexically i.e. which is function is defined. 
```
var myVar = 1;
function bar(){
    function foo(){}{
        console.log(myVar);
    }
    foo(); // gets my var from global scope
}
bar();
```

# Operators 
* **Numeric Operators**: +, -, *, / , %, ++, __ 
> **NOTE**: If you add string to a number of any other type everything will get converted to string 
* **Comparision**: ==, ===, !=. !==, >, <, <= , >=
* **bitwise** operators are also supported

## == vs === 
* First is equality other is strict equality
* [JS Equality Table](https://dorey.github.io/JavaScript-Equality-Table/)

## Rest Operator 
* **ES6**
```
function sum(a, b){
    console.log(arguments); //looks like an array and has all arguments passed to functions.
    return a + b;
}

sum(1, 2, 3, 4) // will print 3 & ignore last 2 parameters

function sumArgVar(){
    var total = 0;
    for(var i = 0; i < arguments.length; i++){
        total += arguments[i];
    }
    return total;
}

sumArgVar(1)
sumVarArg(1,2,3,4) // the problem with above is that we cant look at method signature to tell about paramters
```

* **REST operator** : This has to be last param in a function. **most commonly used in functions**
```
function login(method, ...options){
    console.log(method);
    console.log(options);
}

login("facebook", 1, 2, 3, 4);
```
## Spread Operator 
* takes a single array value and explodes as a number of single element 
```
var arg1 = [4, 5,6]
var arr2 = [1, 2, 3, ...arg1] //[1, 2, 3, 4, 5, 6]
```
* **Use Cases**: 
    * Concat, Join Arr, Copying an array 
    * Explode the function arg which takes variables of arg. 

# Control Structures
* if , if else, if else if, while , do wile, for , for of , for in (which is for object properties)
* Ternary operator & Switch Statements

