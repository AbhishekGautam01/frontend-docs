# Java Script 
## Introduction 
* Brenden Eich (1995); It's an **agreement**
* TC39 disucss **features** for JS 
* 100% Backward Compatible 
> **NOTE** [CanIUse.com](caniuse.com) -> to check which JS features is supported by which browser.
> [node.green](node.green) -> does the same for node
* Runs a **scripting language** in a host environment 
* Supports OOPS by **Object Prototyping** and not classes
* **FUNCTIONAL PROGRAMMING** - Functions may be stored in a variables & passed around as any variable

## Types
* We can use **typeof()** to check type
* **Dynamically types language vs Statically typed language** 
    * In STL, while coding we have to define what the type var will hold
    * in DTL, the type of variable is determined at run time, it's quicker to get up and running fast but we can get **runtime errors**, which might caught at **compile time** in STL

1. **Numbers**
    * double precision 6-bit IEEE 754 format
    * There is no concept of integers except **BigInt** 
    * Everything is implicitly **float** so following things can happen: 0.1 + 0.2 = 0.300000000000000000004
    * Simple + Adv maths arithmetic operations are supported.
    * **parseInt** ot convert str to int
    * **parseFloat** to convert to float; Both method will continue  to do conversion until they reach a character. 
    * **NaN** is returned if the string is not a number. Can be testing using **isNaN** function
    * **Special Values**: NaN, Infinity, -Infinity 
3. **String**
    * Sequenc ef unicode charecters. By default supports **internationalization** 
    * it has **length** property
    * Built In functions like charAT(), replace, toUpperCase
    **Template Literal Tag**: 
        * Used in React Styled Component and i18n tagged package 
        * These are just functions, which add features to template string
        ```
        function h1(strings, ...values){
            var body = "";
            for(var i = 0; i < strings.length; i++){
                body += strings[i] + (values[i] || "");
            }
            return `<h1>${body}</h1>`;
        }
        var place = 'Delhi';
        var name = "Abhishek"
        console.log(h1`hello ${place} my name is ${name}`) // genrate h1 of passed string
        ```

3. **Boolean** 
    * False, 0, Empty string, NaN, null and undefined all become false. 
    * All others become true
4. **Symbol**(ES2015)
5. **Object**
    * Function, Array, Date, RegExp 
6. **null**
    * it represents not defined values and undefined represents not initialized values
6. **undefined** 
    * Undefined is actually a constant value , a variable which is declared but not initialized belongs tot the undefined type.

