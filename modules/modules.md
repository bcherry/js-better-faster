!SLIDE

# modules

## how to make `BC.util`?

### _not_ the same as inheritance

!SLIDE

	@@@ javascript
	BC.util = (function (BC) {
		var util = {},
			foo; // private variable
		
		// public
		util.someFunction = function () {};
		
		// private
		function someOther() {}
		
		return util;
	}(BC));
---
## this a fast, reusable pattern