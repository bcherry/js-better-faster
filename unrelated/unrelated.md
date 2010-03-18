!SLIDE

# random extras

## somewhat important

!SLIDE

# `parseInt` needs radix!
---
	@@@ javascript
	parseInt("123"); // 123
	parseInt("10"); // 10
	parseInt("010"); // 8 -> WTF?
	
	// with a radix
	parseInt("010", 10); // 10 -> crisis averted!
---
## never forget your radix

!SLIDE

# `sort` has issues
---
	@@@ javascript
	var a = [3,1,2];
	a.sort(); // [1,2,3]
	a = [10,1,2];
	
	a.sort(); // [1,10,2] - f**ing javascript!
	
	a.sort(betterComparison); // [1,2,10]
---
## `.sort()` sorts alphabetically
## write your own comparison function

!SLIDE

# CSS expressions are evaluated _right-to-left_!
---
	@@@ css
	#foo div a {/* ... */}
---
## this starts by looking at every `<a>`
## then it looks for those whose parent is `<div>`
## then it checks to see if its parent is `#foo`

!SLIDE biblioteca

# browser share on FB SPP

* 54% Internet Explorer
	* 31.8% IE8
	* 19.7% IE7
	* 2.6% IE6
	* 68 visits from IE 999.1 (it probably has HTML5 support)
* 31% Firefox/Win
* 10% Google Chrome
* 2% Firefox/Mac
* 1.5% Safari/Mac
* 1.5% other
