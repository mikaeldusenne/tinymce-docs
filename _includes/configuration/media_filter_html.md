### `media_filter_html`

This option allows you disable the XSS sanitation filter for video/object elements. Scripts, conditional comments, etc, can't be used within these elements by default for security reasons. If you want to include that and have server side sanitizers or if you trust your users, then you can disable this feature.

**Type:** `Boolean`

**Default Value:** `true`

**Possible Values:** `true`, `false`

#### Example: Using `media_filter_html`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'media',
  menubar: 'insert',
  toolbar: 'media',
  media_filter_html: false
});
```

