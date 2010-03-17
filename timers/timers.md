!SLIDE

# long-running operations

## sometimes you can't avoid it

!SLIDE

# problem script
---
	@@@ javascript
	var i;
	for (i = 0; i < 10000; i += 1) {
		oneMillisecondOperation(i);
	}
---
## browser locks for 10s!

!SLIDE

# solution: timers
---
	@@@ javascript
	var i = 0;
	setTimeout(function iterate() {
		var stop = i + 500;
		for (; i < stop; i += 1) {
			oneMillisecondOperation(i);
		}
		setTimeout(iterate, 20);
	}, 0);
---
## split into half-second chunks, with 20ms in between

!SLIDE bullets
# minimum intervals
---
	@@@ javascript
	setTimeout(function () {
		alert("foo");
	}, 0);
	// how long until "foo"?
---
## no browser really does 0ms
## Chrome is ~5ms, but IE is ~18ms
## others are ~10-12ms

