### `a11ychecker_level`

This configuration option sets the [WCAG level](https://www.w3.org/TR/WCAG20/#conformance) to use when checking issues.

For example, the "Text must have a contrast ratio of at least ..." rule:

* When using **AA**, Accessibility Checker will check that the contrast ratio is not less than 4.5:1.
* When using **AAA**, Accessibility Checker will check that the contrast ratio is not less than 7.0:1.

**Type:** `String`

**Default value:** `aa`

**Possible Values:** `a`, `aa`, `aaa`

#### Example: Using `a11ychecker_level`

```js
tinymce.init({
  selector: 'textarea',
  plugins: 'a11ychecker',
  toolbar: 'a11ycheck',
  a11ychecker_level: 'aaa'
});
```

