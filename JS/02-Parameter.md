# Parameters
* Object is passed by **reference** and primitive types by **value**
* **Pass By Value**: If you change a value of primitive type inside a function then it will not effect outside function block. – Copy of argument is passed. 
* **Pass By Reference**: When we change a property the change will be reflected in outer scope. **We can’t change what variable points to , but only change property value**
```
var a  = {‘moo’: ‘too’}
function foo(a){
    a = {‘too’: ‘moo’}
    }
console.log(a) // prints {‘moo’:’too’} as we cant change what it points to

```