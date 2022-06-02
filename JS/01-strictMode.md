# Strict Mode
* It put program in **strict mode executing context**. It makes debugging easier, it will alert to problem sooner
* pUT **use strict** at top of your JS files. This is a string because when ti was proposed older browser didnt supported it so it would break in them so it is made string
## Why
* Using a variable before declared gives an error. Otherwise without it would create a global variable. 
* Stops from using words reserved from future version of JS. Eg var let = 1 will throw error in strict mode
* You cannot delete function variable in strict mode. 
* It doesn’t let you delete arguments to functions. 
* Eval keyword becomes safer. Variable can’t leak eval block eval (“var a = 1”) a is not accessible from outside in strict mode. 
