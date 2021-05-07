---
layout: default
title: tabfocus
---

This plugin adds the possibility to tab in/out of TinyMCE.

## Initialization Example

```js
tinyMCE.init({
  theme : "advanced",
  mode : "textareas",
  plugins : "tabfocus"
});
```

## tabfocus_elements

(Requires: 3.2.2+)

This option enables you to specify an element ID to focus, when the user pressed the tab key inside the editor. You can also use the special `":prev"` and `":next"` values. It will then places the focus on either the previous or next input element placed before/after the TinyMCE instance in the DOM.

Example of usage of the `tab_focus` option

```js
// Move focus to specific element
tinyMCE.init({
  theme : "advanced",
  tabfocus_elements : "somebutton"
});

// Move focus to next element in DOM
tinyMCE.init({
  theme : "advanced",
  tabfocus_elements : ":prev,:next"
});
```