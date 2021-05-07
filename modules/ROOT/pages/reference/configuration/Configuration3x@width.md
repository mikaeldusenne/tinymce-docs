---
layout: default
title: width
---

This option gives you the ability to specify the width of the editor in pixels or percent. This width can be very useful to specify if the editor is used in hidden tabs or if the editor area should be bigger than the replaced element. The default value of this option is set to the width of the HTML element TinyMCE replaces. For example, the pixel width of a textarea.

## Example of usage of the width option:

```js
tinyMCE.init({
  ...
  width : "640"
});
```