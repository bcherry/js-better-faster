!SLIDE

# The JavaScript Language #

### just what you need to know to understand this talk ###

!SLIDE

# variables and functions #
---
	@@@ javascript
	var foo = 1; // variable statement
	
	function bar() {} // function statement
	
	(function baz() {}); // function expression
	
	(function (spam) {}(1)); // function parameter
---
## those are the _only ways_ you should declare things

!SLIDE

# scope #
---
	@@@ javascript
	var foo = 1;
	(function () {
		var baz = 2;
		foo = 3;
	}());
	alert(foo); // 3
	alert(baz); // ReferenceError
---
## JavaScript has _function-level scope_

!SLIDE

# hoisting #
---
	@@@ javascript
	var foo = 1;
	(function () {
		alert(foo); // undefined
		var foo = 2;
	}());
	alert(foo); // 1
---
## names are always _hoisted_ to the top of their scope
## and always initialized to `undefined`
!SLIDE

# closure #
---
	@@@ javascript
	var foo = (function () {
		var bar = 5;
		
		return function () {
			alert(bar);
		};
	}());
	foo(); // 5
	setTimeout(foo, 10000); // 5, 10s later
---
## functions have access to their original _scope chain_