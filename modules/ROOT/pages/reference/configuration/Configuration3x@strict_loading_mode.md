---
layout: default
title: strict_loading_mode
---

**Removed in 3.4**

This option will force TinyMCE to load scripts using a DOM insert method instead of document.write on Gecko browsers. Since this results in asynchronous script loading, a built-in synchronizer will ensure that theme, plugin, and language pack files are loaded in the correct order. This will, on the other hand, make the initialization procedure of TinyMCE a bit slower, and that's why this isn't the default behavior. This option is set to true by default if the document content type is application/xhtml+xml.

## Example of usage of the strict_loading_mode option:

```js
tinyMCE.init({
  ...
  strict_loading_mode : true
});
```