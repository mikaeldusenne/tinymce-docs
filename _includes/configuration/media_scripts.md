### `media_scripts`

{% include DEPRECATED/generic-5_10.md %}

This option allows you to embed videos using script elements.

**Type:** `Array`

#### Example: Using `media_scripts`

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'media',
  menubar: 'insert',
  toolbar: 'media',
  media_scripts: [
   {filter: 'http://media1.example.com'},
   {filter: 'http://media2.example.com', width: 100, height: 200}
 ]
});
```
