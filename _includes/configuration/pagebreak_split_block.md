### `pagebreak_split_block`

When enabled this option makes it easier to split block elements with a page break.

**Type:** `Boolean`

**Default Value:** `false`

**Possible Values:** `true`, `false`

#### Example: Using `pagebreak_split_block`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'pagebreak',
  menubar: 'insert',
  toolbar: 'pagebreak',
  pagebreak_split_block: true
});
```

