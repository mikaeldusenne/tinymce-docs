---
layout: default
title: theme_advanced_path
---

This option gives you the ability to enable/disable the element path. This option is only useful if the [theme_advanced_statusbar_location](https://www.tinymce.com/docs-3x/reference/configuration/Configuration3x@theme_advanced_statusbar_location/) option is set to "top" or "bottom". This option is set to "true" by default. Setting this option to "false" will effectively hide the path tool, though it still takes up room in the Status Bar.

## Example of usage of the theme_advanced_path option:

```js
tinyMCE.init({
	...
	theme_advanced_path : true
});
```