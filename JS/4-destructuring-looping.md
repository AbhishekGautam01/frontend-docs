# Destructuring 
* came in ES6 
```
const obj = {first: 'abhishek', last: 'gautam'}
const {first: f, last: l} = obj;
console.log(f)
console.log(l)
```

# Different For Loops 
```
// FOR Loop 
let array = [1, 2, 3]
for(let i = o; i < array.length; i++){
    console.log(array[i]);
}

// break & continue are not supported
array.forEach(function(value){
    console.log(value);
})

function doSomething(){ 
  for(let i = 0; i < array.length; i++) {
    console.log(array[i]);
    return; //return from the main outer function 
  }
}

function doSomething(){ 
  array.forEach(function(value){
    console.log(value);
    return; //return out of the inner function not main outer function. 
  })
}

//for in designed for object
var obj = {a: 1, b: 2, c: 3}
for(let prop in object){
  console.log(prop);
}

//for of - for array 
for(let value of array){
  console.log(value);
}

```