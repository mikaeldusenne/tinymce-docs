---
layout: default
title: valid_children
---

**(Requires: 3.4)**

The valid_children enables you to control what child elements can exists within what parent elements. TinyMCE will remove/split any non HTML transitional contents by default. So for example a P can't be a child of another P element.

The syntax for this option is a comma separated list of parents with elements that should be added/removed as valid children for that element. So for example "+body[style]" would add style as a valid child of body.

## Control characters:

| Name | Summary |
| --- | --- |
| + | Adds children to the list of valid elements for the specified parent. |
| - | Removes children from the list of valid children for the specified parent. |

This example shows you how to add style as a valid child of body and remove div as a valid child. It also forces only strong and a and text contents to be valid children of P.

```js
tinyMCE.init({
  ...
  valid_children : "+body[style],-body[div],p[strong|a|#text]"
});
```