---
layout: default
title: merge_styles_invalid_parents
---

**Removed in 3.4**

This option enables you to specify a regular expression with elements you want to exclude from parent merging. By default, style information is attached to the parent element of a selection if all children (the entire element contents) are selected. For example, if you select a whole strong element then select a font size, the font-size style will be applied to the strong element instead of adding a wrapping style element. But sometimes you want to force a span element and this is where this option comes into place. This option is set to nothing by default and applies to the font size, face, and color and to the class drop drown lists.

The value may be a RegExp object or a string. If it's a string, then it is internally converted to a RegExp with ignore-case flag set.

## Example of usage of the merge_styles_invalid_parents option:

```js
tinyMCE.init({
  ...
  // Excludes table cells and strong elements from any parent merge operation
  merge_styles_invalid_parents : "^(TD|STRONG)$"
});
```