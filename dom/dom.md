!SLIDE

# The DOM

## it's absolutely terrible

### but I have a series of simple rules to make it better

!SLIDE subsection

# rule 1

## never edit the live tree

!SLIDE

# you can detach sub-trees
---
	@@@ javascript
	var elem = $("#myelem"),
		parent = elem.parent();
	
	elem.detach();
	// ... muck with elem and sub-elements ...
	parent.append(elem);

!SLIDE

# or you can clone and replace
---
	@@@ javascript
	var old = $("#myelem"),
		clone = old.clone();
	
	// ... muck with the clone ...
	old.replaceWith(clone);
---

## but be careful about event handlers
## use `.clone(true)` to preserve them

!SLIDE subsection

# rule 2

## build bottom-up

!SLIDE

# bottom-up construction
---
	@@@ javascript
	var child = document.createElement("div"),
		parent = document.createElement("div"),
		grand = document.createElement("div");
	
	parent.appendChild(child);
	grand.appendChild(parent);

!SLIDE subsection

# rule 3

## minimize event handlers

!SLIDE
# memory leaks in IE
	@@@ javascript
	$(".myelems").bind("click", function () {/* ... */});
	
	// ...
	
	$(".myelems").remove();
	
	// shit, memory leak!
---
## was that really that surprising?

!SLIDE
# unbind before removal
---
	@@@ javascript
	$(".myelems").unbind("click").remove();
	// phew!
---
## but that kind of sucks too

!SLIDE
# use event delegation
---
	@@@ javascript
	$(".myelems").live("click", function () {/* ... */});
	
	$(".myelems").remove();
	
	$("<div/>").addClass("myelems").appendTo($("body"));
---
## the new `<div>` gets the handler for free

!SLIDE
# avoid handlers in loops
---
	@@@ javascript
	function makeElem(id) {
		return $("<div/>").attr("id", id).click(function () {
			alert($(this).attr("id"));
		});
	}
	
	var i;
	for (i = 0; i < 1000; i += 1) {
		someParent.append(makeElem(i));
	}
---
## this is slow!

!SLIDE
# faster
---
	@@@ javascript
	function handler() {
		alert(this.attr("id"));
	}
	
	function makeElem(id) {
		return $("<div/>").attr("id", i).click(handler);
	}
	
	var i;
	for (i = 0; i < 1000; i += 1) {
		someParent.append(makeElem(i));
	}