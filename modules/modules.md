!SLIDE

# modules

## how to make `SP.util`?

### _not_ the same as inheritance

!SLIDE

	@@@ javascript
	SP.util = (function (SP) {
		var util = {},
			foo; // private variable
		
		// public
		util.someFunction = function () {};
		
		// private
		function someOther() {}
		
		return util;
	}(SP));
---
## this a fast, reusable pattern