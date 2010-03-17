!SLIDE

# page-load performance

## getting your script running quickly

!SLIDE
	@@@ html
	<html>
	<head></head>
	<body>
		<!-- all scripts at the bottom of <body>-->
		<script></script>
	</body>
	</html>
---
## always at the bottom, so the page is not blocked
# no exceptions!

!SLIDE
# avoid inline scripts
	@@@ html
	<script>
		function foo() {
			// ...
		}
	</script>
---
## these cannot be cached or minified
## only put dynamic values here

!SLIDE
# minification
---
	@@@ javascript
	function foo() {
		var bar = 1;
		return bar + 5;
	}
---
	@@@ javascript
	function foo(){var a=1;return a+5}
---
## our build process does this for you
## make sure you're using it!