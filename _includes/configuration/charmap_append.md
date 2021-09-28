### `charmap_append`

This option provides a way to append some additional characters to the default character map. This can be array or a function that returns an array in the above mentioned format.

**Type:** `Array`, `Function`

#### Example: Using `charmap_append`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'charmap',
  toolbar: 'charmap',
  menubar: 'insert',
  charmap_append: [
    [0x2600, 'sun'],
    [0x2601, 'cloud']
  ]
});
```