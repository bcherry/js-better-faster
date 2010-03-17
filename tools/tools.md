!SLIDE

# Performance Tools

!SLIDE

# SP.Performance.profiler
---
	@@@ javascript
	var profiler = SP.Performance.profiler();
	function foo() {
		profiler.begin("body");
		// ... some operations ...
		profiler.end("body");
	}
	// ... repeated calls to foo() ...
	profiler.report(); // alerts time spent in "body"
---
## allows complex instrumentation

!SLIDE 
# apps.pet.dependencies
---
	@@@ python
	B('fb_lib.js',
		I('js/fb_superpet.js'),
		# ...
	)
---
	@@@ python
	$apps.pet.dependencies.include('fb_lib.js')
---
## handles minification on live, raw scripts on dev

!SLIDE biblioteca

# other tools

* JSLint (JavaScript syntax checker) <http://jslint.com/>
* YSlow (Firebug extension) <http://developer.yahoo.com/yslow/>
* Page Speed (Firebug extension) <http://code.google.com/speed/page-speed/>
* Speed Tracer (Chrome extension) <http://code.google.com/webtoolkit/speedtracer/>
* dynaTrace AJAX (Windows program/IE plugin) <http://ajax.dynatrace.com/pages/>