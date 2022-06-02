# Closures 
* Js has **lexical scoping(Static Scope)**, Every scope has access to everything else outside the scope.  
```
let i = 1;
const f = () => console.log(i); // so i becomes available to the function
```
* __Lexical Scope__: HERE you define your function, determines what variables the function have access to WHEN it gets called.In other words, it doesn’t matter where and how you invoke the function, its all about where did it got declared.
* Js is mostly func programming lang so we define func in one scope and pass it to another scope in that scenario this may fail. 
* Closures are frequently used in JavaScript for object data privacy, in event handlers and callback functions, and in partial applications, currying, and other functional programming patterns.
* A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). Simple words: **Closures give you access to outer func scope from inner function.**
* In Js a closure is created every time a function is created.
* **Using closure**: define it inside another function and expose it: 
		1. return it
		2. pass it to another function. 
* __Creating Stateful function with closures__
		1. A stateful func is one which remembers about it's previous execution. 
	* __Implementing Singleton Pattern with closures__
	```
    		const LoggingService = (function() {
		    const infoMessage = 'Info: ';
		    const warningMessage = 'Warning: ';
		    const errorMessage = 'Error: ';
		    return {
		        info: function(str) {
		            console.log(`${infoMessage}${str}`);
		        },
		        warning: function(str) {
		            console.log(`${warningMessage}${str}`);
		        },
		        error: function(str) {
		            console.log(`${errorMessage}${str}`);
		        },
		    };
			})();			.
		// someOtherFile.js
		LoggingService.info('one'); // Info: one
		LoggingService.warning('two'); // Warning: two
		LoggingService.error('three'); // Error: three
    ```

	* __Higher Order function__
		1. The function which takes one or more functions as arguments and returns a func as argument
        ```
    	function rounder(places) {
    	return function(num) {
        return Number(num.toFixed(places));
		};
		}
		const rounder2 = rounder(2);
		const rounder3 = rounder(3);
		rounder2(floatingPoint); // 3.46
		rounder3(floatingPoint); // 3.457
        ```