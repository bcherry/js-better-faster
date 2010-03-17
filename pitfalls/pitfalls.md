!SLIDE

# Run-Time Performance #
## common pitfalls ##

!SLIDE subsection

# "namespaces" #

!SLIDE

## Python ##

	@@@ python
	import apps.pet.util
	apps.pet.util.some_function()

	# this is quite fast
---
## JavaScript ##

	@@@ javascript
	SP.util.someFunction();
	
	// but this is very slow
	
!SLIDE process

# here's what happens #
---
	@@@ javascript
	SP.util.someFunction();

1. lookup `SP`
2. resolve property `util`
3. resolve property `someFunction`
4. execute function

---
## imagine that in a loop! ##

!SLIDE

# store that reference #
---
	@@@ javascript
	var some_function = SP.util.some_function,
		i;
	
	for (i = 0; i < 1000000; i += 1) {
		some_function();
	}
---
## this is much faster ##

!SLIDE subsection

# scope chains #

!SLIDE

# the slow way
---
	@@@ javascript
	var foo = 1;
	function bar() {
		var i;
		for (i = 0; i < 10000; i += 1) {
			alert(foo);
		}
	}
	bar();
---
## `foo` is one step down the chain
	
!SLIDE

# faster
---
	@@@ javascript
	var foo = 1;
	function bar() {
		var myFoo = foo, i;
		for (i = 0; i < 10000; i += 1) {
			alert(myFoo);
		}
	}
	bar();
---
## now `myFoo` is on the end of the chain

!SLIDE subsection

# arrays

!SLIDE

# arrays are objects, not arrays
---
	@@@ javascript
	var a = [];
	typeof a; // "object"
	a.length; // 0
	
	a[10] = 1;
	a.length; // 11
	
	a["something_else"] = 1;
	a.something_else; // 1
	a.length; // 11

!SLIDE
# this means arrays are slower than you expect

## but some browsers do optimize them

!SLIDE subsection

# loops

!SLIDE

# for loops
---
	@@@ javascript
	// slow method
	var i;
	for (i = 0; i < someArray.length; i += 1) {
		// ...
	}
---
	@@@ javascript
	// faster
	var i, l;
	for (i = 0, l = someArray.length; i < l; i += 1) {
		// ...
	}
	
!SLIDE

# for-in loops
---
	@@@ javascript
	var key;
	for (key in someObject) {
		// ...
	}
---
## these are slow, avoid them

!SLIDE

# for-in alternative
---
	@@@ javascript
	var keys = ["foo", "bar", "baz"], i, l, key;
	for (i = 0, l = keys.length; i < l; i += 1) {
		key = keys[key];
		// ... someObject[key] ...
	}
---
## this is much faster, and is preferred

!SLIDE subsection

# arguments

!SLIDE

	@@@ javascript
	function foo() {
		return arguments[0];
	}
	foo(1); // 1
---
## much slower (up to 100x) than using parameters
## `arguments` should be avoided if possible

