# compilation vs Polyfilling
* JS is 100% backward compatible 
* As a developer we should be using new features without worry but by this we will be limiting browser and node versions.
* But we use compilers which allows us to write latest feature. Compiler compiles the code to older version of JS
* **Babel** – Allows to write in one version of JS and compile to another version. Eg Let is new feature babel convert it to var. https://babeljs.io   
> **NOTE**: We can't add feature by compiling, but if new feature can be achieved using some old feature then it will work. **For brand new feature it will not work.  For this we will use Polyfill e.g., Promise Polyfill – if we include them then those features will also run, with same Syntax as new version **