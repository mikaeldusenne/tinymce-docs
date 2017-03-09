---
layout: default
title: execcommand_callback
---

This option allows you to add a custom callback function for execCommand handling. This enables you to override internal command functions in TinyMCE. The example below shows how the mceLink and mceImage are overridden.

Use the [addCommand](https://www.tinymce.com/docs-3x/api/class_tinymce.Editor.html/#addcommand/) method instead.

## Example of usage of the execcommand_callback option:

```js
function myCustomExecCommandHandler(editor_id, elm, command, user_interface, value) {
	var linkElm, imageElm, inst;

	switch (command) {
		case "mceLink":
			inst = tinyMCE.getInstanceById(editor_id);
			linkElm = tinyMCE.getParentElement(inst.selection.getFocusElement(), "a");

			if (linkElm)
				alert("Link dialog has been overriden. Found link href: " + tinyMCE.getAttrib(linkElm, "href"));
			else
				alert("Link dialog has been overriden.");

			return true;

		case "mceImage":
			inst = tinyMCE.getInstanceById(editor_id);
			imageElm = tinyMCE.getParentElement(inst.selection.getFocusElement(), "img");

			if (imageElm)
				alert("Image dialog has been overriden. Found image src: " + tinyMCE.getAttrib(imageElm, "src"));
			else
				alert("Image dialog has been overriden.");

			return true;
	}

	return false; // Pass to next handler in chain
}

tinyMCE.init({
  execcommand_callback : "myCustomExecCommandHandler"
});
```

An additional note: if you have URL processing rules, you may wish to apply these to the HREF of the attribute you're using, as follows (getFocusElement should be replaced by getNode in 3.xx):

```js
  var linkRef = (linkElm) ? tinyMCE.getAttrib(linkElm, "href") : '';
  if (linkRef != '')
  linkRef = tinyMCE.convertURL(linkRef, inst.selection.getFocusElement(), false);
```