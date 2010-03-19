!SLIDE

# Performance Tools

!SLIDE

# my JavaScript profiler
---
	@@@ javascript
	var profiler = performance.newProfiler();
	function foo() {
		profiler.begin("body");
		// ... some operations ...
		profiler.end("body");
	}
	// ... repeated calls to foo() ...
	profiler.report(); // alerts time spent in "body"
---
## source at <http://gist.github.com/322060>

!SLIDE biblioteca

# other tools

* JSLint (JavaScript syntax checker) <http://jslint.com/>
* YSlow (Firebug extension) <http://developer.yahoo.com/yslow/>
* Page Speed (Firebug extension) <http://code.google.com/speed/page-speed/>
* Speed Tracer (Chrome extension) <http://code.google.com/webtoolkit/speedtracer/>
* dynaTrace AJAX (Windows program/IE plugin) <http://ajax.dynatrace.com/pages/>