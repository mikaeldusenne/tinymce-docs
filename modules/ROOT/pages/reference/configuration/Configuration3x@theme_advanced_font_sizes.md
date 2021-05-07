---
layout: default
title: theme_advanced_font_sizes
---

This option should contain a comma separated list of font sizes to include. Each item in the list should be a valid value for the font-style CSS property (10px, 12pt, 1em, etc.). A more powerful version of this option was introduced in the 3.2 release of TinyMCE. Check the second example below.

## Example of usage of the theme_advanced_font_sizes option:

```js
tinyMCE.init({
  ...
  theme_advanced_font_sizes : "10px,12px,14px,16px,24px"
});
```

## Advanced example of usage of the theme_advanced_font_sizes option:

```js
tinyMCE.init({
  ...
  theme_advanced_font_sizes : "Big text=30px,Small text=small,My Text Size=.mytextsize"
});
```